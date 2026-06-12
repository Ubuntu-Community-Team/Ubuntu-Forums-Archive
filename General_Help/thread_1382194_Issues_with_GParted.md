---
title: "Issues with GParted"
date: 2010-01-15
forum: General Help
---

### Post by henryblowery on 2010-01-15
Hey ya'll I just installed a dual boot of ubuntu with XP on my laptop. I'm planning on deleting XP altogether and keeping ubuntu. Now, as I understand the best way to do this is to go to GParted, delete the ntfs partition, and format it to ext3. Does this sound right?

Now the problem is I can't seem to get GParted installed. I go to the terminal window and type 

sudo apt-get install gparted 

but it doesn't work. I get the following messege.

Reading package lists... Done
Building dependency tree
Reading state information.. Done
E: Couldn't find package gparted

Any ideas? Thanks in advance!

Gray

---

### Post by Cheesemill on 2010-01-15
Have you done:
```
sudo apt-get update
```
first?

---

### Post by henryblowery on 2010-01-15
Good call! Now lets hope my instructions for deleting XP are valid.

Gray

---

### Post by agrh on 2010-01-15
A simpler way to install might be this:

1. Press Alt-F2 to open the run dialog
2. Type in "apt:gparted" (without the quotes)

You should then be prompted for your password, confirm changes, etc.

---

### Post by Cheesemill on 2010-01-15
Rather than formatting the free space as ext3 you could just expand your current Ubuntu partition to take up the free space.

---

### Post by kiddykoff on 2010-01-15
> **Cheesemill said:**
> Have you done:
```
sudo apt-get update
```
first?

That is a good idea. I like to use a [gparted live cd]("http://gparted.sourceforge.net/livecd.php").

EDIT: forgot to add that you'll need to use this if you want to expand a mounted filesystem

---

### Post by warfacegod on 2010-01-15
Gparted is also available in Synaptic.

---

### Post by henryblowery on 2010-01-15
Ok, so I got GParted on my computer now, but it wont let me delete the ntfs partition. I select it and right click on it but I'm unable to click the delete button. Any thoughts?

Gray

---

### Post by audiomick on 2010-01-15
can you post a screen shot of gparted?

---

### Post by ajcham on 2010-01-15
> Ok, so I got GParted on my computer now, but it wont let me delete the ntfs partition. I select it and right click on it but I'm unable to click the delete button. Any thoughts?

You need to unmount the partition before you can alter it in Gparted.

Go to System » Administration » Disk Utility

Then select the NTFS partition and click the Unmount icon on the toolbar.

---

### Post by warfacegod on 2010-01-15
> **ajcham said:**
> You need to unmount the partition before you can alter it in Gparted.

Go to System » Administration » Disk Utility

Then select the NTFS partition and click the Unmount icon on the toolbar.

Partitions can be unmounted within Gparted. Right click the partition or drive, select unmount.

---

### Post by henryblowery on 2010-01-15
I'm working on getting that screen shot....I've taken it, now I'm trying to get my laptop online so I can post it here. Now that I look at it I have two partitions. One is Really small and the other is about 15 gigs. Before I installed ubuntu this morning the HD had 9 gigs on it. It's looking like it installed Ubuntu in the same partition as XP, so I can't unmount it or delete anything :( 

Screen shot coming...I hope.

Gray

---

### Post by henryblowery on 2010-01-15
Just got hooked up to the internet. As you can see, I only have a few GB of space left so I desperately need to get rid of XP haha

Gray

---

### Post by warfacegod on 2010-01-15
In the top right corner where it says dev/sda, are there any other drives in that menu?

---

