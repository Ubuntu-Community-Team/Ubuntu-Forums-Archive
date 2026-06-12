---
title: "Won't boot - Possible data corruption?"
date: 2010-09-09
forum: General Help
---

### Post by Kir_B on 2010-09-09
Hey All :eek:.
  
  I'm having an interesting issue with my computer right now. It has   Ubuntu lucid installed, which was upgraded from karmic shortly after it   became available and was up to date as of September 1.
  
  The issue is as follows:
  It will not boot the internal hard drive (250GB Seagate barracuda).  When I  select any of the kernels, it appears to be booting, but 6 Hours  later,  no joy. If I select any of the Kernels in recovery mode, it  does nothing, so again no joy.
  
  It will boot my 500GB removable  drive via USB (Samsung on the inside),  which  contains a backup of my lucid (cloned with Clonezilla) from  June-ish,  but will not do so if the internal hard drive is hooked up,  so I cannot  access the internals contents while using the backup USB  HD.
  
  Now this is where it get's interesting, at least for me. It will boot  up  a livecd while the internal HD is connected, which _was_ the  only way for  me to access the contents of my Ubuntu partitions in the  internal HD. I have since pulled  the Internal out, removed the USB  500GB HD from it's case, installed  it into the internal HD bay, hooked  up all the cables, turned the  computer on and it did boot. While it did  seem to take a long while to boot, I'm hoping this may be because it  needs a serious amount of updates (294 updates, 485MB  are ready via  synaptic!). So I now have placed the 250GB Seagate into  the USB HD case  and can now access it, but the only contents that can be seen, are the  items in my defunct vista partition and I cannot find any remnants of my  Ubuntu installation, despite gparted being able to see all of the  partitions.
  
 In my completely uneducated opinion, it appears that the internal HD is  either hooped, or I've got some serious data corruption in my Linux  extended partitions, but I would love to hear what you all can conclude  as to what may be happening. I'd really hate to lose all the alterations  I've made over the past months, along with god knows what else (I know,  I should have been backing up more often, but I got complacent), but  more important to me is what may be happening here, as I'm trying very  hard to understand all things Linux. I would really appreciate your  expert opinions on if and what options I may have.
  
  Please, if any of you can provide some incite, it would be  very much  appreciated. Thank you all in advance and sorry if this is a little   confusing, but that was as good as I could explain the the situation and  of course will  clarify and include additional details as needed.
  
  Thanks again everyone. Kirby ):P

---

### Post by baddnady23 on 2010-09-10
If you can't see it there, it seems to me as if there is a physical failure of the disk or the install doesn't actually exist...:confused:

When you upgraded, did you mess with the partition tables at all?

---

### Post by Kir_B on 2010-09-10
Thank you so much for the response.

I haven't messed around with any of the partition tables and everything was running fine until last week.

What's really strange, is that after it happened, I put in an Ultimate Edition livedvd to retrieve a few files that I urgently needed and was successful in retrieving them, but now I can't find any of them, even though I know they are there.

I hope I answered your question.

Thanks again. Kirby

---

### Post by lisati on 2010-09-10
Threads merged.

---

### Post by Kir_B on 2010-09-10
> **lisati said:**
> Threads merged.

Thanks a lot, and again, sorry to be a pain.

Kirby

---

### Post by teward on 2010-09-10
Interesting, I had a Seagate 250GB drive that wouldnt boot due to dead sectors. (on my laptop, not a barracuda drive but still a seagate)

You loaded from either your backup or a LiveUSB, and forced a complete fsck check for bad sectors and things?

---

### Post by QIII on 2010-09-10
Does your drive have the SD15 firmware version?  (You can check it on the label.)

---

### Post by Kir_B on 2010-09-10
> **TrekCaptainUSA said:**
> Interesting, I had a Seagate 250GB drive that wouldnt boot due to dead sectors. (on my laptop, not a barracuda drive but still a seagate)

You loaded from either your backup or a LiveUSB, and forced a complete fsck check for bad sectors and things?

Thanks for the response.

I was thinking of loading either the parted magic livecd or system rescue livecd to run some checks, but I thought it might be best to get some advice from you fine folks first. Being that my backup HD isn't recognizing the contents properly, I thought it would be best to use one of those livecd's for this purpose.

