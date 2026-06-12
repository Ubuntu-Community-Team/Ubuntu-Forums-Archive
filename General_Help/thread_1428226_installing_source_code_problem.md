---
title: "installing source code problem"
date: 2010-03-12
forum: General Help
---

### Post by locost08 on 2010-03-12
In Ubuntu 9.10 I am trying to install brl-cad source code.  The extraction seems to go OK, but I can't configure.  I have loaded the build-essentials.  It appears that I need to run "sh autogen.sh"  I have attempted every method that I can think of to no avail.  I went to the directory where I extracted to and typed "find . autogen.sh" and it comes up with nothing.  What am I doing wrong?

---

### Post by flippo on 2010-03-12
I just looked at brlcad and downloaded the linux install, and it is not a source archive.  Did you download the linux install, or the source archive.  

If you downloaded the linux version it should have extracted to a directory named "usr".  if you move all the contents of that directory to your /usr directory that should do it (I think). 

If your actually working with the source code (also comes in a .tar.gz) then let me know, I'll take a look at that too.

---

### Post by locost08 on 2010-03-12
I downloaded the linux install not the source code.  You are correct, it does extract to a usr folder.  So I should move the entire contents of this usr folder to the main usr folder?  Looking at the contents of the extracted usr folder there is what looks like a lot of extras.  Think I should move all of it?

---

### Post by flippo on 2010-03-12
I don't know anything about it, to be honest.  They intend for the code to go into the /usr/ directory, its obvious by the tar.  I'm not sure if further steps need to be taken from there.  But the issue is not a ./configure or ./autogen.sh script, you don't have source code.

---

### Post by tom4everitt on 2010-03-12
> **locost08 said:**
> I downloaded the linux install not the source code.  You are correct, it does extract to a usr folder.  So I should move the entire contents of this usr folder to the main usr folder?  Looking at the contents of the extracted usr folder there is what looks like a lot of extras.  Think I should move all of it?

It definitely sounds like it, yes.

---

### Post by locost08 on 2010-03-12
OK, I moved the folder.  Now is says that I have to run the script "./configure --enable-optimized"  I know that to do that I have to be in that directory to do that.  How would I do that?  Sorry I am such a dweeb.

---

### Post by tom4everitt on 2010-03-13
Don't worry, we're all new once :)

In a terminal, you move between directories with the command 'cd'. So to move to the main usr folder (/usr) you type:

cd /usr

Then you can use the 'ls' command so to where you can proceed. Say that one of the outputs of ls is bin. Then you can type

cd bin

to move into that directory. Then type ls again etc. Don't forget its case sensitive! To see what directory you're in at the moment, type 'pwd'. To return to your home directory, type just 'cd' (without arguments).

And do get back for more info!

---

### Post by locost08 on 2010-03-17
Ok, I finally realized why I was having problems getting to the root directories.  Thanks for your help on that.

The installation instructions are as follows:
Generic Binary Distributions:

For the unspecialized binary distributions that are basically
compressed tarballs of the installation root, they should contain the
entire hierarchy of the distribution.  That is to say that they
contain /usr/brlcad in it's entirety so that if you decompress, you
will have a `usr' directory that contains a single `brlcad' directory:

gunzip brlcad-7.2.4_linux_ia64.tar.gz
tar -xvf brlcad-7.2.4_linux_ia64.tar
sudo mv usr/brlcad /usr/.

Of course, there are other compression options possible including zip
and bzip2.  By default, BRL-CAD expects to be installed into
/usr/brlcad and MGED is not relocateable by default.  It's recommended
that you start from a source distribution if you would like to install
into an alternate installation location.

However, if you do desire to install and run BRL-CAD from a different
location, give it a try.. ;) The only problems encountered should be
with running the MGED solid modeler where you will need to set the
BRLCAD_ROOT environment variable to your different install location
(e.g. /usr/local).  If this doesn't work (some platforms are more
problematic than others), you will need to compile and install from a
source distribution.

Nowhere do I see where it actually installs and identifies the other dependencies.  Down further in the instructions it says to test an installation to run "rt".  I found that and tried to run it.  It now says to try sudo apt-get install <name>

The results are shown below.

ron@ron-laptop:/usr/brlcad/rel-7.10.4/bin$ sudo apt-get install brlcad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package brlcad is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package brlcad has no installation candidate

Obviously, the dependencies and install is not completed.  Any ideas.  I have tried ./configure
make
(do I have to run the make command different than I have listed here?)  I am kind of lost.

---

### Post by tom4everitt on 2010-03-17
Do run this from the readme:
```

gunzip brlcad-7.2.4_linux_ia64.tar.gz
tar -xvf brlcad-7.2.4_linux_ia64.tar
sudo mv usr/brlcad /usr/.

```

Then post the output of 

```

ls -l /usr/brlcad

```

---

### Post by locost08 on 2010-03-17
I actually ran "tar xjvf /home/Downloads/brlcad_7.10.4_ia32.tar.bz2
Then I ran the sudo mv usr/brlcad /usr/.

ls -1 /usr/brlcad
bin
include
lib
man
rel-7.10.4
share
stable

I don't know if it makes any difference, but the rel-7.10.4 is a different color(blue) than the rest of the entries(green).

---

### Post by tom4everitt on 2010-03-17
Blue generally means that it is a folder, green that it is an executable. 

I would try to run the program by just running 

/usr/brlcad/bin

in a terminal. This should execute the file bin (bin is usually short for binary).

---

### Post by locost08 on 2010-03-17
Ok I must be slightly colorblind.  Apparently it is a light blue.  It is a directory.  Within that directory is a shell script called brlcad-config

This is what it says.
# BRL-CAD configuration script for determining compilation
# characteristics of a given install.
# 
# Author -
#   Christopher Sean Morrison
###

prefix=/usr/brlcad/rel-7.10.4
exec_prefix=${prefix}
includedir=${prefix}/include
libdir=${exec_prefix}/lib


usage ( ) {
    cat <<EOF
Usage: brlcad-config [OPTIONS] [LIBRARIES]

Options:
    [ --help ]
    [ --version ]
    [ --cflags ]
    [ --ldflags ]
    [ --libs ]
    [ --prefix[=DIR] ]
    [ --libdir[=DIR] ]
    [ --includedir[=DIR] ]

Libraries:
    bn
    brlcad (default)
    bu
    dm
    fb
    fft
    multispectral
    optical
    pkg
    rt
    wdb

There is more, but I think this may tell you what is needed?  I am not completely discouraged.  This is how I had to learn the PC way back in the DOS days.  We'll get it, then everyone will know.

---

### Post by tom4everitt on 2010-03-17
Okay, so to launch any (executable) file you just type its full path in the terminal. 

It sounds like you should launch the configure script, so run:
```

/usr/brlcad/bin/brlcad-config

```
and it will hopefully give you further instructions :)

You can also try finding other executables in the /usr/brlcad folder and its subfolders. Either list them with 
```

ls /usr/brlcad/subfolder

```
or find the diamonds in nautilus. 

Then just try to launch them with their full path in the terminal.

EDIT: you should probably launch them as sudo. So launch the config script with:
```

sudo /usr/brlcad/bin/brlcad-configure

```

---

