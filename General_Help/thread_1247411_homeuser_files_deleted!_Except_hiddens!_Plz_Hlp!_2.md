---
title: "/home/user/ files deleted! Except hiddens! Plz Hlp! 2nd Time"
date: 2009-08-22
forum: General Help
---

### Post by tylenol187 on 2009-08-22
Hello!  Okay, so a few days ago I was browsing the internet and downloading torrents and all the sudden ktorrent told me that the files i was downloading had disappeared.  So I went to check my /home/user/downloads folder with the shortcut that's on my desktop, but it told me the folder didn't exist!      Well, turns out everything in my /home/user/ directory disappeared! Everything except all the .hidden files and .folders!  Needless to say I was VERY frustrated! But after searching google for an answer and finding next to nothing, I gave up and figured i needed to make backups more often.      Well, about 2 hours ago I was sitting here browsing the internet and downloading again and the SAME THING HAPPENED!  All the files in my /home/user directory are GONE! Except the hidden files and folders with the '.' in front of them.  I'm am freaking out because I have NO idea how this could've happened.  I've searched my logs for any mention of /home/* and there's nothing at all.  I've searched for 'rm' commands in my logs, but there wasn't ANY!  I've checked my bashrc for anything unusual, and couldn't find anything!  I've done a search for some of the files that went missing, but I can't find them!  This is so ridiculous!       Can anyone here please help me?  I'm at my wits end and I can't figure out what the hell is doing this.  Any advice and help would be much appreciated, thanks in advance!  Using Jaunty 9.04 with Gnome and Kubuntu desktop package.

---

### Post by michy99 on 2009-08-22
Open a terminal and enter```
ls -a
``` and post the output here.

---

### Post by transmition on 2009-08-22
Maybe give us an output for 
```

top

```

as well. You may have a malicious script running :/

---

### Post by tylenol187 on 2009-08-22
Thanks for quick responses!   OK, 'ls -a' just lists all the hidden files and files i've created since the deletion, but it doesn't list any of the things that ended up missing.  here's the output of 'top'  maybe you guys will see something i dont?   I've also just installed a program called 'recover' to attempt to recover my files, and i did an 'inode dump' (?) to a folder, but the files it produced just look like garbage to me, theres only two of them.

---

### Post by tylenol187 on 2009-08-22
here's the output for "ls -a" just incase you wanted to see it anyways.  but As far as i can tell, it doesn't show any of the files that got erased.  the ones without the "." in front of them are folders/files that i have created SINCE the distaster...

---

### Post by michy99 on 2009-08-23
I see folders for Documents, Videos, Music, Pictures, etc. Are you files in those folders by any chance?

---

### Post by drs305 on 2009-08-23
If you know the name of a file that has gone missing, try to find it on your computer with the following command. If it moved to another location this command should find it:
```

sudo find / -type f -iname <yourfilename>

```
Example: 
sudo find / -type f -iname test.txt

---

### Post by tylenol187 on 2009-08-23
> **michy99 said:**
> I see folders for Documents, Videos, Music, Pictures, etc. Are you files in those folders by any chance?

 Thanks, but no. Like I said the files in my /home/user directory are either hidden files that did not get deleted, or files I have since created.  Is it a bad idea for me to create files in the same directory? Will that lessen my chances of recovering the lost data?  > **drs305 said:**
> If you know the name of a file that has gone missing, try to find it on your computer with the following command. If it moved to another location this command should find it: Code:  sudo find / -type f -iname   Example: sudo find / -type f -iname test.txt

I've tried 'sudo find / -name myfile.jpg -print' but nothing shows up.  I also tried it your way, 'sudo find / -type f -iname foobar.jpg' but...nothing. 
A little thing I just noticed.  I went to open synaptic and it gave me an error about my user .xAuthorization file.  Well, it turns out my .xAuthorization file is gone, too! So this is the first .hidden file I've noticed missing.  Not sure what this means. I'll try restarting x and see if it creates a new one.  Thanks again for the responses!  UPDATE: Restarting X11 did indeed give me a new ".Xauthority" so thats good.  I can now run synaptic.

