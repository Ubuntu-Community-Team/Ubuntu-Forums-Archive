---
title: "remove physical volume label"
date: 2011-09-10
forum: General Help
---

### Post by subin-p on 2011-09-10
Hai..
         I hav a duel booting system. my hard disk partition format is NTFS.I want to remove the physical volume label from hard disk.for Ex. "500 GB Hard Disk: Films" .I want to make it only Films..
its very sad that in Ubuntu I can't rename it directly as in windows..........

Subin-p:(

---

### Post by jacksaff on 2011-09-10
You want the program e2label.
Type 'man e2label' into a terminal to see how it works.

---

### Post by raja.genupula on 2011-09-10
have you tried in disk utility ?

---

### Post by subin-p on 2011-09-10
I had downloaded e2fsprogs-1.41.14.tar.gz....But  don't know how to instal it ,am a beginner in ubuntu

---

### Post by coffeecat on 2011-09-10
> **subin-p said:**
> I had downloaded e2fsprogs-1.41.14.tar.gz....But  don't know how to instal it ,am a beginner in ubuntu

You already have e2fsprogs installed, so you can discard that downloaded tar.gz file.

However, e2fsprogs (e2label is part of e2fsprogs) will not help you because the partition you are wanting to relabel is an NTFS one. You need ntfslabel (which is part of ntfsprogs) which is also already installed. Open a terminal, and type:

```
man ntfslabel
```

... to get instructions on how to use it.

But why not do what raja.genupula suggests? Use Disk Utility. It's already installed, it's a GUI app and it's easy to use.

By the way, a piece of advice. Don't bother with downloading tar.gz and tar.bz2 packages from the internet. These are source code and for advanced users. >95% of what you need you will find pre-compiled in the Ubuntu Software Centre and easily installed with a couple of mouse clicks.

---

### Post by haqking on 2011-09-10
> **coffeecat said:**
> 
But why not do what raja.genupula suggests? Use Disk Utility. It's already installed, it's a GUI app and it's easy to use.

.


Edit: original post shouldnt of been run as root as i suggested.

---

### Post by sisco311 on 2011-09-10
> **haqking said:**
> This should work but needs to be run as root.

gksudo** palimpsest**

thought i would add that as the command to launch it is obscure

palimpsest uses policy kit, so you don't have to (and shouldn't) run it as root. When an action needs root privileges you are prompted for a password.

---

### Post by coffeecat on 2011-09-10
> **haqking said:**
> This should work but needs to be run as root.

gksudo** palimpsest**

thought i would add that as the command to launch it is obscure

Are you sure? Tbh, I don't use Disk Utility much (preferring Gparted) but I've just tried it in Natty, running it as an ordinary user. When I told it to relabel a partition, it prompted me for my password - and promptly relabelled the partition!

You might want to try that in Maverick and report back. :wink:

**EDIT**: sisco311 beat me to it! You have to be quick round here. :)

---

### Post by haqking on 2011-09-10
> **sisco311 said:**
> palimpsest uses policy kit, so you don't have to (and shouldn't) run it as root. When an action needs root privileges you are prompted for a password.


oh right.

how do you run disk utility with the change label option ?

sorry about that, i did it a few days ago for same thing and took me ages to find out

---

### Post by haqking on 2011-09-10
> **coffeecat said:**
> Are you sure? Tbh, I don't use Disk Utility much (preferring Gparted) but I've just tried it in Natty, running it as an ordinary user. When I told it to relabel a partition, it prompted me for my password - and promptly relabelled the partition!

You might want to try that in Maverick and report back. :wink:

**EDIT**: sisco311 beat me to it! You have to be quick round here. :)


it does but not for NTFS, on mine anyways

---

### Post by coffeecat on 2011-09-10
> **haqking said:**
> it does but not for NTFS, on mine anyways

It works for me on NTFS partitions in Natty. Check that you've got ntfsprogs installed. It *should* come with a default installation but may have gone awol.

---

### Post by haqking on 2011-09-10
> **coffeecat said:**
> It works for me on NTFS partitions in Natty. Check that you've got ntfsprogs installed. It *should* come with a default installation but may have gone awol.


yeah i already checked that.

