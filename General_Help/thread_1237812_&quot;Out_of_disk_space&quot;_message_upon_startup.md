---
title: "&quot;Out of disk space&quot; message upon startup"
date: 2009-08-11
forum: General Help
---

### Post by thatstheguy on 2009-08-11
Hey ya’ll,
   
  I’m having trouble booting up my laptop, on which I recently installed Ubuntu 9.04.  I was under the impression that Ubuntu removed all components of Windows Vista, which was previously installed on the machine, but alas, it seems to have simply been installed alongside it.  Now I’m completely out of disk space, which I believe is probably because the partition I created for Ubuntu was not big enough.  This is confirmed by the following error message, which is seen upon startup:
   
  (in recovery mode and regular--9.04 kernal--boot):
  “GDM could not write a new authorization entry to disk.  Possibly out of diskspace.  Error: No space left on device.”
   
  So then I hit Enter, and got this:
   
  “Could not start the X server (your graphical environment) due to some internal error.  Please contact your system administrator or check your syslog to diagnose.  In the meantime this display will be disabled.  Please restart GDM when the problem is corrected.”
   
  Baffled, I did a search a couple days ago and realized Ubuntu needs more room than I’m giving it.  
   
  According to TeoBigusGeekus, who addressed a similar-sounding issue 3 weeks ago:
   
  “Anyway, boot with a live cd, open terminal, type 
  Code:
  gksudo gparted
  to start gnome partition manager and do any changes you like.”
   
  [[http://ubuntuforums.org/showthread.php?t=1217459&highlight=no+disk+space]]("http://ubuntuforums.org/showthread.php?t=1217459&highlight=no+disk+space%5D")
   
  I don’t know how to do this, however.  What “live cd” should I be running?  I think I lost my Ubuntu 9.04 disk, if that is what Teo is referring to.  And I am completely inexperienced when it comes to making changes to my computer’s partitions.
   
  How can I free up some space and get this machine, as well as Ubuntu, up and running again?
   
  Many thanks for your help.
   
  Chris

---

### Post by michy99 on 2009-08-11
Here is a thread dealing with your very problem:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

Very easy to follow.

---

### Post by dcstar on 2009-08-11
> **thatstheguy said:**
> 
.........
How can I free up some space and get this machine, as well as Ubuntu, up and running again?


There are many posts on this exact issue, it is usually caused by log files being over-filled with error messages.

Do a search for a fix that will allow you to boot up, then you can investigate the real problem.

---

### Post by 3rdalbum on 2009-08-11
Get a hold of another copy of Ubuntu 9.04 and run the installer again, and this time choose to "Erase entire disk" rather than "Resize a partition". This will create a single-boot Ubuntu system.

---

### Post by thatstheguy on 2009-08-13
> **3rdalbum said:**
> Get a hold of another copy of Ubuntu 9.04 and run the installer again, and this time choose to "Erase entire disk" rather than "Resize a partition". This will create a single-boot Ubuntu system.

OK, I found my disk and I'm running the installer. When you say "Erase entire disk," you mean "Use the entire disk," right?  Not to split hairs or anything--that's the wording, and I want to make sure I don't blow anything up.

Thanks,
Chris

---

