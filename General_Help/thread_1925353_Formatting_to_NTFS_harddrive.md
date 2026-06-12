---
title: "Formatting to NTFS harddrive?"
date: 2012-02-14
forum: General Help
---

### Post by daren1093251 on 2012-02-14
Hello, I've been using Ubuntu for quite a while now, for school, mostly, but earlier today I was trying to re-install Windows (TO do a dual-boot) but on the installation it told me that Windows could not be installed due to my hard drive (On a laptop, if theirs a difference)is not NTFS. I have no idea what this means, if anybody could tell me how to change my hard drive back to NTFS so I could dual boot both OS's, I would really appreciate it. Thanks!

---

### Post by QIII on 2012-02-14
May I ask what you want to use Windows for?  I don't intend to dissuade you.  If you need Windows then by all means use it.

But there is an easy path here and a "hard" one.

---

### Post by runny6play on 2012-02-14
Your going about it the wrong way.... download gparted and resize the disk so you can make a partion for windows.. you'll also want to reinstall grub

---

### Post by QIII on 2012-02-14
If only it were that easy...

---

### Post by daren1093251 on 2012-02-14
> **QIII said:**
> May I ask what you want to use Windows for?  I don't intend to dissuade you.  If you need Windows then by all means use it.

But there is an easy path here and a "hard" one.

I want windows to play my games when i'm on the bus, or waiting, and for other applications so I don't need to use Wine. I use Ubuntu because of the very quick start up to be able to just open it up with ease and write my notes. If it's a lot of trouble dual-booting, I might as well just get WIndows. I'm not a computer genius haha.

---

### Post by Mark Phelps on 2012-02-14
You don't need to justify using Windows -- at least, not to me, as I continue to use it daily.  There's stuff there I need to use and have not been able to get it working in Linux.

As to the install problem, MS Windows doesn't understand any filesystems but its own.  If your drive is entirely formatted using Linux filesystems, that can confuse the installer.

Your best bet would be to boot from an Ubuntu desktop CD, select Try Ubuntu, and use the Gnome Partition Editor to shrink down the Linux filesystem partition to make some free room for Windows.

Then, when you boot from the Windows DVD, it should see the free space and allow you to install to that.

---

### Post by QIII on 2012-02-14
My intent was not to ask for justification, only to see if virtualizing might be an easy answer.

Doesn't sound like it from the posted response.

We all know the frustration that can come from a "Linux first" installation of Windows.

---

### Post by oldfred on 2012-02-14
Windows requires a primary NTFS formated partition set as active or with the boot flag from gparted.

---