### Post by Sisyphus48 on 2010-01-15
Good luck to you.  I tried to use Gparted to do something similar but after two weeks of trying 50 different suggestions, none of which worked (people have actually tried the things they suggest, don't they) I finally just reinstalled 9.04 so I could use the whole disk!  Using Gparted with a live CD didn't do squat!:P

---

### Post by warfacegod on 2010-01-15
> **Sisyphus48 said:**
> Good luck to you.  I tried to use Gparted to do something similar but after two weeks of trying 50 different suggestions, none of which worked (people have actually tried the things they suggest, don't they) I finally just reinstalled 9.04 so I could use the whole disk!  Using Gparted with a live CD didn't do squat!:P

Let's not be so negative. Gparted is a very reliable app whether in an installed or Live environment. I have never had a problem with it that wasn't due to my own foolishness.

---

### Post by Cheesemill on 2010-01-15
I see what the problem is.

Did you install using Wubi by any chance instead of a normal dual boot?
If so then your Ubuntu installation isn't on its own partition, it's on a file inside the NTFS partition.

If this is the case then you can't get rid of Windows without getting rid of Ubuntu as well, you'll have to do a clean install to get just Ubuntu on the machine.

---

### Post by henryblowery on 2010-01-15
Well hopefully I'll be able to work something out. I just want to get rid of XP and use Ubuntu as my operating system. I don't care what I have to do to accomplish it.

I clicked on the button you were referring to, but nothing happened so I don't think I have anything there

Gray

---

### Post by henryblowery on 2010-01-15
Ok, I think you're right Cheesemill. How do I go about doing the clean install. Just put the disk in and tell it to reboot right then? Will the lack of space on my HD pose a problem?

Gray

---

### Post by warfacegod on 2010-01-15
I think your best option would be to install ubuntu again (don't worry, it doesn't take that long) and select "Use entire disk" when the partitioner loads and wants to know how to partition your hard drive. That will automatically rid you of Windows, format the HDD to ext4, and free up allot of drive space. Make sure you go into Windows and backup anything important to you. Pictures, music, etc. before you do the install. If you don't then any thing you wanted will be erased and extremely difficult to recover.

---

### Post by audiomick on 2010-01-15
What cheesemill said, particularly the bit about backing up first.;)

---

### Post by warfacegod on 2010-01-15
> **audiomick said:**
> What cheesemill said, particularly the bit about backing up first.;)

That was me!!!!!!:(:(:(


:D:D:D:D

---

### Post by Cheesemill on 2010-01-15
Haha, I get credit for everything !!

---

### Post by audiomick on 2010-01-15
> **warfacegod said:**
> That was me!!!!!!:(:(:(


:D:D:D:D

oops, sorry. It's one o'clock in the morning here, and half past two beers...:oops:

---

### Post by henryblowery on 2010-01-15
Thanks y'all! I'm working on reinstalling it right now.

Gray

---

### Post by warfacegod on 2010-01-15
> **Cheesemill said:**
> Haha, I get credit for everything !!

Curses, foiled again.

---

### Post by Sisyphus48 on 2010-01-15
How come cheesemill and warfacegod are getting the credit??  I told you to do a clean install before either of them.  And I'm not being negative warfacegod, just telling like it is!:lolflag::lolflag:

---

### Post by henryblowery on 2010-01-15
Thanks again y'all. I just got done with my install and am using the laptop. Now I've got over 15 gigs on the HD :) It's a lot better than two.

Gray

---

### Post by warfacegod on 2010-01-15
> **Sisyphus48 said:**
> How come cheesemill and warfacegod are getting the credit??  I told you to do a clean install before either of them.  And I'm not being negative warfacegod, just telling like it is!:lolflag::lolflag:

I always get the credit!

---

### Post by warfacegod on 2010-01-15
> **henryblowery said:**
> Thanks again y'all. I just got done with my install and am using the laptop. Now I've got over 15 gigs on the HD :) It's a lot better than two.

Gray

I'm glad to hear your happy with your results. I suggest investing in either an internal or external drive, 15 GB can fill up very quickly.

---

### Post by henryblowery on 2010-01-16
Yeah, I may end up getting a new drive, but I'm not really using this computer for anything other than getting used to Linux, and figuring out how to use it to host a website. It's just an old laptop I had lying around the house so I figured I could start my education on it. Once I get the webhosting thing figured out, I'll get a decent computer do do it with.

Gray

---

