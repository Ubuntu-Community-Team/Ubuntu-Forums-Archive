---
title: "Help troubleshooting a non-starting system"
date: 2012-09-01
forum: General Help
---

### Post by Glum_Reaper on 2012-09-01
Hi all

I wonder if someone can give me some tips please? I'm running Xubuntu 12.04 (64-bit). It was fine until a few days ago, when I decided to install updates (it'd been a couple of weeks since I last did). Everything worked that session, but on reboot now the system won't start.

It goes through boot-up normally, and I get the login screen as usual. However when I enter my password, it flicks to a black screen then back to the login. On the second attempt the login box disappears, leaving the blue default background picture, and just freezes like that. :confused:

I've tried booting to recovery mode. From that menu I've tried to run fsck and package cleanup. They don't seem to work though, they prompt me that it's about to mount / as RW, then I get a line of text telling me /dev/sda5 is clean, listing files/blocks. Then it hangs there. I tried leaving both processes for 30 minutes to an hour, but they never got anywhere.

Now my first instinct is to slap the CD back in and re-install. But I'd like to actually learn how to troubleshoot linux better. I can generally fix 'doze when it falls over, but I'm pretty much lost in linux. I think this is an opportunity to address that!

Thanks, in advance.

Glum

---

### Post by steeldriver on 2012-09-01
Can you log in normally at one of the virtual terminals (Ctrl-Alt-F1 thru F6)? If so it's only your X session that's broken. We can take it from there.

---

### Post by Glum_Reaper on 2012-09-01
Thanks for your suggestion.

I tried switching, and found I could log in on VT1. Seems to be working, so just the X session that's broken as you say.

I did get an error message after logging in. About ten seconds after, not in response to anything I'd done, a few lines of text popped up. They all started with a number in square brackets (e.g.: *[51.808038]*) then "*ata6.00*". The first line was:
*exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6*
Then:
*failed command: READ DMA*
then two lines staring *'cmd'* and *'res'*, with long strings of hexadecimal digit pairs
Then:
*status: { DRDY }*
And finally:
*SRST failed (errno=-16)*

I'm going to hit google to try and find out what these mean.

---

### Post by steeldriver on 2012-09-01
What's your graphics hardware?

You could try killing lightdm and then starting your (user) X session from VT1

```
sudo service lightdm stop
startxfce4
```If it works, that would point to a lightdm session auth / startup issue - if it doesn't, then at least there should be some errors we can work with

You can also check the very basic stuff e.g. that your auth file(s) didn't get screwed up,

```
ls -l ~/.{ICE,X}authority
```(should both be owned  by user:user and mode 600)

---

### Post by dragonfly41 on 2012-09-01
I was about to post another thread when I read this thread.

I'm trying to troubleshoot a drive (/dev/sda  250 GB) which is giving me many READ DMA errors and I have to say that it points to a failing drive (in my case). I've removed it from my laptop so that I can work on it in slave mode (in a USB enclosure) to recover files using testdisk .. then ditch it.

here is a sample of my error ..

```

ata 3.00: failed command: READ DMA
ata 3.00: cmd c8/00:08:00:00:00/00:00:00:00:00:e0 tag 0 dma 4096
res 51/40:08:00:00:00/00:00:00:00/e0 Emask 0x9 (media error)
ata 3.00: status: {DRDY ERR}
ata 3:00 error: {UNC}

```I have the same problem of trying to force into desktop from a tty console.  So I'll try the commands suggested by steeldriver above to force start an x session.

---

### Post by Glum_Reaper on 2012-09-01
I think you're onto something with the ~/.ICEauthority file.

I tried the method you suggested of stopping lightdm, then restarting X. The error that came back was:

*xfce4-session: Unable to access file (~)/.ICEauthority: InputOutput error*

I ran *ls -l* on it, and got:

*-rw------- 1 (my username) (my username) 0 Aug 28 21:02*

I'm sorry but I don't know what you mean by mode 600. I'm guessing the ls command is giving the owner when it shows my username twice?

I've googled a bit about the iceauthority file. I can find descriptions of what it's for, but not necessarily how to fix it if it breaks!

Dragonfly - drive errors suck! I wondered if that's what I've got, given the DMA errors. I'm hoping not though, the drive operates fine booted to the windows partition. I've run fsck and it's not come back with any errors.
I'll run a full diagnostic on it just to make sure.

---

### Post by steeldriver on 2012-09-01
Actually more likely dragonfly41 is on to something with his observation about the disk error - if your disk (or more specifically your home partition) is unwriteable either because it's full or because the disk is failing, then you won't be able to start an X session

 *InputOutput error* is also likely an indication of bad [B]hardware

At this point I would suggest you [/B]**boot into a live CD session and back up any critical data**

---

### Post by dragonfly41 on 2012-09-01
I second the suggestion that you assume your hard drive is failing ..

My own setup is as follows ..

Internal failing /dev/sda drive has now been removed for data recovery.

With disk removed I can still boot my laptop to use a USB version of ubuntu on a USB drive (use F12 at bootup to enable USB boot).   This can be created using clonezilla.

I started using testdisk to recover files from failed drive.  Have been partially successful.   Then USB drive became too full (0 bytes left) and I could not get into desktop session.
I solved that by reading another thread which suggested [COLOR=Blue]sudo startx[/COLOR] command.  Then I can start clearing data.

When I've got back to a reasonable stable state I hope to resume using testdisk to recover remaining files from the slave drive.

The moral is to act swiftly when you see "bad sectors"  or READ DMA errors.  I left it too late.

---

### Post by Glum_Reaper on 2012-09-01
Thanks guys.

Thankfully there's no valuable data on that drive, it's purely OS and installed programs. I just thought this might be an opportunity to learn some troubleshooting steps - which I have, a bit. :)

I'll run some tests on the disk. All the data's already elsewhere and backed up.

Thanks for your help.

---

### Post by Glum_Reaper on 2012-09-09
Hey all,

Just by way of an update. I can't find any signs of imminent disk failure. I usually try and be cautious, and I've increased my backup regime. If this disk failed it wouldn't be disastrous.

I've run fsck on this filesystem, from this OS at shutdown, and from a liveCD. I've also scanned the windows partitions, and found no errors. I ran the manufacturer's disk diagnostic (seatools), and again found no problems.

All I did in the end was rename the .ICEauthority file. It created a new one and everything seems to be working now. I've not had any more problems in Xubuntu, and nothing is noticeably changed or missing.

Fingers crossed it was just one corrupted file, and it'll keep running smoothly! :)

Thanks

Glum

---

