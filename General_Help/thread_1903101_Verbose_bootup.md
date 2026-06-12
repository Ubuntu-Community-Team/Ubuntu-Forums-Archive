---
title: "Verbose bootup"
date: 2012-01-01
forum: General Help
---

### Post by birdfoot on 2012-01-01
I'm running Lubuntu 11.10 and when my computer boots, I would just like to have a verbose text bootup. You know, the kind that shows all the details of the boot up process, so I can see if anything goes wrong.

Some Googling points to editing GRUB2, but I just can't understand it. Isn't it for a menu if you have more than one operating system? 

I should note that I have an old monitor and that it turns off briefly during boot up then turns on again when Lubuntu desktop loads.

Thanks.

---

### Post by oldfred on 2012-01-01
You just need to edit grub.cfg and run sudo update grub. Or if just one time, use shift to get to menu and use e for edit and remove quiet & spash.

gksudo gedit /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMDLINE_LINUX
    * Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   * This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 


then 

sudo update-grub

---

### Post by birdfoot on 2012-01-01
> **oldfred said:**
> You just need to edit grub.cfg and run sudo update grub. Or if just one time, use shift to get to menu and use e for edit and remove quiet & spash.

gksudo gedit /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMDLINE_LINUX
    * Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   * This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 


then 

sudo update-grub


Thanks. Unfortunately that didn't work.

---

### Post by birdfoot on 2012-01-01
I should add that I would like a verbose shutdown.

---

### Post by birdfoot on 2012-01-02
> **oldfred said:**
> You just need to edit grub.cfg and run sudo update grub. Or if just one time, use shift to get to menu and use e for edit and remove quiet & spash.

gksudo gedit /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMDLINE_LINUX
    * Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   * This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 


then 

sudo update-grub

You didn't reply again. Was there some more information needed?

---

### Post by oldfred on 2012-01-02
I do not know about shut down. I am not sure if someone asked before or not as I did not save any notes on that.

The edit of grub and the sudo update-grub should change how it boots. What is happening when you reboot?

---