Thanks again. Kirby

---

### Post by Kir_B on 2010-09-10
> **QIII said:**
> Does your drive have the SD15 firmware version?  (You can check it on the label.)

Thanks for your response.

I've checked the HD's firmware and it says that it is; Firmware: 3.ADG.

Thanks again. Kirby

---

### Post by QIII on 2010-09-10
Ah, good.  SD15 causes drives to behave badly and ultimately become bricks suitable for use as door stops.

They can be unbricked (I've done it three times for people), but that takes to technical expertise and a purpose-built cable you have to assemble for yourself.

In any case, I'd try to recover what you can from the disk and then start checking for bad sectors as suggested above.

---

### Post by chaanakya_chiraag on 2010-09-10
I've had a similar problem where the boot hanged due to plymouth hanging (plymouth's the bootsplash).  I had to completely remove it.  To do so, boot up with a liveCD and open up a terminal **after mounting your internal hard drive**:
```
cd /mnt/<name of harddrive>/etc/init.d/
sudo mv plymouth plymouth.bak
sudo mv plymouth-log plymouth-log.bak
sudo mv plymouth-splash plymouth-splash.bak
sudo mv plymouth-stop plymouth-stop.bak

```
I think that should do it.  If it doesn't, please post back and we'll go from there.

---

### Post by perspectoff on 2010-09-10
You sure it has to do with the hard drive?

Graphics driver problems (as with Intel integrated graphics, as discussed all over these forums) give the same symptoms.

---

### Post by Kir_B on 2010-09-10
> **QIII said:**
> Ah, good.  SD15 causes drives to behave badly and ultimately become bricks suitable for use as door stops.

They can be unbricked (I've done it three times for people), but that takes to technical expertise and a purpose-built cable you have to assemble for yourself.

In any case, I'd try to recover what you can from the disk and then start checking for bad sectors as suggested above.

Thanks QIII, I'll probably be trying that, if necessary.

Thanks again. Kirby

---

### Post by Kir_B on 2010-09-10
> **chaanakya_chiraag said:**
> I've had a similar problem where the boot hanged due to plymouth hanging (plymouth's the bootsplash).  I had to completely remove it.  To do so, boot up with a liveCD and open up a terminal **after mounting your internal hard drive**:
```
cd /mnt/<name of harddrive>/etc/init.d/
sudo mv plymouth plymouth.bak
sudo mv plymouth-log plymouth-log.bak
sudo mv plymouth-splash plymouth-splash.bak
sudo mv plymouth-stop plymouth-stop.bak

```I think that should do it.  If it doesn't, please post back and we'll go from there.

Thanks for that advice. I wish that I'd known about that months ago, as the lines across the top of my screen were quite annoying and served absolutely no purpose, except perhaps to slow down the boot process.

THanks a lot. Kirby

---

### Post by Kir_B on 2010-09-10
> **perspectoff said:**
> You sure it has to do with the hard drive?

Graphics driver problems (as with Intel integrated graphics, as discussed all over these forums) give the same symptoms.

Thank you for your response.

I was beginning to suspect the same thing, but the fact that I can't access the contents of it while it's installed in the USB case had me thinking it was something much more serious. But then again, perhaps that has something to do with it not belonging in the USB case?. 

Thanks again. Kirby

---

### Post by chaanakya_chiraag on 2010-09-10
> **Kir_B said:**
> Thank you for your response.

I was beginning to suspect the same thing, but the fact that I can't access the contents of it while it's installed in the USB case had me thinking it was something much more serious. But then again, perhaps that has something to do with it not belonging in the USB case?. 

Thanks again. Kirby
By the way...graphics problems cause the plymouth lockup, which may be what you are experiencing - as perspectoff has mentioned.

---

### Post by Kir_B on 2010-09-10
> **chaanakya_chiraag said:**
> By the way...graphics problems cause the plymouth lockup, which may be what you are experiencing - as perspectoff has mentioned.

Thank you all for your kind responses.

I've reinstalled the hard drive and rebooted into a livecd environment. Once at the desktop, I checked the contents of the drive, and indeed everything is there, so that's one less worry.

