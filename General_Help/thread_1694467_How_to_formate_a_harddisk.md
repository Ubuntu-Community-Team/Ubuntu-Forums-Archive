---
title: "How to formate a harddisk?"
date: 2011-02-24
forum: General Help
---

### Post by hooz on 2011-02-24
Hi, i'm a beginner in computer, but need to formate my harddrive to install ubuntu?
I cant use the cd to formate it, but is there a commando line i can write ?

---

### Post by wiggly81 on 2011-02-24
download gparted from software center or by typing in terminal 
```
sudo apt-get install gparted
```
there is a good gui for editing hard drives adding deleting formating etc...

---

### Post by hooz on 2011-02-24
i'll try that now

---

### Post by hooz on 2011-02-24
it won't format :(

---

### Post by wiggly81 on 2011-02-24
if the drive is mounted you will need to unmount it first

---

### Post by hooz on 2011-02-24
cd drives to ?

---

### Post by wiggly81 on 2011-02-24
you only need to unmount the hard drive you wish to format, make sure the correct hard drive is selected in gparted top right there is a drop down box (only matters if u have more than 1 hard drive in use) then you should be able to unmount and format

---

### Post by seawolf167 on 2011-02-24
If you are going to partition it as NTFS, make sure you also get 

```
sudo apt-get install ntfsprogs
```

the drive needs to be unmounted before you can format it

---

### Post by srs5694 on 2011-02-24
> **hooz said:**
> Hi, i'm a beginner in computer, but need to formate my harddrive to install ubuntu?
I cant use the cd to formate it, but is there a commando line i can write ?

> it won't format :sad:

Please be more precise. The Ubuntu installation CDs/DVDs most emphatically *can* create partitions and create filesystems in those partitions. (Newbies usually use the term "format" to refer to one or both of these actions, but they're different things.) If you're having problems doing these things, we really have no clue what's going on if you just say "it won't format." We need to know precisely what actions you're taking and what, if any, error messages you're seeing. Posting a screen shot or cutting-and-pasting text mode output (between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags) can be very helpful. It's also likely to be helpful, and perhaps necessary, for us to know the current state of the hard disk. That is, is it a brand-new blank disk, or does it have existing partition(s), OS installation(s), or other types of data on it? Do you intend to install Ubuntu alone, or have it dual-boot with Windows or some other OS? Are you using a commodity PC or something more specialized, like a Mac?

---

### Post by hooz on 2011-02-24
My computer is an Acer Aspire 5738ZG originally with Vista (but upgraded it to windows 7).
Then I installed Ubuntu 10.10 and used the whole harddisk. Now my original Ubuntu won't start so I run "Try Ubuntu". I have tried to install it again, but the instalation progress stops. Now i want to "formate" the computer but I don't know how. If there's anything you need of information to help me just ask.

---

