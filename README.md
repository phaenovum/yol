This readme will guide you to build your arm toolchain on Linux from the very
first step.


How to setup the build environment?
====================================

For a proper build environment, you need the following tools:

GCC/G++
-------
* Homepage:       http://gcc.gnu.org/
* Description:    The GNU Compiler Collection
* Ubuntu:         build-essential
* Gentoo:         sys-devel/gcc (installed by default)

GNU libc6
---------
* Homepage:       http://www.gnu.org/software/libc/libc.html
* Description:    GNU libc6 (also called glibc2) C library
* Ubuntu:         build-essential
* Gentoo:         sys-libs/glibc (installed by default)

GNU Make
--------
* Homepage:     http://www.gnu.org/software/make/make.html
* Description:  Standard tool to compile source trees
* Ubuntu:       build-essential
* Gentoo:       sys-devel/make (installed by default)

GMP
---
* Homepage:     http://gmplib.org/
* Description:  Library for arithmetic on arbitrary precision integers,
                rational numbers, and floating-point numbers
* Ubuntu:       libgmp3-dev
* Gentoo:       dev-libs/gmp (installed by default)

MPFR
----
* Homepage:     http://www.mpfr.org/
* Description:  library for multiple-precision floating-point computations with
                exact rounding
* Ubuntu:       libmpfr-dev
* Gentoo:       dev-libs/mpfr (installed by default)

zlib
----
* Homepage:     http://www.zlib.net/
* Description:  Standard (de)compression library
* Ubuntu:       zlib1g-dev
* Gentoo:       sys-libs/zlib (installed by default)

Ncurses
-------
* Homepage:     http://www.gnu.org/software/ncurses/
                http://dickey.his.com/ncurses/
* Description:  console display library
* Ubuntu:       libncurses5-dev
* Gentoo:       sys-libs/ncurses (installed by default)

GNU patch
---------
* Homepage:     http://www.gnu.org/software/patch/patch.html
* Description:  Utility to apply diffs to files
* Ubuntu:       patch
* Gentoo:       sys-devel/patch

Texinfo
-------
* Homepage:     http://www.gnu.org/software/texinfo/
* Description:  The GNU info program and utilities
* Ubuntu:       texinfo
* Gentoo:       sys-apps/texinfo (installed by default)

GNU Readline library
--------------------
* Homepage:     http://cnswww.cns.cwru.edu/php/chet/readline/rltop.html
* Description:  Another cute console display library
* Ubuntu:       libreadline5-dev
* Gentoo:       sys-libs/readline (installed by default)

Gawk
----
* Homepage:     http://www.gnu.org/software/gawk/gawk.html
* Description:  GNU awk pattern-matching language
* Ubuntu:       gawk
* Gentoo:       sys-apps/gawk

GNU Wget (optional)
-------------------
* Homepage:     http://www.gnu.org/software/wget/
* Description:  Network utility to retrieve files from the WWW
* Ubuntu:       wget
* Gentoo:       net-misc/wget


All these files should be available via your Linux Distributions package
management.

On Ubuntu this should do the trick:

    apt-get install libgmp3-dev libmpfr-dev build-essential zlib1g-dev libncurses5-dev patch texinfo libreadline5-dev gawk wget

On Gentoo most packages are already part of the system. Install the rest via:

    emerge -av sys-devel/patch sys-apps/gawk net-misc/wget

Congratulations, you have installed your build environment.

Inside your system's shell, type:

    gcc --version
    makeinfo --version

As result, the version info of gcc and makeinfo will be displayed.


Modified YAGARTO Build Scripts
------------------------------
The build scripts and patches are hosted in a git repository on github.com.

You can download them using git:

    git clone git@github.com:phaenovum/yol.git

The repository is downloaded to the directory "yol", change into it:

    cd yol

Or if you don't have git installed, open the download page in your web-browser:

https://github.com/phaenovum/yol/downloads

And click the button "Download as tar.gz" to download a Tarball of the current
git "master" branch. Back in the shell untar the Tarball and change into the
untared directory:

    tar -xvf phaenovum-yol-*.tar.gz
    cd phaenovum-yol-*

Now you will find this README.md and all the other scripts you need to build
the arm toolchain. An directory "download" is created too. This is the
directory, where you must download the arm-toolchain source.


How to build an arm-toolchain on Linux?
=======================================

For the arm-toolchain you need the following sources:

[expat-2.0.1](http://sourceforge.net/project/showfiles.php?group_id=10127&package_id=10780&release_id=513851)

[gmp-5.0.4](ftp://ftp.gnu.org/gnu/gmp/gmp-5.0.4.tar.bz2)

[mpfr-2.4.2](http://www.mpfr.org/mpfr-2.4.2/mpfr-2.4.2.tar.bz2)

[binutils 2.22](ftp://sources.redhat.com/pub/binutils/releases/binutils-2.22.tar.bz2)

[gcc-4.7.1](ftp://sources.redhat.com/pub/gcc/releases/gcc-4.7.1/gcc-4.7.1.tar.bz2)

[newlib 1.20.0](ftp://sources.redhat.com/pub/newlib/newlib-1.20.0.tar.gz)

[gdb 7.4.1](ftp://sources.redhat.com/pub/gdb/releases/gdb-7.4.1.tar.bz2)

[mpc 0.8.1](http://www.multiprecision.org/mpc/download/mpc-0.8.1.tar.gz)


You MUST download all these files into the download directory which was created
in the step before. To download these files from the yagarto website change
into the download directory and execute the download helper script to download
all at once, then change back to the project directory:

    cd download
    ./download-helper.sh
    cd ..

Here you will find some build scripts.

The first script, "00-set-env.sh" will expand the source and apply patches if
needed. After this you can start script 01 to 09 (in this order) with:

    ./<script-name.sh>

At the end, you will find the arm-toolchain inside the "install" directory.

You can copy this directory anywhere on your linux pc for example inside
"armdev", but you must expand the PATH by

    <armdev>/bin.

The toolchain here was build on a Gentoo Linux x86_64 machine with kernel
release 3.3.8-gentoo without any problems (now).



Credits
=======

- Thanks to Michael Fischer for providing [Yagarto] (http://yagarto.de).

- A lot of information I have found in the internet


(25.07.2012, Lars Moellendorf, https://github.com/phaenovum/yol)
