---
title: "Need to link a shared drive under places?"
date: 2009-10-23
forum: General Help
---

### Post by RaveJunkie on 2009-10-23
[COLOR="RoyalBlue"]I searched "linking network drive" but came up empty.

I can boot up and then click and mount my shared network drive.  I mount my other six internal drives via "ntfs-config" app on boot and they are listed under "my computer" i can read and write to them and i have my music pictures ect shared and on them i have pressed "crtl+shift" and made shortcuts in my home folder. All is well there and work flawless.  My problem is on reboot the symbolic link i make to my network drive goes away...... is there a way to make a link to this so its there on reboot or do i have to mount it everytime?[/COLOR]

---

### Post by alphaniner on 2009-10-23
A symbolic link shouldn't disappear if it's target is unavailable, it should show up as broken.  I make symlinks through the terminal so I don't know what Ctrl+Shift does.  But my guess is that you're not really making a symbolic link.  Try

```
ln -s /full/path/to/network_drive ~/
```

This won't make the share automatically mount though, you'll need to edit your fstab or use one of the GUI tools to do that.

---

### Post by RaveJunkie on 2009-10-23
yes sorry your right, upon reboot its not "gone" its broken. used the wrong term.  I will try that command to make the link and ill do some research and edit my fstab to add in the network drive.  thank you.

---

### Post by alphaniner on 2009-10-23
No, if it is just broken there is no need to use the command.  That is, if the link works after you mount the share manually.

Like you said, what you need to focus on is getting the share mounted automatically.  I recommend the post [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131") here on the forums.  It's how I learned.

---

### Post by RaveJunkie on 2009-10-23
thank you sir, I need to learn how to do it without all my silly GUI's  ;)  Thanks for the link too!  I will have to get on this, I just started using Ubutnu about 8-10 months ago, and at first had so many issues (SLI, mounting drives, x64bit flash) i had issues with permissions with the the fstab last go around so i hope im a bit more experienced this time around and with this tutorial i should be ok.   thanks again.

---

### Post by alphaniner on 2009-10-23
It was the same way for me.  A lot of things were :confused::mad:](*,):cry: early on.  I set them aside for a while to do more basic things and when I came back to them it was like, "how was this ever difficult?"

---

