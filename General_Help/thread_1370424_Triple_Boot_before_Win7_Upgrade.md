---
title: "Triple Boot before Win7 Upgrade"
date: 2010-01-02
forum: General Help
---

### Post by Setarkos on 2010-01-02
Hi there!

I just received my new laptop (Lenovo T500) and it came with Vista and a free Upgrade option which I ordered already. 
I would like to install Ubuntu 9.10 and Fedora 12 besides Win7. Here are my questions:

1. Can I install Ubuntu and Fedora before I upgrade to Win7 (it will be shipped within 1-2 weeks) or should I rather wait?

2. I would like to have 4 partitions: one for each OS and one for file storage. Its a 160GB hard drive, what partition sizes would you reccommend? 

3. In which order should I install the OS's and how do I do that exatly. (My experiences: I have only installed Ubuntu once as the only OS and later added WinXP.)

---

### Post by Leppie on 2010-01-02
1. i'd say install fedora first then ubuntu, but i don't know what bootloader fedora 12 uses. ubuntu 9.10 (karmic) uses grub2, which can easily be restored and personalized. remember to resize your windows partition in windows before installing the linux systems.
when your win7 upgrade arrives, you can just install it and then restore grub2.

2. i haven't really used win7, but the system partitions depend mostly on what you're going to install. i'd say that for the linux partitions most probably about 15gigs each would suffice, but again this depends on what you're installing. windows systems have much higher requirements for disk space. just remember to resize your windows partition from within windows first. if you want to use hibernation you want to add a swap partition of about the same size as your ram.

3. see 1.

---

### Post by Setarkos on 2010-01-02
> **Leppie said:**
> 1. i'd say install fedora first then ubuntu, but i don't know what bootloader fedora 12 uses. ubuntu 9.10 (karmic) uses grub2, which can easily be restored and personalized. remember to resize your windows partition in windows before installing the linux systems.
when your win7 upgrade arrives, you can just install it and then restore grub2.

2. i haven't really used win7, but the system partitions depend mostly on what you're going to install. i'd say that for the linux partitions most probably about 15gigs each would suffice, but again this depends on what you're installing. windows systems have much higher requirements for disk space. just remember to resize your windows partition from within windows first. if you want to use hibernation you want to add a swap partition of about the same size as your ram.

3. see 1.

How should I format the file storage partition? How do I resize my Windows partition?

---

### Post by Mark Phelps on 2010-01-02
> **Setarkos said:**
> How should I format the file storage partition? How do I resize my Windows partition?

If you want to share the file storage partition between MS Windows and Linux, format it as NTFS.

Resize your MS Windows partition using the builtin Vista Disk Management utility.  Do not use GParted or the Ubuntu installer to do that.

---

### Post by Setarkos on 2010-01-02
> **Mark Phelps said:**
> If you want to share the file storage partition between MS Windows and Linux, format it as NTFS.

Resize your MS Windows partition using the builtin Vista Disk Management utility.  Do not use GParted or the Ubuntu installer to do that.

So I do the following:
1. Resize Windows partition
2. Install Ubuntu and Fedora using their own partition tools
3. Format fourth partition form within Windows

Last question: With boot loader do I have to use? In which order should I install Fedora an Ubuntu? Is there a easy detailed How-To?

Thank you so far

Edit: Do I have to configure the swap partition somehow? Do I need one for every OS?

---

