---
title: "ubuntu boots to shell"
date: 2012-03-20
forum: General Help
---

### Post by smanz on 2012-03-20
Please help! I was trying to update drivers (Radeon HD 4200 series)and it kept failing, after following the advice found on a few threads from this site. my 1st problem occurred when my monitor wouldn't receive signal, i followed the advice given here. [http://ubuntuforums.org/showthread.php?t=1857059&highlight=effenberg+ati&page=2]("http://ubuntuforums.org/showthread.php?t=1857059&highlight=effenberg+ati&page=2") but now when rebooting, it boots directly to shell. please help!i have less than a months worth of experience using linux.

---

### Post by gleedadswell on 2012-03-20
I'm not the expert you want, but when those experts show up one of the things they'll probably ask you to do is post the contents of your 

/var/log/Xorg.0.log

file.  That is likely to give them some useful info on what is causing the problem.  A good place to post it is pastebin

[http://pastebin.ca/]("http://pastebin.ca/")

Stick it there and then post back here with the link.

Another thing to try, which the link you referred to mentioned, is to edit your

/etc/default/grub

It should contain a line that looks like:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Back it up first!  Do

sudo cp /etc/default/grub /etc/default/grub.bak

Then do:

sudo nano /etc/default/grub

which will open a text editor that runs in the console.  Replace that line above with: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash nomodeset"

Save it and exit the editor.  Then, from the command line run

sudo update-grub

Then reboot.  That might get you into a desktop environment but with somewhat downgraded graphics capabilities compared to what your hardware should be able to do.

---

### Post by Bucky Ball on 2012-03-21
When you are sitting at the blinking cursor after boot, could you try inputting:

```
startx
```What happens? Report result back here, please.

Also, try adding 'nomodset', as gleedadswell suggests (good advice but please put code between code tags; [code] to start and add a / before the word 'code' with the end tag or 'Go Advanced', mark out the code and hit '#'). ;)

---

### Post by smanz on 2012-03-21
when i tried imputing /var/log/Xorg.0.log

i get a message that reads "file directory does not exist"

---