---

### Post by tylenol187 on 2009-08-24
ok, im bumping this thread because i need to get this fixed otherwise its just going to happen again ( i assume ).  can anyone please help me with this?  I can give you more information if you need?  Is there any chance that a X11 program could've caused this from a crash or something?  I've been having KTorrent crash on me sometimes.  But i didn't think it could cause something like THIS... please help guys!

---

### Post by ankspo71 on 2009-08-24
Hi tylenol187,

Before I made the move to Linux, I used Utorrent in windows XP, and I had similar trouble downloading large torrents, like Linux ISO's. It was either data loss or locked files, but it was more in system directories. I found out later that using full file allocation can cause this data corruption in rare instances, (for me it was when I was running very high cpu usuage), and disabling the allocation seem to help me. I don't know if you could be having a similar problem in linux though. I'm not familiar with Ktorrent either, but see if you can disable file allocating, or maybe even make a switch to Deluge or Transmission if you need to.

---

### Post by mike555 on 2009-08-24
Do you have WINE installed , if so maybe it got a virus and is messing with the only files it can (the ones in your /home folder & the files in your .wine folder )..... just a thought.

 read;   [http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

---

### Post by tylenol187 on 2009-08-26
> **mike555 said:**
> Do you have WINE installed , if so maybe it got a virus and is messing with the only files it can (the ones in your /home folder & the files in your .wine folder )..... just a thought.  read; [http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598) 
Yes, I do have WINE installed.  However, I don't think this is the problem because all my WINE programs are still intact and working perfectly.  Plus, it would be highly unlikely that I've got a Windows virus because the only programs I've installed with WINE are 3 PC games that I own.  My .wine folder is perfectly fine, nothing missing there, but thanks for the reply!  Any other ideas? 

> **ankspo71 said:**
> Hi tylenol187,  Before I made the move to Linux, I used Utorrent in windows XP, and I had similar trouble downloading large torrents, like Linux ISO's. It was either data loss or locked files, but it was more in system directories. I found out later that using full file allocation can cause this data corruption in rare instances, (for me it was when I was running very high cpu usuage), and disabling the allocation seem to help me. I don't know if you could be having a similar problem in linux though. I'm not familiar with Ktorrent either, but see if you can disable file allocating, or maybe even make a switch to Deluge or Transmission if you need to. 
I think you may be right about this... I did have 'reserve disk space' in Ktorrent turned on, and I was downloading several very large torrents, and was somewhat low on disk space (~10GB).  I'm thinking maybe one night while I was sleeping, Ktorrent was running and maybe it filled up the disk and just started to overwrite stuph, or maybe it just decided to clear the folder because the space ran out?  I don't know this for fact, I never saw the disk space go below 5 GB while I was downloading, but I'm saying maybe it happened while I wasn't paying attention or something and it erased the files, so the disk space would've cleared back up and I wouldn't have known that it was so low?  
One weird thing about this theory is, I download my torrents to my '/home/user/Downloads/' directory, but it was (almost) everything in the parent folder (/home/user/) that got deleted.  Why would Ktorrent go up a folder?  Anyways, I've taken your advice and turned off 'reserve disk space before starting torrent' just incase that's my problem (which I tend to think it is, but I'm not sure).  Note that while 'reserve disk space' was enabled, 'fully reserve disk space' was NOT enabled.  Also, I tried using Deluge, because I heard it was similar to uTorrent and I love uTorrent.  However, Deluge kept crashing on me ALL the time, and when it crashed it would leave processes running that were a bitch to kill, so I gave up on Deluge.  Ktorrent still crashes sometimes, but not nearly as much.  If this problem persists, my next step is to uninstall Ktorrent, and then Firefox, because those were the only two programs I was using at the times of both disasters.  Anyways, thanks for all the help guys.  Hopefully this WON'T happen again, but if it does I'll post back here.

---