### Post by Setarkos on 2010-01-02
I found a guide [http://www.go2linux.org/triple-boot-windows-two-linux](http://www.go2linux.org/triple-boot-windows-two-linux) but this is not detailed enough and I am not sure if it equally applies to Vista, Karmic Koala and Constantine. Please help!

---

### Post by Leppie on 2010-01-02
> **Setarkos said:**
> I found a guide [http://www.go2linux.org/triple-boot-windows-two-linux](http://www.go2linux.org/triple-boot-windows-two-linux) but this is not detailed enough and I am not sure if it equally applies to Vista, Karmic Koala and Constantine. Please help!
well, vista you already have installed on your system. so, i would just advise to install fedora first and then karmic. but this is simply because i don't know what bootloader fedora uses.
you don't have to configure the swap and you can use 1 swap between 2 systems. you can't hibernate both fedora and ubuntu at the same time if using the same swap.

---

### Post by Setarkos on 2010-01-02
Would somebody be so kind to write a short step-by-step . I feel a little bit unsure about this. Sorry but I am a beginner...:(

---

### Post by LinuxRules1 on 2010-01-02
this is my suggestion.

Step 1: Install win7 first

Step 2: Take a ubuntu live cd, boot it

Step 3: Use gparted to resize the windows partition to about 25-30GB.

Step 4: use gparted to create 2 more partitions, 10-15GB for fedora and 10-15GB for ubuntu. 

Step 5: use gparted to use the remaining space on the drive for storage.

Step 6: install fedora

Step 7: install ubuntu

i hope this helps you.

---

### Post by Leppie on 2010-01-02
> **LinuxRules1 said:**
> Step 3: Use gparted to resize the windows partition to about 25-30GB.
use a windows application to resize the windows partition to avoid a broken system after resizing.

---

### Post by Setarkos on 2010-01-02
> **LinuxRules1 said:**
> this is my suggestion.

Step 1: Install win7 first

Step 2: Take a ubuntu live cd, boot it

Step 3: Use gparted to resize the windows partition to about 25-30GB.

Step 4: use gparted to create 2 more partitions, 10-15GB for fedora and 10-15GB for ubuntu. 

Step 5: use gparted to use the remaining space on the drive for storage.

Step 6: install fedora

Step 7: install ubuntu

i hope this helps you.

Okay so far so good (Not using GParted for Win-Partition). Now what about swap partition and boot loader? Will Ubuntu automatically recognise Windows AND Fedora and include them in grub?

---

### Post by LinuxRules1 on 2010-01-02
yes, ubuntu will recognize windows and fedora and put them in the boot loader automatically

---

### Post by Setarkos on 2010-01-02
> **LinuxRules1 said:**
> yes, ubuntu will recognize windows and fedora and put them in the boot loader automatically

Okay I think I got it:

1. Resize Windows within Vista
2. Use Ubuntu LiveCD to create partition
2.1. One partition each for Ubuntu and Fedora
2.2. One partition for file storage which will later be formatted via Windows
2.3. One swap partition the size of my RAM
3. Install Fedora
4. Install Ubuntu
5. Format File storage partition

After Win7 Upgrade:

6. Win7 Upgrade
7. If Grub gets lost recover via Ubuntu LiveCD

Is that alright? One last question: Will it work just as well with Mint 8?

---

### Post by LinuxRules1 on 2010-01-02
it might i don't know for sure.

you should do the win7 install after you create the partitions then install fedora and ubuntu.

---

### Post by Setarkos on 2010-01-02
> **LinuxRules1 said:**
> it might i don't know for sure.

you should do the win7 install after you create the partitions then install fedora and ubuntu.

I'm still wainting for my Win7 Upgrade and I would love to do most of the work tomorrow, since its sunday. It should work as I stated, too, shouldn't it?

---

### Post by LinuxRules1 on 2010-01-02
you can create the partitions now but you won't be able to load fedora or ubuntu until your windows disk comes. the reason is because when you try to load windows with linux windows deletes the linux partition because it's an unknown partition to it. so you can load fedora and ubuntu now but you will have to reload them again when you install windows 7.

---

### Post by Leppie on 2010-01-02
> **Setarkos said:**
> After Win7 Upgrade:

6. Win7 Upgrade
7. If Grub gets lost recover via Ubuntu LiveCD
this is no if, grub will be overwritten as windows systems are egocentric (they believe they're the onlys systems on a machine).

> **Setarkos said:**
> Is that alright? One last question: Will it work just as well with Mint 8?
yes, this should work with Mint as well as AFAIK it is based on Karmic.

---

### Post by Leppie on 2010-01-02
> **LinuxRules1 said:**
> you can create the partitions now but you won't be able to load fedora or ubuntu until your windows disk comes. the reason is because when you try to load windows with linux windows deletes the linux partition because it's an unknown partition to it. so you can load fedora and ubuntu now but you will have to reload them again when you install windows 7.
windows will not delete all partitions. this depends entirely on how you use the setup program. you can leave the partitions in tact and just install into the vista partition. and if this really is an upgrade, that is most probably what it will do automatically.

---

### Post by Setarkos on 2010-01-02
> **LinuxRules1 said:**
> you can create the partitions now but you won't be able to load fedora or ubuntu until your windows disk comes. the reason is because when you try to load windows with linux windows deletes the linux partition because it's an unknown partition to it. so you can load fedora and ubuntu now but you will have to reload them again when you install windows 7.


Okay, thanks for the advice. That sucks but good to know...

---

### Post by LinuxRules1 on 2010-01-02
No problem

---

