---
title: "Can't open/install Ghemical (don't know programming or coding; translation please)"
date: 2012-05-07
forum: General Help
---

### Post by Ulysses1994XF04 on 2012-05-07
So I tried downloading Ghemical, a molecular/chemical modeling program, from Ubuntu Software Center. It says it's installed but when I type "Ghemical" into the Terminal, a white icon comes up that says Ghemical underneath it but nothing opens. 

I tried going directly to the website ([http://www.bioinformatics.org/ghemical/download/](http://www.bioinformatics.org/ghemical/download/)) and downloaded the 20111012 version. I downloaded ghemical-3.0.0.tar.gz and opened the "INSTALL" file. I thought it would automatically install like in Windows, but instead a text document appears that tells me to type all these commands I don't know where. A lot of them simply don't work in Terminal. Here's what it says.

>     REQUIREMENTS:
    -------------

The ghemical package is dependent on "libghemical" package, in addition
to the packages/files that are needed to compile and run programs at
the GTK2 platform. Also ghemical is optionally dependent on "OpenBabel"
packages (for file import/export features).

You can get "libghemical-2.95.tgz" or newer from

    [http://bioinformatics.org/ghemical/download.html](http://bioinformatics.org/ghemical/download.html)

You can get "openbabel-2.0.0.tar.gz" or newer from

    [http://openbabel.sourceforge.net/](http://openbabel.sourceforge.net/)

Other software/packages that are needed to compile and run this program
are:

    g++            gcc version 4.1.2 or later
    make            GNU Make version 3.76.1
    pkg-config        pkg-config-0.15
    
    glib            glib-2.0 version 2.6.0 or newer
    gtk+            gtk+-2.0 version 2.6.0 or newer
    gtkglext        gtkglext-1.0 version 1.0.5 or newer
    libglade        libglade-2.0 version 2.4.0 or newer
    gthread            gthread-2.0 version 2.6.0 or newer (optional)

In short, any up-to-date Linux installation like Redhat, Mandrake
or Debian should work, if the necessary development packages (that
contain the header files) are also present, in addition to the standard
packages (that contain the libraries).


    INSTALLATION:
    -------------

Simple set of commands

    ./autogen.sh
    ./configure
    make
    make install        [run as root user]

will produce an executable program in which all the optional dependencies
mentioned above are disabled. You can enable the options by adding the
following statements to the configuration script command line:

    ./configure --enable-openbabel

If you wish to disable multithreading you may use:

    ./configure --enable-threads=no

For more options and information you can try

    ./configure --help

If at configuration step you get stuck and see some error messages about
PKG_CONFIG, please try the following tricks (and re-try ./configure):

    export PKG_CONFIG=pkg-config
    export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

Also if problems appear you might want to try updating the configuration
files using commands at the top of the source tree (and re-try ./configure):

    aclocal
    autoconf
    autoheader

This is an example how to set different compiler versions in Makefiles:

    CC=gcc-3.4 CXX=g++-3.4 ./configure

The "make install"-command will copy the executable and some extra files to
their proper places so that the program can be run anywhere. After you have
installed the program you can click the item "Help/Help" from the main menu
to read the User's Manual (highly recommended).

In the "examples"-directory there are some useful example molecules, and
in the "small-utilities"-directory there are... well, some small utilities.

Enjoy!!!
Does anybody have any idea what to do?

---

### Post by searchfgold6789 on 2012-05-07
What you've done is downloaded the source code for your program, that is, the raw, non-computer-executable code that came straight from the developers. Usually this is only needed by people seeking to make software packages for their linux distribution.
What I recommend doing is to try to get Ghemical to work without compiling the source code. Try not using the terminal, but use the actual Unity icon (search it from the dash). If that doesn't work, can you tell us the output from the terminal?

---

### Post by Ulysses1994XF04 on 2012-05-07
Sorry, I meant to say the search bar, not the terminal. I type "Ghemical" into the search bar and a white icon appears but it doesn't open. I then go into the terminal and type the commands from the "INSTALL" text. Here's what I get.

> steven@steven-1001PXD:~$ ./autogen.sh
bash: ./autogen.sh: No such file or directory


> steven@steven-1001PXD:~$ ./configure
bash: ./configure: No such file or directory
steven@steven-1001PXD:~$ 


> steven@steven-1001PXD:~$ make
make: *** No targets specified and no makefile found.  Stop.


> steven@steven-1001PXD:~$ make install [run as root user]
make: *** No rule to make target `install'.  Stop.


> steven@steven-1001PXD:~$ ./configure --enable-openbabel
bash: ./configure: No such file or directory


:confused:

---

### Post by Ulysses1994XF04 on 2012-05-08
bump

---

### Post by codingman on 2012-05-08
Try this:

```

sudo apt-get install ghemical

```
in terminal.

---

### Post by Ulysses1994XF04 on 2012-05-08
Just tried that, but here's what I got in the Terminal.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
ghemical is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Ghemical still won't open up when I click on the icon after searching for it in the search bar.

---

### Post by codingman on 2012-05-08
have you typed ghemical in terminal?

---

### Post by Ulysses1994XF04 on 2012-05-08
> **codingman said:**
> have you typed ghemical in terminal?

I just tried that. Here's what I got.

> steven@steven-1001PXD:~$ ghemical

OpenGL extension version - 1.4
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/builder/amino.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/builder/nucleic.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/default/atomtypes.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/default/parameters1.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/default/parameters2.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/default/parameters3.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/default/parameters4.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/tripos52/atomtypes.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/tripos52/parameters1.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/tripos52/parameters2.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/tripos52/parameters3.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/tripos52/parameters4.txt
DEBUG ; preparing to open file /usr/share/libghemical/2.99.1/param_mm/tripos52/parameters5.txt
Added local light.

OpenGL visual configurations :

gdk_gl_config_is_rgba (glconfig) = TRUE
gdk_gl_config_is_double_buffered (glconfig) = TRUE
gdk_gl_config_is_stereo (glconfig) = FALSE
gdk_gl_config_has_alpha (glconfig) = FALSE
gdk_gl_config_has_depth_buffer (glconfig) = TRUE
gdk_gl_config_has_stencil_buffer (glconfig) = TRUE
gdk_gl_config_has_accum_buffer (glconfig) = FALSE


(ghemical:6550): GdkGLExt-WARNING **: cannot load PangoFont
*** ERROR : Can't load font 'courier 12'

---

### Post by Ulysses1994XF04 on 2012-05-08
Do you know if there's anything I should type BEFORE the " ./autogen.sh " or the " ./configure"?

---

### Post by scott-ian on 2012-05-08
You need to install all dependencies (including the -dev versions) and change to the directory.

---

### Post by Ulysses1994XF04 on 2012-05-09
> **scott-ian said:**
> You need to install all dependencies (including the -dev versions) and change to the directory.


What are the "dependencies" and "directory"? How do I install and change them?

---

### Post by scott-ian on 2012-05-09
To install the dependencies, enter this command:
```
sudo apt-get build-dep ghemical
```
And you need to be in the folder with the decompressed source:
```
cd /home/username/Downloads/ghemical_src
```
Changing that to represent wherever you decompressed the source.

---

### Post by searchfgold6789 on 2012-05-09
> (ghemical:6550): GdkGLExt-WARNING **: cannot load PangoFont
*** ERROR : Can't load font 'courier 12' 			 		
Courier 12 is a Microsoft font. Ghemical won't load because it cannot find the fonts, because they are not installed. The Microsoft fonts come from a third-party source.
So install the ubuntu-restricted-extras package, and try opening Ghemical again. You might have to reinstall Ghemical.[FONT=Verdana]

[/FONT]

---

### Post by Tony Flury on 2012-05-09
To tanslate what searchfgold6789 said : 

Open a terminal and type : 
```

sudo apt-get install ubuntu-restricted-extras

```
and once that has completed then try to execute ghemical

Make sure you reply with any errors from the commands

---