Now if indeed it is a driver related problem, how would I go about fixing it, being that I can't get it to boot normally or through the recovery modes? Will the following commands do the trick (dev/sda6 being my OS, and not my home partition)?

```
cd /mnt/dev/sda6/etc/init.d/
sudo mv plymouth plymouth.bak
sudo mv plymouth-log plymouth-log.bak
sudo mv plymouth-splash plymouth-splash.bak
sudo mv plymouth-stop plymouth-stop.bak 
```
Thanks again guys. Your indeed some of the best examples that Humanity has to offer.

Kirby

---

### Post by Kir_B on 2010-09-10
O.K. The above commands result in "no such file or directory" output in the terminal.

Any ideas guys? Am I doing something wrong?

Thanks Kirby

---

### Post by chaanakya_chiraag on 2010-09-11
So the first command gave you errors...did you mount the hard drive first?  Since you know the device name, try mounting it directly with the following commands:
```
sudo mkdir /mnt/hdd
sudo mount /dev/hda6 /mnt/hdd
```Then modify the **first command** I gave you to read:
```
cd /mnt/hdd/etc/init.d
```
All other commands should work.
At the end, you should also run the following commands:
```
sudo update-rc.d plymouth remove
sudo update-rc.d plymouth-log remove
sudo update-rc.d plymouth-splash remove
sudo update-rc.d plymouth-stop remove
```

---

### Post by Kir_B on 2010-09-11
> **chaanakya_chiraag said:**
> So the first command gave you errors...did you mount the hard drive first?  Since you know the device name, try mounting it directly with the following commands:
```
sudo mkdir /mnt/hdd
sudo mount /dev/hda6 /mnt/hdd
```Then modify the **first command** I gave you to read:
```
cd /mnt/hdd/etc/init.d
```All other commands should work.
At the end, you should also run the following commands:
```
sudo update-rc.d plymouth remove
sudo update-rc.d plymouth-log remove
sudo update-rc.d plymouth-splash remove
sudo update-rc.d plymouth-stop remove
```

Thanks so much!

I knew I was missing something. I currently have my back up installed, so I'm going to re insert the other HD, boot into the live environment and give it a go. Might take me a little while, but I'll post back as soon as I know whether or not it worked.

Thanks again. Kirby

---

### Post by Kir_B on 2010-09-11
O.K. I'm on the way and I'm given this in my terminal readout:

[PHP]ubuntu@ubuntu:~$ sudo mkdir /mnt/hdd
ubuntu@ubuntu:~$ sudo mount /dev/hda6 /mnt/hdd
mount: special device /dev/hda6 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/hdd
ubuntu@ubuntu:~$ cd /mnt/hdd/etc/init.d
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo update-rc.d plymouth remove
update-rc.d: /etc/init.d/plymouth exists during rc.d purge (use -f to force)
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ 
[/PHP]Am I right that at this point I should issue the " -f " command and then proceed with the rest of the commands?

Just thought it might be wise to enquire before going ahead.

Thanks. Kirby

---

### Post by Kir_B on 2010-09-11
Thanks for all the help guys. I really thought that was going to do the trick, but it seems as though I've really stepped in it this time.

Here's what I did```

