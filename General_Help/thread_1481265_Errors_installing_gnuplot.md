---
title: "Errors installing gnuplot"
date: 2010-05-12
forum: General Help
---

### Post by littlebilly91 on 2010-05-12
I downloaded the tar for gnuplot-4.0.0. In command prompt I ran 

./configure --prefix=/sw --without-gd --mandir='${prefix}/share/man'  --with-readline=gnu --enable-mouse --enable-pm3d --with-png --with-pdf --enable-filledboxes  --enable-relative-boxwidth --enable-thin-splines 

it seemed to work fine. 

'make' also seemed to work.

'make install' gave me some permission errors so I tried 'sudo make install'.
I got the following error.

[FONT=Verdana]../mkinstalldirs /sw/info
mkdir -p -- /sw/info
/usr/bin/install -c -m 644 gnuplot.info /sw/info/gnuplot.info
/usr/bin/install: cannot stat `gnuplot.info': No such file or directory
make[1]: *** [install-info] Error 1
make[1]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/docs'
make: *** [install-recursive] Error 1


[/FONT]Any help is appreciated, i'm new to linux. Thanks!!
-Chet

---

### Post by gmargo on 2010-05-12
Is there a particular reason that you're compiling this old version?  Why not install the one from the repository?

---

### Post by littlebilly91 on 2010-05-12
I tried that earlier, it went over about the same... I figured another version was worth a try.

---

### Post by littlebilly91 on 2010-05-12
This is the entire message if it helps any...

Making install in config
make[1]: Entering directory `/home/chet/Desktop/gnuplot-4.0.0/config'
make[2]: Entering directory `/home/chet/Desktop/gnuplot-4.0.0/config'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/config'
make[1]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/config'
Making install in m4
make[1]: Entering directory `/home/chet/Desktop/gnuplot-4.0.0/m4'
make[2]: Entering directory `/home/chet/Desktop/gnuplot-4.0.0/m4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/m4'
make[1]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/m4'
Making install in term
make[1]: Entering directory `/home/chet/Desktop/gnuplot-4.0.0/term'
make[2]: Entering directory `/home/chet/Desktop/gnuplot-4.0.0/term'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/term'
make[1]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/term'
Making install in src
make[1]: Entering directory `/home/chet/Desktop/gnuplot-4.0.0/src'
make[2]: Entering directory `/home/chet/Desktop/gnuplot-4.0.0/src'
make[3]: Entering directory `/home/chet/Desktop/gnuplot-4.0.0/src'
/bin/bash ../mkinstalldirs /sw/bin
  /usr/bin/install -c gnuplot /sw/bin/gnuplot
/bin/bash ../mkinstalldirs /sw/libexec/gnuplot/4.0
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/src'
make[2]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/src'
make[1]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/src'
Making install in docs
make[1]: Entering directory `/home/chet/Desktop/gnuplot-4.0.0/docs'
../mkinstalldirs /sw/share/gnuplot/4.0
/usr/bin/install -c -m 644 gnuplot.gih /sw/share/gnuplot/4.0/gnuplot.gih
/bin/sh /home/chet/Desktop/gnuplot-4.0.0/missing --run makeinfo -I. ./gnuplot.texi --no-split --output=gnuplot.info
/home/chet/Desktop/gnuplot-4.0.0/missing: 63: makeinfo: not found
WARNING: `makeinfo' is missing on your system.  You should only need it if
         you modified a `.texi' or `.texinfo' file, or any other file
         indirectly affecting the aspect of the manual.  The spurious
         call might also be the consequence of using a buggy `make' (AIX,
         DU, IRIX).  You might want to install the `Texinfo' package or
         the `GNU make' package.  Grab either from any GNU archive site.
sed: unrecognized option `--output=gnuplot.info'
Usage: sed [OPTION]... {script-only-if-no-other-script} [input-file]...

  -n, --quiet, --silent
                 suppress automatic printing of pattern space
  -e script, --expression=script
                 add the script to the commands to be executed
  -f script-file, --file=script-file
                 add the contents of script-file to the commands to be executed
  -i[SUFFIX], --in-place[=SUFFIX]
                 edit files in place (makes backup if extension supplied)
  -l N, --line-length=N
                 specify the desired line-wrap length for the `l' command
  --posix
                 disable all GNU extensions.
  -r, --regexp-extended
                 use extended regular expressions in the script.
  -s, --separate
                 consider files as separate rather than as a single continuous
                 long stream.
  -u, --unbuffered
                 load minimal amounts of data from the input files and flush
                 the output buffers more often
      --help     display this help and exit
      --version  output version information and exit

If no -e, --expression, -f, or --file option is given, then the first
non-option argument is taken as the sed script to interpret.  All
remaining arguments are names of input files; if no input files are
specified, then the standard input is read.

E-mail bug reports to: [email]bonzini@gnu.org[/email] .
Be sure to include the word ``sed'' somewhere in the ``Subject:'' field.
touch: missing file operand
Try `touch --help' for more information.
../mkinstalldirs /sw/info
/usr/bin/install -c -m 644 gnuplot.info /sw/info/gnuplot.info
/usr/bin/install: cannot stat `gnuplot.info': No such file or directory
make[1]: *** [install-info] Error 1
make[1]: Leaving directory `/home/chet/Desktop/gnuplot-4.0.0/docs'
make: *** [install-recursive] Error 1

---

### Post by gmargo on 2010-05-12
> **littlebilly91 said:**
> I tried that earlier, it went over about the same... I figured another version was worth a try.

What?  That makes no sense.

Use the package manager to install gnuplot. Version 4.2.6 is in the Lucid repository.
[http://packages.ubuntu.com/lucid/gnuplot](http://packages.ubuntu.com/lucid/gnuplot)

Your version 4.0.0 is quite old (unless you _really_ mean 4.4.0).

But in any case, your compilation problem is obvious.  You don't have the proper packages installed to generate the gnuplot.info file.  Here's your clue:
> 
/bin/sh /home/chet/Desktop/gnuplot-4.0.0/missing --run makeinfo -I.  ./gnuplot.texi --no-split --output=**gnuplot.info**
/home/chet/Desktop/gnuplot-4.0.0/missing: 63: **makeinfo**: not found
WARNING: `makeinfo' is missing on your system.  You should only need it  if
At the very least, you need to install the **texinfo** package.

---

