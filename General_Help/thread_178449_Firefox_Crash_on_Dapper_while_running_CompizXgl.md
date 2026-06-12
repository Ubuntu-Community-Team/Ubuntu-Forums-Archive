---
title: "Firefox Crash on Dapper while running Compiz/Xgl"
date: 2006-05-17
forum: General Help
---

### Post by gkzhang on 2006-05-17
I think the problem is with flash.
I am running an Amd 64 system with compiz/xgl now installed.
I think that everytime it loads up something with flash in firefox, it crashes
Here's the output.
```
sh-3.1$ firefox
NP_Initialize
New
Warning: Color name "black" is not defined
SetWindow
SetWindow
SetWindow
New
SetWindow
SetWindow
SetWindow
SetWindow
SetWindow
NewStream
WriteReady
Write
decoding...
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 54 error_code 17 request_code 129 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I'm quite a n00b to linux.  I've searched all over and can not seem to find a solution to this problem.  Can someone help me?

Thank You
William Zhang

---

### Post by Dr. Nick on 2006-05-17
[quote=gkzhang]I think the problem is with flash.
I am running an Amd 64 system with compiz/xgl now installed.
I think that everytime it loads up something with flash in firefox, it crashes
Here's the output.
```
sh-3.1$ firefox
NP_Initialize
New
Warning: Color name "black" is not defined
SetWindow
SetWindow
SetWindow
New
SetWindow
SetWindow
SetWindow
SetWindow
SetWindow
NewStream
WriteReady
Write
decoding...
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 54 error_code 17 request_code 129 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
``` 
I'm quite a n00b to linux.  I've searched all over and can not seem to find a solution to this problem.  Can someone help me?

Thank You
William Zhang[/quote]

How are you getting flash on amd64? Do you have the 64bit version installed or are you just using teh 32bit ver of ubuntu? 

I used to run the 64bit a few monts ago and at that time thier was no official flash made for amd64 by macromedia, not sure where that issue is today. I did though always get crashing when using a 3rd party flash app found in the repositories.  I would try to rid yourself of flash now and see if it crashes, also try without xgl and see if it still crashes

---

### Post by gkzhang on 2006-05-17
I'll tried without compiz/Xgl and the sites loaded up fine.
I'll try again to make sure.

**Edit:**  I tried in regular KDE and it goes to flash sites.  However in XGL/Compiz mode, it still crashes whenever I go into gmail.  
About the time right after it loads up the google talk applet thing.
So is it a javascript error or something of the sort?

Thanks for the response.

---

### Post by Primal-id on 2006-05-21
I'm having the same problem:



The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 37 error_code 17 request_code 129 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


I've been able to trace it down to flash related sites and seems to have happened within the last week. I update everytime I get notified so I'm assuming one of the updates is causing this. Seems to happen weather or not i'm actively running compiz/xgl effects. I have not tried booting into x without the xgl turned on as an option.

---

### Post by Al3xanR0 on 2006-05-23
[QUOTE=gkzhang]I think the problem is with flash.
I am running an Amd 64 system with compiz/xgl now installed.
I think that everytime it loads up something with flash in firefox, it crashes
Here's the output.
```
sh-3.1$ firefox
NP_Initialize
New
Warning: Color name "black" is not defined
SetWindow
SetWindow
SetWindow
New
SetWindow
SetWindow
SetWindow
SetWindow
SetWindow
NewStream
WriteReady
Write
decoding...
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 54 error_code 17 request_code 129 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I'm quite a n00b to linux.  I've searched all over and can not seem to find a solution to this problem.  Can someone help me?

Thank You
William Zhang[/QUOTE]


I had the same isuue only I was running xcompmgr, Anyway try this edit the xorg.conf by changing the following 

to:

```
Section "Screen"
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  DefaultColorDepth 24
```

From:

```
Section "Screen"
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  DefaultColorDepth 16
```

I caution you, this should not impact the /etc/X11/xorg.conf negatively, but I would create a backup of it before making changes just in case by typing 

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
```

---

### Post by phyzome on 2006-05-24
I removed the libflash0c2 package (and its two dependants, libflash-mozplugin and libflash-swfplayer).  I still have flashplayer-mozilla.  Now firefox doesn't crash.

---

### Post by husher on 2006-05-25
[QUOTE=phyzome]I removed the libflash0c2 package (and its two dependants, libflash-mozplugin and libflash-swfplayer).  I still have flashplayer-mozilla.  Now firefox doesn't crash.[/QUOTE]

I can confirm the same behavior on i386, and removing those 2 packages seems to fix the problem.   Thanks for the info.

---

### Post by Krash1201 on 2006-05-30
I am having this same problem, but on i386.  The interesting variation is that libflash and its dependecies were not installed when the problem occured.  I am also using ubuntu on a laptop with an ATI graphics card, so i can't change xorg.conf because there are variable options.  i used bumps to install flash initially, so flashplugin-nonfree is installed, not flashplugin-mozilla.  To remedy the situation, i uninstalled flashplugin-nonfree, then installed libflas0c2 and libflash-mozplugin, but not libflash-swfplayer.  everything seems to work fine now.

---

### Post by Krash1201 on 2006-06-01
here is a new permutation on the problem, after completely reinstalling flash and after a restart, yahoo mail beta crashes firefox.  Any idea if this is related to the flash problem?  I know yahoo mail beta doesn't support linux, but it didn't cause this problem before the most recent update in dapper.  any ideas?

---

### Post by ep0ch on 2006-06-03
It also happens with GMail/Digg on Dapper XGL (amd64).


Edit:

It seems to be an unmet dependancy on libXt.so amongst others. Running the following appears to prevent the crash:

```

sudo apt-get install libxext-dev

```

---

### Post by imjustabill on 2006-06-03
[QUOTE=phyzome]I removed the libflash0c2 package (and its two dependants, libflash-mozplugin and libflash-swfplayer).  I still have flashplayer-mozilla.  Now firefox doesn't crash.[/QUOTE]

That seemed to fix everything for me as well. Thanks!

---

### Post by Krash1201 on 2006-06-07
Still having this crash problem intermitantly with yahoo mail beta, and sometimes after i have been using firefox for a while.   xorg.conf has depths set to 24 through the ATI drivers, also installed libxext-dev, but apparently to no avail.  switching between flash nonfree and libflash doesn't seem to make a difference.  any other ideas?

---

### Post by Arawn on 2006-06-16
Krash1201 wrote:
> To remedy the situation, i uninstalled flashplugin-nonfree, then installed libflas0c2 and libflash-mozplugin, but not libflash-swfplayer. everything seems to work fine now.

A friend of mine tried making Compiz/XGL work on my computer, after upgrading it from Breezy. As you can guess, playing Flash content started crashing Firefox.

Just to say that Krash1201 solution worked, thank you very much Krash1201.

I haven't tried any of the other solutions presented. I haven't got Compiz/XGL working, my friend wasn't able/didn't had time to make it work.

Thank you all, for your helpful hints. :D

---

### Post by dimis on 2006-07-13
> **phyzome said:**
> I removed the libflash0c2 package (and its two dependants, libflash-mozplugin and libflash-swfplayer).  I still have flashplayer-mozilla.  Now firefox doesn't crash.
Thank you very much. This was the solution for my installation as well! :D

---

