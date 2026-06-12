---
title: "Error: &quot;cannot execute binary file&quot;"
date: 2012-05-29
forum: General Help
---

### Post by ertansinansahin on 2012-05-29
I'm new at Ubuntu. I have installed a program for astrophysics.

When I try to use one of the commands of the program I'm getting the error like that;

arnavisca@arnavisca-System-Product-Name:~$ powspec
bash: /home/arnavisca/Desktop/heasoft-6.12/x86_64-unknown-linux-gnu-libc2.5/bin/powspec: cannot execute binary file

How can I solve that?

---

### Post by jonedney on 2012-05-29
Just taking a shot in the dark here, trying running the command with sudo.

```
sudo <command>
```

---

### Post by ertansinansahin on 2012-05-29
Cannot solve the problem with 
sudo <command>..
What's the problem here?

---

### Post by gnusci on 2012-05-29
Post the output of the following command:

$ uname -a

EDIT:

Also post for the following command

$ ldd /home/arnavisca/Desktop/heasoft-6.12/x86_64-unknown-linux-gnu-libc2.5/bin/powspec

---

### Post by ertansinansahin on 2012-05-29
1. Linux arnavisca-System-Product-Name 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 i686 i386 GNU/Linux

2. not a dynamic executable

---

### Post by gnusci on 2012-05-29
> **ertansinansahin said:**
> 1. Linux arnavisca-System-Product-Name 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 i686 i386 GNU/Linux

2. not a dynamic executable

You are trying to run a 64 bits binary on a 32 bit OS, you need to install Ubuntu x86_64, which is for 64 bits architecture.

EDIT:

You can download from here:

[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

---

### Post by Bachstelze on 2012-05-29
Well, the binary is 64-bit, and your system is 32-bit, so you can't run it. Install a 64-bit system.

---

### Post by ertansinansahin on 2012-05-29
I download the program in 32 bit. Can I solve the problem in this way.

Now I get a different error

arnavisca@arnavisca-System-Product-Name:~$ powspec
powspec: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory

I think I have to delete early installs. "shared libraries" makes me think like that.

---

### Post by gnusci on 2012-05-29
You need to install libgfortran

sudo apt-get install libgfortran3

---

### Post by ertansinansahin on 2012-05-29
It's already installed. The problem is due to conflict between same programs (32 and 64 bit that I installed) that uses the same library. (This is my thought, I'm not experienced on ubuntu by the way.)

---

### Post by gnusci on 2012-05-29
Maybe you need to add the libgfortran.so.1 symbolic link pointing to the right library.

EDIT:

Post the output of the following command:

$ locate libgfortran.so.1

---

### Post by ertansinansahin on 2012-05-29
> **gnusci said:**
> Maybe you need to add the libgfortran.so.1 symbolic link pointing to the right library.

EDIT:

Post the output of the following command:

$ locate libgfortran.so.1

There is no response for  "locate libgfortran.so.1 (and 2)" so I tried  "locate libgfortran.so.3"

/usr/lib/i386-linux-gnu/libgfortran.so.3
/usr/lib/i386-linux-gnu/libgfortran.so.3.0.0

---

### Post by gnusci on 2012-05-29
Create the symbolic link and try to run the program:

$ sudo ln -s /usr/lib/i386-linux-gnu/libgfortran.so.3 /usr/lib/i386-linux-gnu/libgfortran.so.1

---

### Post by ertansinansahin on 2012-05-29
Result is again the same. I think when I give the command for example "powspec", two program codes are confuses.

```
arnavisca@arnavisca-System-Product-Name:~$ sudo ln -s /usr/lib/i386-linux-gnu/libgfortran.so.1 /usr/lib/i386-linux-gnu/libgfortran.so.3
[sudo] password for arnavisca: 
ln: failed to create symbolic link `/usr/lib/i386-linux-gnu/libgfortran.so.3': File exists
arnavisca@arnavisca-System-Product-Name:~$ sudo ln -s /usr/lib/i386-linux-gnu/libgfortran.so.1 /usr/lib/i386-linux-gnu/libgfortran.so.4
arnavisca@arnavisca-System-Product-Name:~$ sudo ln -s /usr/lib/i386-linux-gnu/libgfortran.so.1 /usr/lib/i386-linux-gnu/libgfortran.so.4
ln: failed to create symbolic link `/usr/lib/i386-linux-gnu/libgfortran.so.4': File exists
arnavisca@arnavisca-System-Product-Name:~$ fdump
fdump: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory
arnavisca@arnavisca-System-Product-Name:~$ powspec
powspec: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory

```

