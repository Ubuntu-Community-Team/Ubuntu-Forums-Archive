---
title: "Error 18 - Selected cylinder exceeds maximum supported by BIOS"
date: 2009-08-12
forum: General Help
---

### Post by db666 on 2009-08-12
Hello All, 

I wonder if anyone would be able to give me some help on Error 18 that I am receiving. 

the other day i was using Open office, went to click the top left menu(file i think) and the my machine hung. caps lock perm on, hdd light perm on, just totally froze. - I hard resetted the machine.

Machine booted up fine and i used it without a problem until i switched off that night.

I switched it on this morning to find that it got stuck booting up and presented me with a couple of errors;

```


"Error 16"

"Error 18: selected cylinder exceeds maximum supported by BIOS"

Press return and I have a choice of 7 options;
Ubuntu 9.04, kernel 2.6.28-14-generic & recovery mode
Ubuntu 9.04, kernel 2.6.28-13-generic & recovery mode
Ubuntu 9.04, kernel 2.6.28-11-generic & recovery mode
Ubuntu 9.04, memtest86+

```All of these when selected produce the above error 18 message - obviously except the memtest which is running as i type.

Looking around the net i cant seem to pin point where the problem might be.. it's a bit cryptic and new to me so i'm struggling to know where to start.

**Current setup**
1 drive with my ubuntu install and a second drive(which i've now unplugged after this problem) which had my data on/ old vista install

BIOS is set to load m main drive only although does mention Boot up cards but the priority is set to my main ubuntu drive

No recent upgrades/changes that I can think of.. my machines a shuttle so not a lot of room for.. modifying! 

Version 9.04 of ubuntu cant be anymore specific unless you can suggest a way of seeing it from looking at the installed hdd in another ubuntu live session.

So far.. i've:

```

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: clean, 184497/4702208 files, 6315304/18786001 blocks

``````

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
  184497 inodes used (3.92%)
    1010 non-contiguous files (0.5%)
     141 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 10457/513/0
 6315304 blocks used (33.62%)
       0 bad blocks
       2 large files

  140838 regular files
   23602 directories
      69 character device files
      26 block device files
       6 fifos
    2833 links
   19910 symbolic links (17736 fast symbolic links)
      37 sockets
--------
  187321 files
ubuntu@ubuntu:~$ 
```Have also just tried.. 

```

sudo grub
find /boot/grub/stage1
(it will print out both /boot locations--hd0,2 and hd1,0--use the newer in the next command)
root (hd1,0) -->i.e. sdb1
setup (hd0) --> this reinstalls it to MBR of sda/hd0
quit

```I"m a little bit confused by all this as my background is solely Windows (am I allowed to say that word?) but was looking to leave that behind which i had been quite successfully until this little problem occured a week or two ago

TIA
DB

---

### Post by dcstar on 2009-08-13
> **db666 said:**
> Hello All, 

I wonder if anyone would be able to give me some help on Error 18 that I am receiving. 

the other day i was using Open office, went to click the top left menu(file i think) and the my machine hung. caps lock perm on, hdd light perm on, just totally froze. - I hard resetted the machine.

Machine booted up fine and i used it without a problem until i switched off that night.

I switched it on this morning to find that it got stuck booting up and presented me with a couple of errors;

[code]

"Error 16"

"Error 18: selected cylinder exceeds maximum supported by BIOS"
.......

At a guess it may be a hardware error has reset/corrupted the BIOS settings on your PC.

---

### Post by db666 on 2009-08-13
THanks for the reply

I'll try and reset my BIOS back to defaults (assuming that is what you're suggesting?) however the machine appears to detect the HDD fine, and you can see it attempting to boot the Ubuntu install so my assumption was that it was past the BIOS stage.

---

### Post by Roasted on 2009-08-13
What kind of errors do you get? Do you bounce between error 16, error 18, and error 21, with error 18 being the most common?

What motherboard do you have?

I ran into this issue recently... turns out I had a bad SATA cable.

What's even more weird is that I run an Ubuntu computer at work for imaging services with FOG (linux based open source windows imaging program). I have 2 hard drives in that computer, 1 main and 1 for backing my images to. I started to have problems with my backup drive in this computer at work about a month after I fixed my problem at home with a new SATA cable.

Turns out the bad SATA cable that I had at home was of the same brand that went bad in the Ubuntu machine at work.

Give it a shot. I spent about a month beating myself up and badmouthing ASUS thinking my ASUS motherboard was bad. Give it a shot and see how things go. If things continue to drive you nuts, well, then we'll have to track it down. At least you can say you gave it a try!

---

### Post by db666 on 2009-08-13
> **Roasted said:**
> What kind of errors do you get? Do you bounce between error 16, error 18, and error 21, with error 18 being the most common?

What motherboard do you have?

I ran into this issue recently... turns out I had a bad SATA cable.

What's even more weird is that I run an Ubuntu computer at work for imaging services with FOG (linux based open source windows imaging program). I have 2 hard drives in that computer, 1 main and 1 for backing my images to. I started to have problems with my backup drive in this computer at work about a month after I fixed my problem at home with a new SATA cable.

Turns out the bad SATA cable that I had at home was of the same brand that went bad in the Ubuntu machine at work.

Give it a shot. I spent about a month beating myself up and badmouthing ASUS thinking my ASUS motherboard was bad. Give it a shot and see how things go. If things continue to drive you nuts, well, then we'll have to track it down. At least you can say you gave it a try!