sudo mkdir /mnt/hdd
sudo mount /dev/sda6 /mnt/hdd
```Then this:
```
cd /mnt/hdd/etc/init.d
```Then these:
```
sudo mv plymouth plymouth.bak
sudo mv plymouth-log plymouth-log.bak
sudo mv plymouth-splash plymouth-splash.bak
sudo mv plymouth-stop plymouth-stop.bak
```Then these:
```
sudo update-rc.d -f plymouth remove
sudo update-rc.d -f plymouth-log remove
sudo update-rc.d -f plymouth-splash remove
sudo update-rc.d -f plymouth-stop remove
```The terminal made me put in the -f argument in the above set of commands in order to accomplish it.

Once everything was completed, I rebooted to what appears to be the exact situation as before! It appears to be booting up as it did before, with lines along the top of the screen, then never ever reaching the log in screen. Go figure.

I'm quite frustrated right now, so I'm done for the night and I'll check back in tomorrow. I hope by then, you guys will have some ideas for me to try. I look forward to hearing from you all. Hope you all have a good night, as I'm going to, as I drink wine until I can't anymore.

Thanks again for all your efforts. Kirby

---

### Post by chaanakya_chiraag on 2010-09-13
Wait...in order for the update-rc.d commands to work, you have to chroot into the hard disk.  If you can't figure out how to do it, ask here and we'll help you accomplish it.

---

### Post by Kir_B on 2010-09-13
> **chaanakya_chiraag said:**
> Wait...in order for the update-rc.d commands to work, you have to chroot into the hard disk.  If you can't figure out how to do it, ask here and we'll help you accomplish it.

Thanks for all the help so far chaanakya_chiraag.

That's funny that you say that (chroot), as we were reading over the instructions given to me by "lmarmisa" way, way back, when I had an unfortunate incident with grub2 (see my signature). That happened so long ago, that I'd forgotten all about the procedure. We (my cousin and I) may be able to figure it out ourselves, which may be necessary, as getting answers on this forum seems to have become a little difficult lately (I'm guessing that we have a rather large group of newbies right now).

Thanks again. Kirby

---

### Post by Kir_B on 2010-09-13
Okay. I've reworked the commands, as you can now see below. As soon as I can get someone to take a look at them and give me a thumbs up, I'll go ahead and give it another go.

One question I have right away? Should my first command be "sudo bash", as that is what I was told to do when I reinstalled grub2 from a livecd?

```
sudo mkdir /mnt/hdd
sudo mount /dev/sda6 /mnt/hdd
```Then this:
```
chroot /mnt
```Then this:
```
cd /mnt/hdd/etc/init.d
```Then these:
```
sudo mv plymouth plymouth.bak
sudo mv plymouth-log plymouth-log.bak
sudo mv plymouth-splash plymouth-splash.bak
sudo mv plymouth-stop plymouth-stop.bak
```Then these:
```
sudo update-rc.d -f plymouth remove
sudo update-rc.d -f plymouth-log remove
sudo update-rc.d -f plymouth-splash remove
sudo update-rc.d -f plymouth-stop remove
```Another question. In the last set of commands, do I need the "-f" argument, or...?

Thanks again. Kirby

---

### Post by chaanakya_chiraag on 2010-09-14
> **Kir_B said:**
> Okay. I've reworked the commands, as you can now see below. As soon as I can get someone to take a look at them and give me a thumbs up, I'll go ahead and give it another go.

One question I have right away? Should my first command be "sudo bash", as that is what I was told to do when I reinstalled grub2 from a livecd?

```
sudo mkdir /mnt/hdd
sudo mount /dev/sda6 /mnt/hdd
```Then this:
```
chroot /mnt
```Then this:
```
cd /mnt/hdd/etc/init.d
```Then these:
```
sudo mv plymouth plymouth.bak
sudo mv plymouth-log plymouth-log.bak
sudo mv plymouth-splash plymouth-splash.bak
sudo mv plymouth-stop plymouth-stop.bak
```Then these:
```
sudo update-rc.d -f plymouth remove
sudo update-rc.d -f plymouth-log remove
sudo update-rc.d -f plymouth-splash remove
sudo update-rc.d -f plymouth-stop remove
```Another question. In the last set of commands, do I need the "-f" argument, or...?

Thanks again. Kirby
You should ```
sudo chroot /mnt/hdd
``` and ```
cd /etc/init.d
``` instead of what you have there.

---

### Post by Kir_B on 2010-09-14
> **chaanakya_chiraag said:**
> You should ```
sudo chroot /mnt/hdd
``` and ```
cd /etc/init.d
``` instead of what you have there.

Awesome. Thank you.

So, I take it there is no need to start with "sudo bash"?

This should do it then:
```
sudo mkdir /mnt/hdd
sudo mount /dev/sda6 /mnt/hdd
```Then this:
```
sudo chroot /mnt/hdd
```Then this:
```
cd /etc/init.d
```Then these:
```
sudo mv plymouth plymouth.bak
sudo mv plymouth-log plymouth-log.bak
sudo mv plymouth-splash plymouth-splash.bak
sudo mv plymouth-stop plymouth-stop.bak
```Then these:
```
sudo update-rc.d -f plymouth remove
sudo update-rc.d -f plymouth-log remove
sudo update-rc.d -f plymouth-splash remove
sudo update-rc.d -f plymouth-stop remove
```I'll get to it, just as soon as my brain is ready (just woke up ;)).
Thank you very, very much. Kirby ):P

---

### Post by chaanakya_chiraag on 2010-09-16
And you shouldn't need the -f in the last set of commands.  Otherwise, that should work :)

---

### Post by chaanakya_chiraag on 2010-09-16
But again, we still don't know if Plymouth is the problem...however, it's always worth a try.  Plus, you should get faster startup times!!  Be warned, however, that you *might not* get interactive prompts during the boot process (if, for example, fsck found an error).  Therefore, it might seem like the boot has hung...I'm not sure as to the state of this "bug", as there have numerous mountall updates which may have fixed the problem...

---

### Post by chaanakya_chiraag on 2010-09-16
Also, just as a tip, you can add the ```
console=tty2
``` at the **GRUB configuration** to supress all boot messages.  I did this because there are a lot of messages...

---

### Post by Kir_B on 2010-09-16
> **chaanakya_chiraag said:**
> But again, we still don't know if Plymouth is the problem...however, it's always worth a try.  Plus, you should get faster startup times!!  Be warned, however, that you *might not* get interactive prompts during the boot process (if, for example, fsck found an error).  Therefore, it might seem like the boot has hung...I'm not sure as to the state of this "bug", as there have numerous mountall updates which may have fixed the problem...

Thanks again.

I ran those commands from a lucid 10.4.1 livecd. Everything went well, with no errors, but I then rebooted into the HD and had the exact same result (dots and lines across the top of the screen and it never gets to the login screen.).

I can't see running them again without the -f option making any difference, but then again, I really don't entirely know exactly what I'm doing all of the time, so please correct me if I'm wrong.

Thank you. Kirby

---

### Post by Kir_B on 2010-09-16
> **chaanakya_chiraag said:**
> Also, just as a tip, you can add the ```
console=tty2
``` at the **GRUB configuration** to supress all boot messages.  I did this because there are a lot of messages...

Are you talking about just appending _**console=tty2**_ to the boot command (press "e" at the grub screen), or are we talking about something else entirely?

As it has been for some time, I don't see any messages during the boot process.

Thanks again. Kirby

---

### Post by Kir_B on 2010-09-16
Another quick question.

Is there a command I can issue at the grub screen via command line, to bring the system up to date, which may include a mountall fix?

Thanks again. Kirby

---

### Post by chaanakya_chiraag on 2010-09-17
> **Kir_B said:**
> Are you talking about just appending _**console=tty2**_ to the boot command (press "e" at the grub screen), or are we talking about something else entirely?

As it has been for some time, I don't see any messages during the boot process.

Thanks again. Kirby
Yes, that is what I mean

---

### Post by chaanakya_chiraag on 2010-09-17
> **Kir_B said:**
> Another quick question.

Is there a command I can issue at the grub screen via command line, to bring the system up to date, which may include a mountall fix?

Thanks again. Kirby
I don't think so. :(

---

### Post by chaanakya_chiraag on 2010-09-17
I just realized you have to remove the ```
splash
```parameter from the GRUB boot command in order to actually feel the effects of the change.

---

### Post by Kir_B on 2010-09-20
Sorry I've taken so long  to respond, but I needed a break after experiencing more "no joy"!!!

The commands went off without a hitch, but no joy on reboot.

Tried removing "splash" from the boot command and again no joy!

Tried removing "splash" and adding "console=tty2" to the boot command and again no joy!

Tried removing "splash" and adding nomodeset to the boot command and once again no joy!

Also tried a few other combination's to the boot command with no results (ex. removing quiet and splash), so I went back to the drawing board, or more accurately, to the forums for some more reading. I've seen a few more things. One thing that interests me, is to upgrade the system from a livecd, so I'm currently looking for a good howto on this. If anyone has a favorite method, please, don't hesitate to post it, or a link to it here.

Thanks & good day. Kirby

---