---

### Post by gnusci on 2012-05-29
> **ertansinansahin said:**
> Result is again the same. I think when I give the command for example "powspec", two program codes are confuses.

```
arnavisca@arnavisca-System-Product-Name:~$ sudo ln -s /usr/lib/i386-linux-gnu/libgfortran.so.1 /usr/lib/i386-linux-gnu/libgfortran.so.3
[sudo] password for arnavisca: 
ln: failed to create symbolic link `/usr/lib/i386-linux-gnu/libgfortran.so.3': File exists
arnavisca@arnavisca-System-Product-Name:~$ sudo ln -s /usr/lib/i386-linux-gnu/libgfortran.so.1 /usr/lib/i386-linux-gnu/libgfortran.so.4
arnavisca@arnavisca-System-Product-Name:~$ sudo ln -s /usr/lib/i386-linux-gnu/libgfortran.so.1 /usr/lib/i386-linux-gnu/libgfortran.so.4
ln: failed to create symbolic link `/usr/lib/i386-linux-gnu/libgfortran.so.4': File exists
arnavisca@arnavisca-System-Product-Name:~$ fdump
fdump: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory
arnavisca@arnavisca-System-Product-Name:~$ powspec
powspec: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory

```

My mistake. The correct command is:

$ sudo ln -s /usr/lib/i386-linux-gnu/libgfortran.so.3 /usr/lib/i386-linux-gnu/libgfortran.so.1

---

### Post by ertansinansahin on 2012-05-29
Another error occured:

```
arnavisca@arnavisca-System-Product-Name:~$ powspec
powspec: symbol lookup error: /home/arnavisca/Desktop/heasoft/heasoft-6.12/i686-pc-linux-gnu-libc2.5/lib/libxanlib_6.12.so: undefined symbol: _gfortran_copy_string

```

How can I completely erase the effects of preceding installation? or how can  I solve the problem above?

---

### Post by gnusci on 2012-05-29
post the output of:

$ ls /home/arnavisca/Desktop/heasoft/heasoft-6.12/i686-pc-linux-gnu-libc2.5/lib/

EDIT;

post the output of:

$ ldd powspec

and

$ locate powspec

---

