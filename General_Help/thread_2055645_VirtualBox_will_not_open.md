---
title: "VirtualBox will not open"
date: 2012-09-09
forum: General Help
---

### Post by PremiumG on 2012-09-09
I just installed VirtualBox from the Lubuntu Repositiories, and now, when I click Start>Accessories>VirtualBox... **nothing** :( The machine continues to remain nominal.

Did I install this incorrectly? I most certainly was not indicated so.

How can I run VirtualBox so I can begin learning Slackware? 

Unacceptable solutions include, but are most certainly not limited to: Just install Slackware alongside of your Lubuntu 64-bit partition.

Thank you for your time, consideration, help, and love.

---

### Post by vexorian on 2012-09-09
Try running virtualbox in a terminal window. No, this won't fix the issue, but there are good chances you are going to receive a message that can help us find out what the issue is.

---

### Post by PremiumG on 2012-09-09
How would I go about doing that? I am just coming from Windows and I have no experience with Linux, nor do I know what codes mean. #-o

Lo siento.

---

### Post by vexorian on 2012-09-09
Oh, don't worry.

First of all, you open a terminal in lubuntu. This page shows you how to do it in different versions: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

The terminal is going to be your worst enemy and your best friend in your Linux life. Specially if you want to try to learn slackware.

Once the terminal is open, type:

virtualbox

and press enter.

Then some messages might appear, select them with the mouse. Right click and "copy". Then paste them here.

---

### Post by PremiumG on 2012-09-09
brian@brzan:~$ virtualbox
mkdir: cannot create directory `/home/brian/.VirtualBox': Permission denied
Qt WARNING: QGtkStyle was unable to detect the current GTK+ theme.
Segmentation fault
brian@brzan:~$

And thank you for your patience and assistance.

---

### Post by vexorian on 2012-09-09
ok... Seems it is having issues with its config folder.

well, let us try creating a .VirtualBox folder

in terminal type:

mkdir ~/.VirtualBox

Let us make sure there are permissions:

chmod +rwx+rwx+rwx ~/.VirtualBox

And try again. If it does not work, try from the terminal too.

---

### Post by PremiumG on 2012-09-09
> **vexorian said:**
> ok... Seems it is having issues with its config folder.

well, let us try creating a .VirtualBox folder

in terminal type:

mkdir ~/.VirtualBox


brian@brzan:~$ mkdir ~/.VirtualBox
mkdir: cannot create directory `/home/brian/.VirtualBox': Permission denied

---

### Post by vexorian on 2012-09-09
I wonder if your home is for some reason getting mounted read only?

Try:

sudo mkdir ~/.VirtualBox

It will ask you your password. sudo makes a command run with administrator rights. If that does not work, then for some reason your home is getting mounted as read-only which is not nice.

(and if it works)

sudo chmod +rwx+rwx+rwx ~/.VirtualBox

---

### Post by PremiumG on 2012-09-09
Thank you, that worked... or, no issues were indicated. :D whats next!

EDIT: VirtualBox now opens. My original issue, it is solved, thank you good sir!

---