mmm i will look into this further because i had to use the above as root to do it a few days back.

cheers for the info and apologies for bad advice above ;-)

---

### Post by subin-p on 2011-09-11
My ntfs configuration tool is not opening...????
I had tried sudo ntfslabel /dev/sda6 Films...But it does not removes the physical volume label...
please help

---

### Post by coffeecat on 2011-09-11
@subin-p, I think I can see what the problem is now...

> **subin-p said:**
>  "500 GB Hard Disk: Films" .

Is that what you are seeing when you open "Computer"? The "500GB Hard Disk" is not part of the partition label; just "Films" is, so your partition label is already "Films". The system is simply telling you that you have a 500GB hard drive with a partition labelled Films.

If you open a file browser window and look in the left (Places) pane, what does it say for "Films"?

Also - which release of Ubuntu are you using, 10.04, 10.10 or 11.04?

> **subin-p said:**
> My ntfs configuration tool is not opening...????
I had tried sudo ntfslabel /dev/sda6 Films...But it does not removes the physical volume label...
please help

If the ntfs partition you are trying to relabel is sda6, then your command is correct. However, it sounds as though you don't need to run it. See above.

Open a terminal and run this command:

```
sudo blkid
```

Paste the output. If you highlight the output with the mouse, right-click and "copy", you can paste the output into your post without retyping it.

---

### Post by subin-p on 2011-09-12
I think you guys are misunderstood.....I just want to remove "500GB HARD DISK" from the label.......
am using UBUNTU 10.10, If there is any option for that please tell...

---

### Post by coffeecat on 2011-09-12
@subin-p, you didn't answer my question whether what you are seeing is when you open "Computer" from the Places, but I'll asssume that is what you are talking about. So that there is no misunderstanding, please have a look at the screenshot attached to this post. I don't have access to a 10.10 installation, so the screenshot is from 10.04, but this shows very much the same.

This is from my laptop with a 320GB hard drive. It has a number of partitions apart from the one on which 10.04 is installed. The labels are: "Vista", "Data", "Empty-7", "Empty-9" and "Oneiric". You can see them listed in the left pane. But if you look in the main pane you will see over each hard drive icon, this:

```
320 GB Hard Disk:
     Data
```

And so on for each partition. What you will be seeing is:

```
500 GB Hard Disk:
    Films
```

But if you look in the left pane, you will see that your Films partition is listed simply as "Films". In your case "Films" is the partition label. The "500 GB Hard Disk" is the system telling you that you have a 500GB Hard Disk, not that the partition label is "500 GB Hard Disk".

You can change a partition label as previously described but I know no way of getting the system not to show the "500 GB Hard Disk". It's trying to be helpful! :wink:

Is this what you are seeing on your system? If it is not and I have misunderstood you, then post a screenshot.

---

### Post by subin-p on 2011-09-12
yaahh ..wat am asking is,there is any option to remove "500 GB Hard Disk:"??.. and display just Films like in windows......
:oops:  :oops:

---

### Post by coffeecat on 2011-09-12
> **subin-p said:**
> yaahh ..wat am asking is,there is any option to remove "500 GB Hard Disk:"??.. and display just Films like in windows......
:oops:  :oops:

> **coffeecat said:**
> I know no way of getting the system not to show the "500 GB Hard Disk". It's trying to be helpful! :wink:

:)

---

### Post by sisco311 on 2011-09-12
Related BUG report: [lpbug]388904[/lpbug]

It has been marked as NOTABUG by the nautilus team, 
but its triaged on Ubuntu so you might see this fixed in Oneiric+1.

---

### Post by subin-p on 2011-09-13
please inform me when this problem is finished...........
pls tell where i can find Oneiric+1..?

---

### Post by nothingspecial on 2011-09-13
Oneiric is the new version of Ubuntu being released in a few weeks.

It is not recommended that you install it while it is still in beta unless you want to test it and don't mind possible occasional breakages.

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview)

---

### Post by sisco311 on 2011-09-13
Actually, Oneiric+1 is the next release which will be released around 2012.04

@OP: Subscribe to the BUG report.

And, from the [CoC]("http://ubuntuforums.org/index.php?page=policy"):
*Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.*

---

