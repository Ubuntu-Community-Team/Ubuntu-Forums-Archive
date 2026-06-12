---
title: "Just need an answer about installing a HD in 9.04"
date: 2010-01-20
forum: General Help
---

### Post by fagan on 2010-01-20
I know that there is 1,000,000 of you guys that could help. Please take the time to help a brother out.

---

### Post by lotharmat on 2010-01-20
You are going to need to be a little more specific in your question.

The easy answer is plug it in and let ubuntu detect it.

What kind of HD is it?

USB (external)
IDE
SATA
??

Throw us a freakin' bone :D

BTW - Double posting is considered bad etiquette [1st post]("http://ubuntuforums.org/showthread.php?t=1385853")

---

### Post by fagan on 2010-01-20
it is an IDE 80G that I am trying to install. I have tried using GParted and Ubuntu did not just plug n play. 
p.s. sorry bout the 2nd post. New here.

---

### Post by lotharmat on 2010-01-20
When you load gparted, click on the drop down arrow on the right at the top (see picture). You should see two drives in there.

If you do; post the results of 

```
fdisk -l
```

(lowercase L not a One)

---

### Post by fagan on 2010-01-20
> **lotharmat said:**
> When you load gparted, click on the drop down arrow on the right at the top (see picture). You should see two drives in there.

If you do; post the results of 

```
fdisk -l
```

(lowercase L not a One)

I am using my laptop to write in this forum and my pc is the computer having the issues. Could I just give you my number I'm so new at this it's embarressing!!! Do I need to type all that I see in fdisk? or can I copy and paste from the terminal and how do I do it?

---

### Post by fagan on 2010-01-20
fdisk is showing that I have 2 drives. Also they are both present on the right hand list in gparted.  The 80G drive that I am trying to install is listed as Disk /dev/sdb  Does this help?

---

### Post by fagan on 2010-01-20
Is their more information that I can give you?

---

### Post by fagan on 2010-01-20
You tell me that posting twice is bad etiquette but then you leave and don't say goodbye. Is that bad etiquette?

---

### Post by lotharmat on 2010-01-20
I'm actually at work!

You need to be more patient - no-one here gets paid for their support..

I'd suggest the following google search

mount second hard drive ubuntu

There are countless tutorials - No point in me re-inventing the wheel!

---

### Post by amsterdamharu on 2010-01-20
Is the hard disk formatted? If so you can just open the file browser (nautilus) click on computer and click on the hard disk/partition you want to see.

If it's not formatted then format it using gparted or something but make sure you format the right hard disk.

---

