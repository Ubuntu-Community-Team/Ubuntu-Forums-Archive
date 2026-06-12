---
title: "Ubuntu UDF DVD File Reading Problem?"
date: 2010-07-29
forum: General Help
---

### Post by Dak446 on 2010-07-29
Hey everyone, as you can tell, I'm new to Linux and Ubuntu.  I've always been a PC/Windows guy.  I recently purchased some computer parts for a carpc that I am putting together to put into my truck.  The 40GB SSD harddrive that I got for dirt cheap already has Ubuntu loaded onto it.  Through my school, I downloaded Windows 7 64-bit version onto a DVD off of my laptop Windows 7 64-bit. 

Problem is, I set up  my carpc computer (running it off of a 12v power supply in my house just to set it up) that has Ubuntu on it's hdd, and now, I can't get it to read the dvd to install Windows 7.  I am not comfortable running Ubuntu on my carpc at the moment (new to programming and Linux, etc) and would like to have plain ole' W7 on it, so that I can easily switch back and forth between my laptop and carpc.  

Has anyone else had the problem of Ubuntu not being able to read a dvd, specifically an executable or .box?  Or other ideas?  Thanks!

---

### Post by ubunterooster on 2010-07-29
Can it read *any* DVDs?

---

### Post by Dak446 on 2010-07-29
I just tried Role Models, and a window popped up asking me to use Movie Player to play it.  I said yes, and it opened Movie Player, but an error window popped up saying "no URI handler implemented for "dvd"

---

### Post by ubunterooster on 2010-07-29
You need to change the boot order to boot off of the DVD first so You can install Windows

---

### Post by Dak446 on 2010-07-29
Hrm, I wonder how I could do that?  Just go to the BIOS and tell it to boot from the CD drive instead of Windows first?  I wonder if that would work

---

### Post by samijam on 2010-07-29
If your dvd was made correctly (i.e. bootable) then you should be able to set your boot order in the system BIOS to boot from DVD drive before hard drive.  Then it should boot the dvd and take you into the windows installation.

---

### Post by Dak446 on 2010-07-29
Ok.  I gotta run to walmart real quick to grab a USB keyboard, so I can access BIOS, and then I'll let you know how it goes

---

### Post by Dak446 on 2010-07-30
Ok, so I got a keyboard, and I can't boot my optical drive because it is solely USB.  So that's a problem

---

### Post by Dak446 on 2010-07-30
Any ideas?

---

### Post by cavalier911 on 2010-07-30
Make ISO image from the Win 7 DVD install disk.
Use this tool with the ISO to make bootable Win 7 USB flash drive.

[http://wudt.codeplex.com/](http://wudt.codeplex.com/)

---

### Post by Dak446 on 2010-07-30
Seems like a great idea.  I tried it, and it got 99% thru and said that it couldn't, and that I needed to check my ISO and USB disk.  WTF, all I wanna do is put Windows 7 on my computer! Man, this is irritating, but thanks for the good idea!  I'm gonna try it again...wish me luck

---

### Post by Dak446 on 2010-07-30
Nothin.  Still not having any luck.  Is there a program I could put on my Ubuntu computer that would allow me to read UDF files? Seems simple enough

---

### Post by sydbat on 2010-07-30
> **Dak446 said:**
> Nothin.  Still not having any luck.  Is there a program I could put on my Ubuntu computer that would allow me to read UDF files? Seems simple enoughMaybe try this - [http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/](http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/)

I found it by asking my [best friend]("http://www.google.com").

---

### Post by Dak446 on 2010-07-30
I've tried it too.  No workie

---

### Post by sydbat on 2010-07-30
> **Dak446 said:**
> I've tried it too.  No workieHave you got all the codecs possible? Might be one or two that were not installed that you/application did not realize was necessary?

---

### Post by philinux on 2010-07-30
If the OP wants to install windows then this DVD needs to be booted not readable from an OS I thought.

---

### Post by Dak446 on 2010-07-30
I'm not sure about the codec thing.  How could I find out?  What codec would I need?  I'm COMPLETELY new to Linux/Ubuntu, so sorry for being such a newb :(

---

### Post by ubunterooster on 2010-07-30
Like the post above you says, you don't need to worry about codecs, you need to find a way to boot off of the DVD

---