### Post by ertansinansahin on 2012-05-30
```
arnavisca@arnavisca-System-Product-Name:~$ ls /home/arnavisca/Desktop/heasoft/heasoft-6.12/i686-pc-linux-gnu-libc2.5/lib/
fgui                  libCOM.so             libreadline.so           libxpa.so.1.0
fv                    libcoordfits.so       libreadline.so.6         libxpi_wrappers_6.12.so
grfont.dat            libcoord.so           libreadline.so.6.2       libxron_6.12.so
itcl3.3               libcpgplot4perl.so    librew.so                libxronos.so
itk3.3                libcpgplot5.2.2.a     libros_6.12.so           libxrrt-dummy.so
iwidgets              libcpgplot5.2.2.so    libsexfits.a             libxrrt.so
iwidgets2.2.0         libephemeris.so       libsexwcs.a              libXS.a
iwidgets4.0.1         libEVS.so             libswuvot.so             libxself_6.12.so
libANL.so             libexo_6.12.so        libswxrt.so              libxselt_6.12.so
libape_2.8.so         libfimage_6.12.so     libtcl8.4.so             libXSFit.so
libasca_6.12.so       libfitstcl.so         libtclreadline-2.1.0.so  libXSFunctions.so
libast-5.1.0.so       libftools_6.12.so     libtclreadline.a         libXSMinuit.so
libastadd_6.12.so     libgro_6.12.so        libtclreadline.so        libxsmix.so
libaste_com.so        libhdinit_2.6.so      libtclstub8.4.a          libXSModel.so
libaste_hxd.so        libhdio_2.6.so        libtclxpa.so             libXSPlot.so
libastetool.so        libhdsp_2.6.so        libtclxpa.so.1           libxstar_6.12.so
libaste_xis.so        libhdutils_2.6.so     libtclxpa.so.1.0         libXSUser.so
libaste_xrs.so        libhistory.so         libtk8.4.so              libXSUtil.so
libaste_xrt.so        libhistory.so.6       libtkpgplot5.2.2.a       libxte_6.12.so
libatFunctions3.2.so  libhistory.so.6.2     libtkpgplot5.2.2.so      perl
libatFunctions.so     libIntegral.so        libtkstub8.4.a           pow
libbatfftsg.so        libmpfit.so           libuvotcal.so            rgb.txt
libbatimageutils.so   libparam_wrappers.so  libvela_6.12.so          tcl8.4
libbatmaskutils.so    libpgadd_6.12.so      libwcs-4.4.4.a           tclreadline
libbatutils.so        libpgplot4perl.so     libwcs-4.4.4.so          tclreadline2.1.0
libBNK.so             libpgplot5.2.2.a      libwcs_6.12.so           Tix8.4
libcaltools_6.12.so   libpgplot5.2.2.so     libxanlib_6.12.so        tk8.4
libCCfits_2.4.so      libplt.so             libxdf.so                txselect
libcernlib-dummy.so   libpowclient.so       libximage_6.12.so        xspackage.tmpl
libcfitsio_3.29.so    libpow.so             libxpa.a                 xsut
libcftools_6.12.so    librandom.so          libxpa.so                xtcl
libCLI.so             libreadline.6.2.so    libxpa.so.1
**arnavisca@arnavisca-System-Product-Name:~$ ldd powspec**
ldd: ./powspec: No such file or directory
**arnavisca@arnavisca-System-Product-Name:~$ locate powspec**
/home/arnavisca/Desktop/heasoft/heasoft-6.12/ftools/i686-pc-linux-gnu-libc2.5/bin/powspec
/home/arnavisca/Desktop/heasoft/heasoft-6.12/ftools/i686-pc-linux-gnu-libc2.5/help/powspec.hlp
/home/arnavisca/Desktop/heasoft/heasoft-6.12/ftools/i686-pc-linux-gnu-libc2.5/help/powspec.txt
/home/arnavisca/Desktop/heasoft/heasoft-6.12/ftools/i686-pc-linux-gnu-libc2.5/syspfiles/powspec.par
/home/arnavisca/Desktop/heasoft/heasoft-6.12/i686-pc-linux-gnu-libc2.5/bin/powspec
/home/arnavisca/Desktop/heasoft/heasoft-6.12/i686-pc-linux-gnu-libc2.5/fguipfiles/powspec.par2
/home/arnavisca/Desktop/heasoft/heasoft-6.12/i686-pc-linux-gnu-libc2.5/help/powspec.hlp
/home/arnavisca/Desktop/heasoft/heasoft-6.12/i686-pc-linux-gnu-libc2.5/help/powspec.txt
/home/arnavisca/Desktop/heasoft/heasoft-6.12/i686-pc-linux-gnu-libc2.5/syspfiles/powspec.par
/home/arnavisca/Desktop/heasoft-6.12-12/ftools/x86_64-unknown-linux-gnu-libc2.5/bin/powspec
/home/arnavisca/Desktop/heasoft-6.12-12/ftools/x86_64-unknown-linux-gnu-libc2.5/help/powspec.hlp
/home/arnavisca/Desktop/heasoft-6.12-12/ftools/x86_64-unknown-linux-gnu-libc2.5/help/powspec.txt
/home/arnavisca/Desktop/heasoft-6.12-12/ftools/x86_64-unknown-linux-gnu-libc2.5/syspfiles/powspec.par
/home/arnavisca/Desktop/heasoft-6.12-12/x86_64-unknown-linux-gnu-libc2.5/bin/powspec
/home/arnavisca/Desktop/heasoft-6.12-12/x86_64-unknown-linux-gnu-libc2.5/fguipfiles/powspec.par2
/home/arnavisca/Desktop/heasoft-6.12-12/x86_64-unknown-linux-gnu-libc2.5/help/powspec.hlp
/home/arnavisca/Desktop/heasoft-6.12-12/x86_64-unknown-linux-gnu-libc2.5/help/powspec.txt
/home/arnavisca/Desktop/heasoft-6.12-12/x86_64-unknown-linux-gnu-libc2.5/syspfiles/powspec.par
```

---

### Post by ertansinansahin on 2012-05-30
What should I do. I have to run this software for my courses.
Please help!

---

### Post by oldos2er on 2012-05-30
> **ertansinansahin said:**
> 
/home/arnavisca/Desktop/heasoft/heasoft-6.12/ftools/i686-pc-linux-gnu-libc2.5/bin/powspec

Isn't the above what you're trying to run?

---

### Post by ertansinansahin on 2012-05-30
Problem solved with the help of NASA. The link includes the solution of the problem. I think it's a common problem.

[http://heasarc.gsfc.nasa.gov/lheasoft/linux.html](http://heasarc.gsfc.nasa.gov/lheasoft/linux.html)

---

### Post by oldos2er on 2012-05-30
Would you please mark the thread as 'Solved' under Thread Tools? Thanks.

---