I normally get error 16 first, then follows with error 18. then consistantly 18 until I change a bios setting or attempt to fix the problem with the things i've mentioned above.

I have a[ Shuttle SB62G2]("http://www.dansdata.com/2xpcs.htm") which is getting a bit old now I must admit but i was hoping to ahve one last ditch attempt with it!

While i was attempting to boot my machine again after resetting all the bios settings (then changing it to enahnced mode so the hdd would be selected to boot) the machine went through the usual errror above so i attempted to boot from the CD again.. this time though i came back to the screen to see;

[[IMG]http://img40.imageshack.us/img40/4726/img00009b.th.jpg[/IMG]](http://img40.imageshack.us/i/img00009b.jpg/)

I left this going for some time.. 1130 i think or more - i hard powered off again and removed my hdd cables (which is sata) and simply left the bare cd (ide) ram, cpu and psu etc plugged in. and I continue to get the same error.

I assume its curtains for my machine by the way its slowly seems to be going down hill? 

Tia
DB

---

### Post by Roasted on 2009-08-13
I don't understand something, though. Those errors are in relation to being unable to find a selectable boot partition to launch the operating system. Why would you remove the HDD cables? I can understand letting the "bare system" run if you were trying to troubleshoot something at a lower level that would maybe effect powering on or something of that nature, but these "Error 16/18/etc" are in relation to boot issues, so removing the HDD cables (based on what little I know) doesn't seem to be a viable idea for troubleshooting.

Do you have other SATA cables that you could try, just to say you did it? After all, it's something so simple. I just hate to see you go through the prolonged headaches I had when it was a cable all along.

Not saying that IS what it is.
I'd just rather see you say "I tried it, didn't work" even if it doesn't solve it.

---

### Post by db666 on 2009-08-13
Well, the fault appeared while the hdd was plugged in. Knowing nothing about Ubuntu errors i took an assumption that it might be a hdd fault as the system was struggling to boot.  

I figured to rule out any possibility of the hard drive being at fault or the sata bus etc by removing the hdd first. 

I'll grab another cable in a minute and try that shortly.....

tia

---

### Post by db666 on 2009-08-13
Well...

I removed the sata cable and replaced with another in port 1 and it booted straight away...

I then tried the other port with the new cable in port 0.... it worked fine

I then tried the old cable in port 1 it worked fine.. and finally tried port 0 in the original port... all fine

So its back to all as it was... errr....?? :|

---

### Post by Roasted on 2009-08-13
Keep running with the new cable. Throw the other cable on the shelf for now.

It took me about 3 days of rebooting before I felt confident that it solved my problems. It's been 2 months and my system hasn't had a faulty boot ever since I replaced that SATA cable.

Keep in mind, in my situation, my old SATA cable (the problematic one) would work intermittently. There were times it would boot fine 15 times in a row. Then it'd seem like it was having a bad day and require me to reboot upwards of 8 or 9 times to get it to finally boot without error.

With the new SATA cable plugged in, run for a few days. But post a reply asap if you get the same errors with the new cable, because at that point we may be looking at something considerably different than a simple cable failure.

---

### Post by db666 on 2009-08-13
thanks. will do  - I was surprised that no one had posted about this error before too.

---

### Post by Roasted on 2009-08-13
The red flag to me was when I googled for a long time and ultimately found a post dating WAYYY back. Somebody was asking about Error 18. This was on REALLY old computers, though, where the error was more common. This had something to do with dual booting with Windows first... something about the boot partition being AFTER Windows... if it was too far away from the front of the hard drive it would error out and barf out Error 18. Some of the older Ubuntu folk who ran Linux on really old computers seemed to be aware of it, but someone told me that was back in the days where an 8 gigabyte drive was hot stuff. I'm a 23 year old guy - I was probably learning to walk back then. :lolflag:

I told somebody on a forum the specs of my computer and they said it made zero sense how I was getting those errors on a system as new as mine. I was clueless, and someone on a hardware tech forum just kept saying change the cable. I finally did and he was right.

I'm not saying this WILL fix your problem. But like I mentioned before, I'd rather hear you say it didn't work (but we tried) as opposed to seeing this post bump up a month from now with you saying oh my gosh it's working it was just a cable!

Know what I mean? Post back here though regardless - I'm curious to see what the scoop was.

EDIT - A link to my post here when I ran into these issues.

[http://ubuntuforums.org/showthread.php?t=1182131](http://ubuntuforums.org/showthread.php?t=1182131)

---

### Post by db666 on 2009-08-17
thanks, 

I'm away until the end of the month now so I cannot test the machine. I still have my old cable plugged in so I will test with that until I have problem and then use the other cable.

I still think there is hardware issue(motherboard) as I#ve been having strange problems like this and problems with Windows etc.

I will update once I have some news

regards
DB

---

### Post by db666 on 2009-09-06
I've been back a week or so but still using my problematic cable(as I still wasn't convinced) and managed to inherit what looks like graphics card problems!

I had a number of issues getting the machine on, and when it did boot into the BIOS the screen was corrupt and generally unreadable. Removed graphics card and used on board problems went away.

At the same time i also replaced SATA cable to the new one and have disposed of the old one now.

Having some problems playing films now but other than that it's been working since yesterday afternoon

Also I found it really hard to search for this thread, I searched for error 18 in the search box up the top and found no references to my thread... had to do a search for threads by me to find it?? 

regards
DB

---

