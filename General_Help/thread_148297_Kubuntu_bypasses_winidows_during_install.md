---
title: "Kubuntu bypasses winidows during install"
date: 2006-03-21
forum: General Help
---

### Post by hikmat on 2006-03-21
I tried 2 installations of Kubuntu-- an automated one and an 'expert' one. In both cases, before installing Grub, Kubuntu doesnt ask the usual question that begins with : "It seems you have another operating system etc.,..."

What happened? In both cases Grub doesn't see Windows (sda2). I have had to install Acronis OS selector to give me dual boot option, but it is a pain since it is slow.

Can I edit the Grub configuration file to make it see Windows? If so, any link to where I can copy the right kind of text?

Many thanks.

hikmat

---

### Post by DJ Scribblinni on 2006-03-21
Hows it going dude, I don't know how much I can be but I can lead you to the menu list file which is what GRUB looks at to show which operating system you want to choose from and it also tells grub where to look for the OS.  The file is located /boot/grub/menu

This is the clip that is at the end of my list that tells it where to go for windows on hda1
```
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Also in the file are little tidbits of info that will show you a couple of things you can do...
Hope that helps you any possible

---

### Post by hikmat on 2006-03-21
Thanks for the prompt reply! I will try that.

---

