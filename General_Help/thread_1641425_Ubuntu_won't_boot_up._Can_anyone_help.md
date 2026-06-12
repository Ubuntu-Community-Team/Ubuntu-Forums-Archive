---
title: "Ubuntu won't boot up. Can anyone help?"
date: 2010-12-09
forum: General Help
---

### Post by TehGoose on 2010-12-09
I was wondering if there is a way to fix my Ubuntu installation without overwriting everything that is currently there. I have it all backed up, it's just I had planned on working today and the stuff takes at least 7 hours to install.

The problem is that Ubuntu won't boot up. I get to Grub menu, select what I want, it looks like it is about to start and then I get this screen:

[Whole screen]("http://i.imgur.com/gA7zX.jpg")

[(The bottom was a bit blurry)]("http://i.imgur.com/krc2Q.jpg")

This happens no matter which of the 6 Ubuntu options I choose, that is including the 3 recovery modes. I am running Ubuntu 10.10 and it is fully updated. This is the first restart since the last updates.

I noticed that Ubuntu was running really slow for some reason, so I rebooted, and then this happened.

I would appreciate any help or information on this. Thanks in advance.

---

### Post by kainalu on 2010-12-09
How slow? For how long? High disk activity before crashing?

---

### Post by sikander3786 on 2010-12-09
Hopefully, you can do without a re-install here.

We need to see the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

You need to boot an Ubuntu Live CD/USB to run that.

While posting click the # icon from post menu and paste your text in between the generated code tags.

---

### Post by TehGoose on 2010-12-09
> **kainalu said:**
> How slow? For how long? High disk activity before crashing?

I'd say about half the speed it usually goes, and it was only the last time I turned it on. Before that it was all working normally.

---

### Post by TehGoose on 2010-12-09
> **sikander3786 said:**
> Hopefully, you can do without a re-install here.

We need to see the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

You need to boot an Ubuntu Live CD/USB to run that.

While posting click the # icon from post menu and paste your text in between the generated code tags.

I am booting into Ubuntu LiveCD now. Thanks :)

---

### Post by TehGoose on 2010-12-09
> **sikander3786 said:**
> Hopefully, you can do without a re-install here.

We need to see the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

You need to boot an Ubuntu Live CD/USB to run that.

While posting click the # icon from post menu and paste your text in between the generated code tags.

About how long does this usually take because it has been stuck on sda3 for about 15 mins now.

---

### Post by wilee-nilee on 2010-12-09
> **TehGoose said:**
> About how long does this usually take because it has been stuck on sda3 for about 15 mins now.

The script should run in abut 5-10 seconds at most,

---

### Post by sikander3786 on 2010-12-09
> **TehGoose said:**
> About how long does this usually take because it has been stuck on sda3 for about 15 mins now.
That doesn't sound good at all.

It normally completes in about 10-20 secs.

I have a feel as if your HDD is not in good health. Check it for bad sectors. You can use the manufacturer's tools or Disk Utility under System > Administration menu or Gparted or any other software.

---

### Post by TehGoose on 2010-12-09
> **sikander3786 said:**
> That doesn't sound good at all.

It normally completes in about 10-20 secs.

I have a feel as if your HDD is not in good health. Check it for bad sectors. You can use the manufacturer's tools or Disk Utility under System > Administration menu or Gparted or any other software.

I just ran the test on my HDD. It has 72 bad sectors. I don't know if that is a lot or not, or even if it is recoverable. Is there anyway to repair it, and do you know if this means my HDD is permanently damaged?

---

### Post by sikander3786 on 2010-12-09
> **TehGoose said:**
> I just ran the test on my HDD. It has 72 bad sectors. I don't know if that is a lot or not, or even if it is recoverable. Is there anyway to repair it, and do you know if this means my HDD is permanently damaged?
Backup your important data. Thats what is most important here.

Recoverable, well I don't think so. You can mark those sectors bad in an OS so the OS doesn't try to read/write to those sectors. How? That needs a separate thread. I don't know much there.

And even if you mark those sectors bad, at every re-install of the OS, you'll need to do that again.

As I said, my knowledge is limited on that. A thread with "Bad sectors" title would definitely gain attention of experienced users.

Good Luck!

---

### Post by happymellon on 2010-12-09
> **TehGoose said:**
> I just ran the test on my HDD. It has 72 bad sectors. I don't know if that is a lot or not, or even if it is recoverable. Is there anyway to repair it, and do you know if this means my HDD is permanently damaged?

How old is this disk? 72 sounds like a lot of bad sectors, my advice is to STOP. 
I assume you have successfully booted from a USB drive based on being able to run scans. If you have to use that computer, use that until you can get that disk replaced. Bad sectors can multiply quickly, especially the more you use the disk, and although I don't know what important data you have and where it is, the chances of recovery diminish the more sectors fail.

---

### Post by TehGoose on 2010-12-09
> **happymellon said:**
> How old is this disk? 72 sounds like a lot of bad sectors, my advice is to STOP. 
I assume you have successfully booted from a USB drive based on being able to run scans. If you have to use that computer, use that until you can get that disk replaced. Bad sectors can multiply quickly, especially the more you use the disk, and although I don't know what important data you have and where it is, the chances of recovery diminish the more sectors fail.

This laptop is exactly a year old this month. I am now really disappointed with ACER. My friend got almost the same model at the same time and his battery is completely dead now. Great...

Thanks for the help you guys.
I'm going to have to get a new HDD.

---

### Post by kainalu on 2010-12-09
Hard drives are very sensitive to shock and vibration, now more than ever, due to expanding capacities. I think it sounds like a dead HDD. Send it in under warranty, or try to replace the drive. Its actually quite easy for the most part.

If you are tech minded, try to find and boot a tool called "spinrite". it will fully diag a disk. Look for lots of ECC errors, I find that they multiply rapidlty with a dying HDD.

---

### Post by soltanis on 2010-12-10
Replace the disk; 72 bad sectors means the drive is not far from failure.

---

