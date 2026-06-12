---
title: "unreadable files from windows after installation."
date: 2010-09-19
forum: General Help
---

### Post by danielswan18 on 2010-09-19
just about three days ago, our school introduced this OS called UBUNTU..

i actually liked it.. very much...

They gave me an installation disk named Ubuntu 10.04 LTS Desktop Edition. So I asked somebody to install it for me. But there were some problems before he could even completely finish the installation. He had to pee.

So I was the one ordered to complete the installation.
There were 3 choices on the 3rd or 4th step of the installation process. By hit-and-miss, I choose the second one.

The process went on safe and sound. It was alright for me to loose windows 7 loader but not the files and programs inside it.

After the installation was done, I then started to explore.
Then I found the problem.




PROBLEM:
    
   I cant find my old files from windows 7. The whole disk was occupied by Ubuntu. 

My friend told me that Ubuntu will only occupy about 4G of the Disk only.My disk has a capacity of 250G. 

So if that's the case, then it should have left a free space of 246G.
But when I took a check on my disk's availability, it showed that there is 210G of Memory Left.

I was then wondering if that big memory are my old files from windows 7.

Another thing is that those files are unreadable. I cant even see those files even if i "show hidden files".

Can they still be recovered or not?

I really need your suggestions and proposed solutions before I choose to reformat my whole drive.

Thank You so much in advance guys.
May the force of Freedom and Sharing be with us all... ^_^

---

### Post by nothingspecial on 2010-09-20
I`ve got a horrible feeling you may have over written windows completely.

In your menu go Accessories > Terminal

And type this

```
sudo fdisk -l
```

Copy and paste what it says in a new reply here.

---

### Post by Mark Phelps on 2010-09-20
> **danielswan18 said:**
> ... But when I took a check on my disk's availability, it showed that there is 210G of Memory Left.
It's not "memory"; it's "disk space".

> Can they still be recovered or not? I really need your suggestions and proposed solutions before I choose to reformat my whole drive...

Not easily.

Looks like your "installer" person chose the option to use the full disk -- which effectively overwrote your entire drive and erased ALL the Win7 stuff.

The first thing you should know is that every time you use this drive now, you worsen the chance of recovering ANYTHING.

The second thing you should know is that it's nearly impossible now to restore the drive to the state it was in before your stupid "installer" person chose the wrong option and overwrote your filesystem.

However, you might be able to recover your data files from the old Win7 install such that you can restore them after you restore Win7.

In order to restore Win7, though, you will need one of the following:
1) Complete Win7 Installation DVD medium
2) Vendor-provided Restore CD -- WITH the existence of a Recovery partition still on your hard drive.

You probably do NOT have the first, especially if your machine came with Win7 preinstalled.

And, there's every possibility that the idiot "installer" person wiped your Recovery partition during the Ubuntu installation.

If you do the "fdisk" command as suggested (that's a lowercase L, not a one), it will tell us what partitions are still present on your drive.  IF the Recovery partition is still there (unlikely), and you either (1) have a Restore CD that came with the machine, or (2) have a Function key you can press to restore the machine, then you have the MEANS to restore your original Win7 setup.

However, doing that will completely wipe your drive and all the data on it.

So, before you do that, you would want to recover whatever data files are important to you.

Others here will tell you to use Testdisk and/or Photorec (in Ubuntu) to do that.  I've had very poor results with both of those when trying to recovery MS Windows partitions.

My best results have been using GetDataBack from Runtime Software.  The free downloadable version has to be installed in a PC in a drive OTHER THAN the one you want to recover. Why? Because you can't restore a drive to itself (Note: This is ALSO true of the Linuc recovery apps). The free version won't actually recover anything -- but it will show you want it CAN recovery. You will have to purchase it to do the actual recovery.

Yeah, I know spending money infuriates folks in this forum, but I know this software works, and the more you mess around with Linux utilities, the more you lower your chances of recovering ANYTHING from your drive.

Good Luck -- and next time, don't let any of those "idiots" install ANYTHING for you.

---

