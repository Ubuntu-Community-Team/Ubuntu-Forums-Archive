---
title: "FaceBook Flash Games Does Not Work"
date: 2010-06-14
forum: General Help
---

### Post by yapanitz on 2010-06-14
_**[SIZE=5]My Facebook Flash games stops loading and does not continue. Here's the screenshot.[/SIZE]**_

[[IMG]http://img715.imageshack.us/img715/2889/screenshotninjawarzonfa.th.png[/IMG]]("http://img715.imageshack.us/i/screenshotninjawarzonfa.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

_**[size="5"]Even Flash Videos does not work[/size]**_

---

### Post by lovinglinux on 2010-06-14
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Sandertje on 2010-06-14
Are you using a 32bit or 64bit system? (ubuntu-restricted-extras on 64bit systems apparently comes with the 32bit flash plugin, which breaks flash. There is a fix for that however :-) see here: [http://ubuntuforums.org/showthread.php?t=1470810](http://ubuntuforums.org/showthread.php?t=1470810) )

---

### Post by NTHQ on 2010-06-14
I got Flash to work unintentionally...
On a fresh install of Lucid Lynx, I had installed the Ubuntu Restriced Extras package. This obviously wasn't good enough. So when I went on YouTube, I clicked on the button to install missing plugins. I decided to try out gnash instead of Adobe since I couldn't play Facebook games before with it. To my suprise, everything was working perfectly; including Facebook games.
The next time I booted my computer, however, nothing worked. Thinking that I just got lucky the first time and the gnash wasn't stable enough to use, I did a complete removal of it using Synaptics. And then everything suddenly worked again...
I tried rebooting my computer a couple of times and it's still working now. This probably won't work for everyone but it's worth a try. :)

---

### Post by yapanitz on 2010-06-14
> **lovinglinux said:**
> Install [FLASH-AID]("http://flash-aid-extension.blogspot.com") extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR=Sienna]**Flash Optimization**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html") section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").

This worked for me thanks. Anyway I have a confusion. I know I installed the 32-bit Ubuntu system but Flash Aid says my Firefox was a 64-bit one. DO you think I installed Ubuntu 64-bit?

---

### Post by lovinglinux on 2010-06-14
> **yapanitz said:**
> This worked for me thanks. Anyway I have a confusion. I know I installed the 32-bit Ubuntu system but Flash Aid says my Firefox was a 64-bit one. DO you think I installed Ubuntu 64-bit?

Paste the result of this command:

```
uname -a
```

---

### Post by yapanitz on 2010-06-14
> **lovinglinux said:**
> Paste the result of this command:

```
uname -a
```

Linux ubuntu 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

Sir, one more thing. How about flash videos like youtube? I won't play on the youtube website. Help pls

---

### Post by sandyd on 2010-06-14
> **yapanitz said:**
> Linux ubuntu 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 **x86_64** GNU/Linux

Sir, one more thing. How about flash videos like youtube? I won't play on the youtube website. Help pls
thats 64bit ubuntu

this is an issue because of [http://ubuntuforums.org/showthread.php?t=1507514](http://ubuntuforums.org/showthread.php?t=1507514)

there is no x64 flash at the moment. the version that flash-aid installs (I already talked w/ lovinglinux about this earlier) is the 32bit version that runs on 64bit systems through a program called nspluginwrapper.  

This is not a really good way to run flash, as its not perfect. As a result, weird stuff occasionally pops up.

However, you can still use the x64 flash version, provided you are not concerned about the security issue.

If you aren't concerned and wish to proceed, please click on the link called "adobe tools" in my signature.


If you want to fix the "cannot click" issue that may still occur (if using 32bit flash), try running this in the terminal.
```

sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

```add ```

export GDK_NATIVE_WINDOWS=1
```to the end and click save.

---

### Post by yapanitz on 2010-06-14
> **carlee said:**
> thats 64bit ubuntu

this is an issue because of [http://ubuntuforums.org/showthread.php?t=1507514](http://ubuntuforums.org/showthread.php?t=1507514)

there is no x64 flash at the moment. However, you can still use the x64 flash version, provided you are not concerned about the security issue.

If you aren't and wish to proceed, please click on the link called "adobe tools" in my signature

Well, I guess I need to reinstall Ubuntu. I though it was a 32-bit system 'coz I downloaded the i386 ISO.

Is it wrong? Please give me the version I should download.

---

### Post by sandyd on 2010-06-14
> **yapanitz said:**
> Well, I guess I need to reinstall Ubuntu. I though it was a 32-bit system 'coz I downloaded the i386 ISO.

Is it wrong? Please give me the version I should download.
you got over 4GB of ram?

if you do, I advise you to just brave it out, and use one of the options described in my previous post (sorry, i updated it while you were still posting!).
flash is only the only issue w/ 64bit.

otherwise
[http://mirror01.th.ifl.net/releases/lucid/ubuntu-10.04-desktop-i386.iso](http://mirror01.th.ifl.net/releases/lucid/ubuntu-10.04-desktop-i386.iso)

---

### Post by yapanitz on 2010-06-14
> **carlee said:**
> you got over 4GB of ram?

if you do, I advise you to just brave it out, and use one of the options described in my previous post (sorry, i updated it while you were still posting!).
flash is only the only issue w/ 64bit.

otherwise
[http://mirror01.th.ifl.net/releases/lucid/ubuntu-10.04-desktop-i386.iso](http://mirror01.th.ifl.net/releases/lucid/ubuntu-10.04-desktop-i386.iso)

Its only 2Gb. Why?

BTW, the ISO file you gave is the same one that I downloaded. How come it turned out into a 64-bit system? I used my USB disk to install Ubuntu.

---

### Post by sandyd on 2010-06-14
> **yapanitz said:**
> Its only 2Gb. Why?
alright, go back to 32bit.

If you got over 4GB of ram, going to 32bit could pose a little problem, and will involve something called the PAE kernel in order to utilize over 3.7 GB of ram. Which is not all that pretty at times. 

If you got under 4GB of ram, go ahead and install 32-bit. 

p.s. Ubuntu x64 actually does use more RAM than 32bit, which is the second reason why im asking if you have over 32bit.

---

### Post by sandyd on 2010-06-14
> **yapanitz said:**
> Its only 2Gb. Why?

BTW, the ISO file you gave is the same one that I downloaded. How come it turned out into a 64-bit system? I used my USB disk to install Ubuntu.
I actually can't answer that, because I have never installed it using the USB disk method.

---

### Post by yapanitz on 2010-06-14
> **carlee said:**
> I actually can't answer that, because I have never installed it using the USB disk method.

I install Ubuntu using my flash disk. Maybe I'll try downloading your ISO and then comment after. Thank you so much for the help :p

---

### Post by yapanitz on 2010-06-15
> Linux yapanitz-ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux



I guess I got it right this time? I'm updating again now. Thank you for your help. I saw the problem. The installation instructions on the Ubuntu site is a failure 'coz it prompts to download the 64-bit system that's why I got the 64-bit at the first place. I google a new procedure and I found the right one.

---

### Post by sandyd on 2010-06-15
> **yapanitz said:**
> I guess I got it right this time? I'm updating again now. Thank you for your help. I saw the problem. The installation instructions on the Ubuntu site is a failure 'coz it prompts to download the 64-bit system that's why I got the 64-bit at the first place. I google a new procedure and I found the right one.its right.
and it prompts to download the 64-bit version because your processor supports 64bit.

---

