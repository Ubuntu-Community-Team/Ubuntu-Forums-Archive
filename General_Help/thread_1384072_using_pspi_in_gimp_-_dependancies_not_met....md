---
title: "using pspi in gimp - dependancies not met..."
date: 2010-01-18
forum: General Help
---

### Post by Megrimn on 2010-01-18
**The solution is in the second post.**

[original post]
Hey, just wondering... 

I'm trying to use that photoshop plug-in for gimp.  Since it hasn't been updated in ages, there is only an i386 version, but it ought to work under amd64 anyway if all the dependencies are met.  

If there is anyone with a clue how to fix this, I would happily appreciate it.  I have to restart my computer every time I want to use the PS plugins, and I couldn't get the plugin working under wine gimp either.

thanks

---

### Post by Vince1 on 2010-01-30
How to install PSPI to work under 64-bit Ubuntu.  I am writing these
instructions on my Jaunty installation, for Gimp 2.6.6.

Most of the basic instructions can be found here:
[http://www.instructables.com/id/Photoshop_Plugins_In_The_GIMP/](http://www.instructables.com/id/Photoshop_Plugins_In_The_GIMP/)
but there are a few special instructions for installing pspi on an Ubuntu
64-bit system.

There is quite a bit of overlap between the instructions found on the above
website and the steps outlined below.

1) Create a directory to save the pspi download, I'll call mine ~/pspi_download

   $ cd
   $ mkdir pspi_download
   $ cd ~/pspi_download

2) Download pspi (Use your web browser to go to
   [http://tml.pp.fi/gimp/pspi.html](http://tml.pp.fi/gimp/pspi.html), and click on the link for
   "Ubuntu 5.10 binary".)  Save file gimp-pspi-1.0.5.ubuntu.i386.tar.gz
   in the ~/pspi_download directory you created above.

3) Unzip it:

   $ gunzip gimp-pspi-1.0.5.ubuntu.i386.tar.gz 

4) Extract the files from the tar:

   $ tar -xfv gimp-pspi-1.0.5.ubuntu.i386.tar

5) Copy files pspi and pspi.exe.so to your personal Gimp plug-in folder.
   Mine is ~/.gimp-2.6/plug-ins

   $ cp pspi pspi.exe ~/.gimp-2.6/plug-ins

6) There are 32-bit Gimp files missing that must be installed in order
   for pspi to work.

   To see the files that are missing, use this command:
   $ cd ~/.gimp-2.6/plug-ins
   $ ldd pspi.exe.so | grep not

   You should see the following:

   libgimpui-2.0.so.0 => not found
   libgimpwidgets-2.0.so.0 => not found
   libgimp-2.0.so.0 => not found
   libgimpmath-2.0.so.0 => not found
   libgimpcolor-2.0.so.0 => not found
   libgimpbase-2.0.so.0 => not found

7) Using a web browser, download the 32-bit .deb package that contains
   these files.  You can find the package here:

   [http://packages.ubuntu.com/jaunty/i386/libgimp2.0/download](http://packages.ubuntu.com/jaunty/i386/libgimp2.0/download)

8.) Save (don't install) libgimp2.0_2.6.6-0ubuntu1.1_i386.deb to a new
   directory called ~/libgimp_32bit_download

9) Unpack the files from the .deb package like this:

   $ cd ~/libgimp_32bit_download
   $ mkdir unpack
   $ dpkg-deb -x libgimp2.0_2.6.6-0ubuntu1.1_i386.deb unpack

10) In the unpack directory, you will find some subdirectories.  Go to
    the usr/lib directory:

    $ cd unpack/usr/lib

11) Change the permissions of all the regular files (not the symbolic links) to 
    -rwxr-xr-x (755):

    $ sudo chmod 755 lib*.6

12) Copy all the files (including links) to /usr/lib32:

    $ sudo cp -d * /usr/lib32

    Note:  The -d option tells cp to also copy the symbolic links

13) Repeat step 6, except this time, you should see NO files listed:

    $ cd ~/.gimp-2.6/plug-ins
    $ ldd pspi.exe.so | grep not

    No files should be listed.  If there are any, you did something wrong
    above, so go back and double check.

14) Run gimp.  It should recognize the new pspi plugin.  Click on the Filters
    menu.  At the bottom, you should see a new menu option, "Photoshop
    Plug-in Settings..."

