---
title: "How to manually install a program?"
date: 2011-07-17
forum: General Help
---

### Post by zxMarce on 2011-07-17
Hello you all!

I have a binary program downloaded as .tar.gz. It's a ZX Spectrum emulator called [**Speccy** (version 1.7)]("http://fms.komkon.org/Speccy/"). It works flawlessly, but the program is sitting in a folder called **Speccy v1.7** in my desktop. The file listing is as follows:

```
~/Desktop/Speccy v1.7$ ls
DIDAKTIK.ROM  speccy-16bpp  TRDOS.ROM     ZXS48.ROM
PENTAGON.ROM  speccy-32bpp  ZXS128.ROM    ZXSPLUS2.ROM
SCORPION.ROM  Speccy.html   ZXS128TR.ROM  ZXSPLUS3.ROM
```There are two executables, **speccy-16bpp** and **speccy-32bpp**. The rest are emulated machines' ROMs and an HTML readme.

I would like the program to be *correctly installed*, with a Launcher in the Applications menu and all the bells and whistles. Problem is I come from a **C:\Program Files\** environment (sorry!) and don't have a clue of where to put the emulator files to begin with. My googling did not help either, maybe I'm using the wrong keywords.

I'd like help in at least having the emulator files where they're supposed to be -not my Desktop-, and I'd like it to have a launcher.

Can anybody help?

TIA,
Marcelo.

---

### Post by claracc on 2011-07-18
To install the program you have to have a .deb file (which I don't see in the Speccy v1.7 directory ( have you downloaded linux or windows files?, if they are windows ones you'll use Wine to install in ubuntu).

Once you have the .deb file in the Speccy v1.7 directory in your /home/name_of_user/ folder you right click on it and use gdebi to install software, the running program will install in the /usr/bin/ directory.

---

### Post by coldraven on 2011-07-18
It depends on what version of Ubuntu you have. Firstly I would move that folder to where you want it. For example /home/yourusername/Speccy
Then if using 10.10 or earlier, right click on "Applications", select "Edit Menus",  select the category you want and click "New Item". 
Title: Speccy16
Command: /home/yourusername/Speccy/[FONT=monospace]speccy16pp
You can get the idea by looking at the properties of other items.

If using 11.04 [/FONT][FONT=monospace][/FONT][FONT=monospace]you run the program and right click it's icon in the launcher and select "Keep in Launcher. It might work!
[/FONT]

---

### Post by zxMarce on 2011-07-18
@claracc:
There's no **.deb** file. Just a **.tar.gz**, and it's a Linux executable (though the application is compiled for other OSs). That is why I posted the program's page link.
Thanks for the **/usr/bin** folder clue, though.

@coldraven:
You're right, my OS is Ubuntu 10.04LTS.
Installing the app in my home folder sounds nice, but I also would like the app to be available to other users. How do I do that? Is **/usr/bin** the way to go? And, Should I just dump everything there, or -just to be tidy- make a folder just for the app's files?

Thanks to all,
Marcelo.

---

### Post by claracc on 2011-07-19
A .tar.gz file is a set of packed files and compressed.

In ubuntu you download this .tar.gz file wherever you want in your /home/name_of_user/ folder.

Then you have to unpacked and uncompress the archive: You can right click on the file and select extract or you can do through a command line in xterm: tar -xzvf name_of_the_file.tar.gz.

Onces unpackaged and uncompressed I think you'll find the .deb file ( the executable one in linux), so you can use gdebi to install it. Depending on the script to install the software you would can find the running files in the /home/name_of_user/..../bin/ folder and they will have a link to /usr/bin/ or the executables will install directly in /usr/bin/ .

The /usr/bin/ folder is that where there are all the running files and it is owned by root. I recommend you don't mess with it.

Other users can have access to the files through permissions policy (I think). Perhaps you have to wait to more expertize advice.

---

### Post by lisati on 2011-07-19
You might find some useful information if you open the file Speccy.html in your browser.

---

### Post by gandaran on 2011-07-19
> **zxMarce said:**
> @claracc:
There's no **.deb** file. Just a **.tar.gz**, and it's a Linux executable (though the application is compiled for other OSs). That is why I posted the program's page link.
Thanks for the **/usr/bin** folder clue, though.

@coldraven:
You're right, my OS is Ubuntu 10.04LTS.
Installing the app in my home folder sounds nice, but I also would like the app to be available to other users. How do I do that? Is **/usr/bin** the way to go? And, Should I just dump everything there, or -just to be tidy- make a folder just for the app's files?

Thanks to all,
Marcelo.
to manually install the folder with all files/these type of applications you should use either /opt or /usr/local directory's, (don't mess with /usr/bin) then create a desktop or applications menu launcher pointing to the executable path.

---

### Post by shashanksingh on 2011-07-19
> **zxMarce said:**
> Hello you all!

I have a binary program downloaded as .tar.gz. It's a ZX Spectrum emulator called [**Speccy** (version 1.7)]("http://fms.komkon.org/Speccy/"). It works flawlessly, but the program is sitting in a folder called **Speccy v1.7** in my desktop. The file listing is as follows:

```
~/Desktop/Speccy v1.7$ ls
DIDAKTIK.ROM  speccy-16bpp  TRDOS.ROM     ZXS48.ROM
PENTAGON.ROM  speccy-32bpp  ZXS128.ROM    ZXSPLUS2.ROM
SCORPION.ROM  Speccy.html   ZXS128TR.ROM  ZXSPLUS3.ROM
```There are two executables, **speccy-16bpp** and **speccy-32bpp**. The rest are emulated machines' ROMs and an HTML readme.

I would like the program to be *correctly installed*, with a Launcher in the Applications menu and all the bells and whistles. Problem is I come from a **C:\Program Files\** environment (sorry!) and don't have a clue of where to put the emulator files to begin with. My googling did not help either, maybe I'm using the wrong keywords.

I'd like help in at least having the emulator files where they're supposed to be -not my Desktop-, and I'd like it to have a launcher.

Can anybody help?

TIA,
Marcelo.


Could you explain what you did after extracting the files from the .tar.gz?

Here is what I have generally experienced:
In many cases (mostly in Linux, when you need access to system libraries), you "make" software from source code, i.e, u compile-configure software right from the source which generally comes in a .tar.gz. You also do get stuff which works when simply extracted.

You mite notice a .configure file when u extract that, and you proceed with a make command.

The .configure has the details of the installation directory and other useful options you can edit.

As mentioned, use /opt as the preferred directory for user apps.

---

