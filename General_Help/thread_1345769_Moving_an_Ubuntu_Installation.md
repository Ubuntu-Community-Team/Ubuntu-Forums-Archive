---
title: "Moving an Ubuntu Installation"
date: 2009-12-04
forum: General Help
---

### Post by The Zezima of &#370;buntu on 2009-12-04
I wanted to know if it's possible to take an "in windows" installation of Ubuntu and turn it into its own installation (outside of Microsoft Windows).

What I want to do is keep my Ubuntu installation since I have customized it so much, but I also want to format my Windows Vista and install a clean version of XP. When I first installed Ubuntu I created a partition in Windows.

Also would it be possible to grab the Ubuntu folder out of Vista and save it onto an external drive, install XP, and move the Ubuntu folder back into windows? And what files would I have to modify to make it read Ubuntu as being an operating system during boot up again?

I have Windows Vista 32Bit as Primary OS, and running 9.10 64Bit Ubuntu if that matters in this situation. Thanks in advance for any help.

---

### Post by hardfire_avk on 2009-12-04
what do you mean you installed it into vista ??

---

### Post by The Zezima of &#370;buntu on 2009-12-04
> **hardfire_avk said:**
> what do you mean you installed it into vista ??

I was in Windows when I put the CD in and installed it. There is a folder in my windows C:\ that is housing Ubuntu. (C:\Ubuntu) But I don't need to be logged into Windows to use Ubuntu. It's on the boot up list.

---

### Post by The Zezima of &#370;buntu on 2009-12-05
Still need some help with this. Searched the forums and found some older stuff but not exactly what I was looking for.

---

### Post by arashiko28 on 2009-12-05
Ok you made a Wubi installation.

all of your customization will be on your home folder, if you keep it safe along with the hidden folders, you can have it back. Ie; I have a separate partition for /home, so I can format / which is the filesystem and once it comes back up, everything is as I left it, including wallpapers.

To do this the way I have it, yo have to mark the partition /home during installation, otherwise will become another partition and you'll have to mount it manually every time.

The programs you have installed will have to be installed again. Ie; Acrobat Reader, Wine... but they will have the same config. you have right now.

Try it and good luck!

---

### Post by arashiko28 on 2009-12-05
An idea... have you thought about double booting?

Now that you're installing XP, you'll have the chance to partition the disk yourself.

In case you're insterested, here's a small howto:

1. Install Windows XP and choose partition size for drive C. Optional drive D [Recommended]
2. Leave an unused space for Ubuntu
3. Install Ubuntu on the empty space. Create Swap partition [Same size as your RAM, double of you want to hibernate] Create / partition. (Optional /home partition) - Recommended.

And you're done! You'll see the same screen when you boot up and can choose between Ubuntu or Windows.

---

### Post by The Zezima of &#370;buntu on 2009-12-10
> **arashiko28 said:**
> An idea... have you thought about double booting?

Now that you're installing XP, you'll have the chance to partition the disk yourself.

In case you're insterested, here's a small howto:

1. Install Windows XP and choose partition size for drive C. Optional drive D [Recommended]
2. Leave an unused space for Ubuntu
3. Install Ubuntu on the empty space. Create Swap partition [Same size as your RAM, double of you want to hibernate] Create / partition. (Optional /home partition) - Recommended.

And you're done! You'll see the same screen when you boot up and can choose between Ubuntu or Windows.

That means I have to start with a new installation of Ubuntu. I want everything I already have in my ubuntu. All the installed packages and all that good stuff. Never mind, I'll figure something out, I'm good at figuring things out myself :)

---

