---
title: "Disk check and error in start up"
date: 2010-02-27
forum: General Help
---

### Post by Aaron Durant on 2010-02-27
Hello,

Today i was using Ubuntu 9.10 on my computer for about 3 hours. I then had to leave my computer, so shut down the internet and left it. When i came back about 15 minutes later, ubuntu refused to open firefox for me (whenever i clicked firefox it said startting firefox, but it nevery actually loaded). I then tried to open another program, but that also failed to load. I tried to restart my computer, but clicking restart simply closed the menu. I then had to turn of my computer using the power button. During shut down text appeared on the screen that does not usually appear talking about some kind of error. (I did not get to read this properly)

On starting up my computer again, Ubuntu started to load and then came up with a message saying that it was performing a disk check of some kind. at 48% it then went to text screen saying that something was wrong with the disk and then had the option for me to enter something. Not knowing what to put i then restarted the computer, to get the same error.

I am now using ubuntu 9.10 live CD.

Does anyone know what the problem is/

Thanx

Aaron

---

### Post by cjhabs on 2010-02-27
It sounds like it is failing when running the fsck disk check. You should post the message and question here so someone can look at it. Typically you have to reply "yes" when it wants to fix something because it won't boot with a "dirty" disk.

---

### Post by Aaron Durant on 2010-02-27
When loading Ubuntu, underneath the logo it says:

File System Checks are in Progress
/)/dev/disk/by-uuid/d2f70070-db7e-4297-a81d-a14be2516e15
Press ESC to cancel checks

When the file system check gets to 48% it then goes to a screen saying:

upsplash: setting mode 1152x864 failede-4297-a18d-a24bc1516e15
upsplash:using mode 1024x768
Mount of file system failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
root@aaron-desktop:~#

If I press CONTROL-D  it goes back to the file system check and repeats. 
If i press ESC to skip the tests it goes to the second screen

---

### Post by Aaron Durant on 2010-02-27
Hi,

I have managed to fix this problem my self. For anyone else who has this problem you have to run Filesystem Check manully by typing in "fsck", then typing y to fix any errors it finds when it asks if you want to fix them

Aaron

---