15) At this point, pspi is installed properly on your 64-bit Ubuntu machine.
    Follow the rest of the instructions found at
    [http://www.instructables.com/id/Photoshop_Plugins_In_The_GIMP/](http://www.instructables.com/id/Photoshop_Plugins_In_The_GIMP/)
    in order to configure and use it.  You can start at step 3.

I hope you find these instructions helpful.

---

### Post by JEdwardP on 2010-02-21
Vince1, please accept my most heartfelt thanks! I'd already installed PSPI, downloaded the 32-bit package, copied the few missing 32-bit files, verified their subsequent presence, and was feeling like the world's most glaring idiot.

When I saw no "Xtns" menu, I'd even looked in the "Filters" menu, but had missed the "Photoshop Plug-in Settings..." sub-menu, simply for lack of having scrolled down far enough.

I hate to even admit that in a public forum, but I do so in hope it'll help someone else, assuming I'm actually NOT the only user on the planet who made the same mistake.

Even some relatively recent instructional posts in other venues still refer to an "Xtns" menu not present in GIMP 2.6x, which I suppose I'd somehow expected PSPI to create :)

---

### Post by Megrimn on 2010-02-21
Thanks.  This totally helped!

---

### Post by enkumber on 2010-03-01
thanks, it worked.
tho, i cannot install a plugin I need, Portraiture.
The plugin appears and I can select it but nothing happens.
I need to install it but I don't know how. I will look into this more tho

---

### Post by riminicat on 2010-03-29
I love you! I changed a few steps in the process(I didn't use the terminal to copy/paste and unpack)  But it works! Thanks a lot, now I can take my photos to the next level.

---

### Post by sounddunk on 2010-05-04
Hi, i've followed the whole guide and have the FRACTALIUS photoshop plug-in installed correctly in GIMP. I can open my photo and the plug-in and preview all of the presets perfectly modified, but when I click on apply it closes the plug-in and all I can see is the original photo without the effect applied. What might have gone wrong? I am using ubuntu 10.04 amd 64 on a presario v5000, with GIMP 2.6.8

Thanks in advance for any advice,

Duncan

p.s. sometimes I get this error after a minute :

El complemento ha fallado: «pspi»              <-   plug-in has failed
(/home/duncan/.gimp-2.6/plug-ins/pspi)

---

### Post by Megrimn on 2010-06-01
> **sounddunk said:**
> Hi, i've followed the whole guide and have the FRACTALIUS photoshop plug-in installed correctly in GIMP. I can open my photo and the plug-in and preview all of the presets perfectly modified, but when I click on apply it closes the plug-in and all I can see is the original photo without the effect applied. What might have gone wrong? I am using ubuntu 10.04 amd 64 on a presario v5000, with GIMP 2.6.8

Thanks in advance for any advice,

Duncan

p.s. sometimes I get this error after a minute :

El complemento ha fallado: «pspi»              <-   plug-in has failed
(/home/duncan/.gimp-2.6/plug-ins/pspi)

Yes, I get this too, but there is a workaround.  

After hitting 'apply' in fractalius, go to the 'filters' menu and select 'Repeat "Fractalius"'.  The keyboard shortcut is ctrl+F. It will now do what you originally asked it to do.  This works for some other plugins that cause this problem as well.

---

### Post by sounddunk on 2010-06-11
thanks a lot! got it working and it looks great!
duncan

---

### Post by celiapgt on 2010-11-18
Thank you very much, Vince1. You're the man!

---

### Post by kcho on 2011-02-04
It works on my Ubuntu 10.10 x64! thank you very much!!!

:guitar:

---

### Post by butti on 2011-05-01
It works or works not. I have succesfuly installed pspi on my ubuntu 10.04 64bit and set it but i can't see any of my photoshop plugins in gimp...Absolutly anyone. Could anybody tell me which plugs work for you?

---

### Post by jfarenden on 2012-01-15
Hi all,

So, I'm trying to get this to work with Ubuntu 11.10 (64 bit) and GIMP 2.6.11

I've installed WINE; downloaded and unpacked pspi in to the correct location and have also unpacked and copied the 32 bit libraries in to /usr/lib32

I've updated the PATH variable in my terminal to include /usr/lib32 and checked that I can see the libraries:
for example

$ which libgimpcolor-2.0.so.0
/usr/lib32/libgimpcolor-2.0.so.0

This all seem correct, following the instructions above:

/usr/lib32$ ls -la libgimp*
lrwxrwxrwx 1 root root      23 2012-01-15 20:04 libgimp-2.0.so.0 -> libgimp-2.0.so.0.600.11
-rwxr-xr-x 1 root root  243816 2012-01-15 20:04 libgimp-2.0.so.0.600.11
lrwxrwxrwx 1 root root      27 2012-01-15 20:04 libgimpbase-2.0.so.0 -> libgimpbase-2.0.so.0.600.11
-rwxr-xr-x 1 root root   87912 2012-01-15 20:04 libgimpbase-2.0.so.0.600.11
lrwxrwxrwx 1 root root      28 2012-01-15 20:04 libgimpcolor-2.0.so.0 -> libgimpcolor-2.0.so.0.600.11
-rwxr-xr-x 1 root root   50692 2012-01-15 20:04 libgimpcolor-2.0.so.0.600.11
lrwxrwxrwx 1 root root      29 2012-01-15 20:04 libgimpconfig-2.0.so.0 -> libgimpconfig-2.0.so.0.600.11
-rwxr-xr-x 1 root root   59492 2012-01-15 20:04 libgimpconfig-2.0.so.0.600.11
lrwxrwxrwx 1 root root      27 2012-01-15 20:04 libgimpmath-2.0.so.0 -> libgimpmath-2.0.so.0.600.11
-rwxr-xr-x 1 root root   17844 2012-01-15 20:04 libgimpmath-2.0.so.0.600.11
lrwxrwxrwx 1 root root      29 2012-01-15 20:04 libgimpmodule-2.0.so.0 -> libgimpmodule-2.0.so.0.600.11
-rwxr-xr-x 1 root root   17944 2012-01-15 20:04 libgimpmodule-2.0.so.0.600.11
lrwxrwxrwx 1 root root      28 2012-01-15 20:04 libgimpthumb-2.0.so.0 -> libgimpthumb-2.0.so.0.600.11
-rwxr-xr-x 1 root root   34496 2012-01-15 20:04 libgimpthumb-2.0.so.0.600.11
lrwxrwxrwx 1 root root      25 2012-01-15 20:04 libgimpui-2.0.so.0 -> libgimpui-2.0.so.0.600.11
-rwxr-xr-x 1 root root  130284 2012-01-15 20:04 libgimpui-2.0.so.0.600.11
lrwxrwxrwx 1 root root      30 2012-01-15 20:04 libgimpwidgets-2.0.so.0 -> libgimpwidgets-2.0.so.0.600.11
-rwxr-xr-x 1 root root 1192964 2012-01-15 20:04 libgimpwidgets-2.0.so.0.600.11

However, I still get the 'not founds' when trying to ldd the module

$ ldd pspi.exe.so|grep not
    libgimpui-2.0.so.0 => not found
    libgimpwidgets-2.0.so.0 => not found
    libgimp-2.0.so.0 => not found
    libgimpmath-2.0.so.0 => not found
    libgimpcolor-2.0.so.0 => not found
    libgimpbase-2.0.so.0 => not found

Does anyone have any ideas about this??
Thanks
Jason

---

### Post by bogopants on 2012-02-17
i have the same issues, the gimp libraries appear to in the path but pspi cant find them for some reason

---

### Post by theirishkiwi on 2012-07-15
Hi,

I've been looking into getting pspi plugin working on Ubuntu 12.04 on a 64 bit system and came across a solution to the issue with the location of the 3 bit modules. I changed the location to below and this seemed to work. :) 

```
sudo cp -d * /usr/lib/i386-linux-gnu/
```

Unfortunately I still have a list of modules which are still missing before the pspi will work :(

```

 chris@chris-RC520 ~/.gimp-2.8/plug-ins $ ldd pspi.exe.so | grep not
	libgtk-x11-2.0.so.0 => not found
	libgdk-x11-2.0.so.0 => not found
	libatk-1.0.so.0 => not found
	libgdk_pixbuf-2.0.so.0 => not found
	libpangocairo-1.0.so.0 => not found
	libpango-1.0.so.0 => not found
	libgtk-x11-2.0.so.0 => not found
	libgdk-x11-2.0.so.0 => not found
	libgdk_pixbuf-2.0.so.0 => not found
	libgtk-x11-2.0.so.0 => not found
	libgdk-x11-2.0.so.0 => not found
	libgdk_pixbuf-2.0.so.0 => not found
	libpango-1.0.so.0 => not found

```

Any assistance with the required modules/ DEB's to be unpacked to satisfy this list would be much appreciated.  I will of course work on this myself and will provide any updated with any new discoveries!

Best 

Chris

---

### Post by Stef089 on 2012-07-24
Here's the link to the missing modules which are to copied to/user/lib/i386-linux-gnu/: [http://packages.ubuntu.com/precise/i386/libgimp2.0/download](http://packages.ubuntu.com/precise/i386/libgimp2.0/download).
The PSPI pluging appears now correctly in GIMP in the filter menu. Unfortunately it crashes if you try to use it because of Wine 1.4 which is installed on my system (Ubuntu 12.04 64bit). Perhaps with another Wine version it could work...
PS: The problem is probably that on Ubuntu 12.04 there is a 64bit Wine version installed by default. But you need to run pspi.exe.so with a 32bit Wine version. But I haven't managed to configure it correctly yet. Can anybody help?

---

### Post by Stef089 on 2012-07-25
I have just filed a bug report on Wine bugzilla (see [http://bugs.winehq.org/show_bug.cgi?id=31311](http://bugs.winehq.org/show_bug.cgi?id=31311)). Perhaps that helps.

---

