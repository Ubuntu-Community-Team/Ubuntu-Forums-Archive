---
title: "Complete system backup/custom install?"
date: 2011-12-16
forum: General Help
---

### Post by opethfan89 on 2011-12-16
Hi all,

I've just spent a few hours tweaking and customizing my Ubuntu 10.10 install to my liking.  Is there any way I can save all my settings and not have to do this every time I wipe out?  By this, I mean is it possible to somehow create a custom install with all of the tweaks and adjustments I've made, or even a partition image of some sorts that lets me re-install Ubuntu and have it be exactly as I left it?

I have zero knowledge of kernel customization or anything like that, and limited programming knowledge, but I am open to suggestions and learning new things.

Thanks,
Opethfan89

---

### Post by Mark Phelps on 2011-12-16
Best tool I've used for imaging and restoring Linux filesystems is Clonezilla.  You can image off the whole drive, or individual partitions.

---

### Post by Megaptera on 2011-12-16
I like Rematersys 'cos it gives me a DVD that I can use, so there you have two choices.

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Actively being developed as mentioned here: [http://ubuntuforums.org/showthread.php?t=1870607&highlight=remastersys](http://ubuntuforums.org/showthread.php?t=1870607&highlight=remastersys) 'cos it was dormant at one stage I believe.

---

### Post by opethfan89 on 2011-12-17
Thank you for the responses.  I think I like remastersys, and I will give it a try in the upcoming days.  Would be amazing to have a completely custom Ubuntu install tailored specifically for each computer I'm using.  Thanks again :)

---

### Post by Megaptera on 2011-12-17
You're welcome!

---

### Post by pretty_whistle on 2011-12-17
> **Mark Phelps said:**
> Best tool I've used for imaging and restoring Linux filesystems is Clonezilla.  You can image off the whole drive, or individual partitions.
I second Clonezilla.  

I make disk images with it.  It's great.  Should anything go wrong I'm able to restore the computer in less than 20 minutes.

Wouldn't go without it. :)

---

### Post by opethfan89 on 2011-12-19
I found a fantastic step-by-step tutorial with screenshots explaining how to use/install Remastersys.  This is just in case someone else searches and finds this thread.

Tutorial [here]("http://www.dedoimedo.com/computers/remastersys.html")

---

### Post by opethfan89 on 2011-12-20
Well, I finally found time to actually use remastersys, and it works great. The "backup" option did not work for me because it said the filesystem was too large for iso9660 standards, but that's probably because it is including my 13gb music folder.

I tried the "dist" option, which creates a "custom" distribution, and it works somewhat, but it does not save all my options.  That is, it saves all the stuff I have installed in the application menu, etc, but I was hoping to have a fully custom version install with ALL the goodies right off the bat, i.e. have it look like it did when I wiped out as soon as I install it.  I made a folder in the main menu called "customizations" and had saved all the program launchers in there, for ease of organization, but for some reason remastersys did not include this and instead left the launchers in their original categories.

Any ideas or suggestions to help me along?

---

### Post by Megaptera on 2011-12-20
I think the limit is 4gb so if you excluded your music folder & backed that up eslsewhere you probably be OK.
With the 'dist' I think some personal stuff is automatically excluded to make sure your personal stuff doesn't form part of the 'dist' copy.

I'd try exluding the music and trying the backup option again.

---

### Post by opethfan89 on 2011-12-30
> **Megaptera said:**
> I think the limit is 4gb so if you excluded your music folder & backed that up eslsewhere you probably be OK.
With the 'dist' I think some personal stuff is automatically excluded to make sure your personal stuff doesn't form part of the 'dist' copy.

I'd try exluding the music and trying the backup option again.

I actually did exactly that: Excluding the 'music' folder the 2nd time I tried, and I got the same result.

Along the same lines as trying to use remastersys, what would be the steps required if someone wants to make a custom distribution based on Ubuntu?  I mean, there are people out there who saw Ubuntu, saw it lacked something they wanted, then they built their own customization to redistribute. I want to do the same thing, but just build it to my own standards and have it packaged in such a way as to be able to burn/redistribute it.  Is such an endeavor possible?

---

### Post by Megaptera on 2011-12-30
I'm not sure why you got that result twice ... anyone know?

As to part two - I can't help with that, I just use Remastersys to get my DVD backups .. sorry.

---

