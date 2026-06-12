---
title: "Ubuntu vs WHS2011 Media Server"
date: 2012-02-17
forum: General Help
---

### Post by just_cruising on 2012-02-17
I'm after some advice, I am building a Media Server. I don't want a  NAS. I have all the equipment ready to go but don't know what OS to use.

I have been looking at WHS 2011 and Ubuntu 11.10 Desktop edition. The  reason I have selected desktop is I want a GUI and I will also be  streaming media via XBMC and PS3 Media Server, additionally it the server will be connected  to a TV via HDMI running at 1980x1020.
 

I have 5TB of data currently, movies / music that are on NTFS  formatted drives. If I were to go to Linux would I need to format these  to ext file system or do I just install NTFS package? 
What backup solutions is there for Linux compared to the WHS2011 backup solution they have?
What OS is better for RAID1 as I will be requiring redundancy / mirroring, I like the look of MDAM?
 

I really don't mind getting my hands dirty so to speak with learning.
 

Please provide as many suggestions as you can.

---

### Post by Grenage on 2012-02-17
> **just_cruising said:**
> I'm after some advice, I am building a Media Server. I don't want a  NAS. I have all the equipment ready to go but don't know what OS to use.

If you're after hassle-free operation, whichever you are most comfortable with.

> **just_cruising said:**
> I have been looking at WHS 2011 and Ubuntu 11.10 Desktop edition. The  reason I have selected desktop is I want a GUI and I will also be  streaming media via XBMC and PS3 Media Server, additionally it the server will be connected  to a TV via HDMI running at 1980x1020.

If you're talking about a 'dumb' file server that's connected to a TV for desktop use, then you could use just about anything; Ubuntu should work fine, as should (I have never used) WHS.
 
> **just_cruising said:**
> I have 5TB of data currently, movies / music that are on NTFS formatted drives. If I were to go to Linux would I need to format these  to ext file system or do I just install NTFS package? 

NTFS tools are included in most distributions, and certainly in Ubuntu.  To enable remote access to files, you would need to configure Samba shared, which isn't that hard.  You can do basic sharing via the GUI.

> **just_cruising said:**
> What backup solutions is there for Linux compared to the WHS2011 backup solution they have?
What OS is better for RAID1 as I will be requiring redundancy / mirroring, I like the look of MDAM?

There are various solutions, but for that volume of data I would probably just get some extra drives and periodically duplicate new data onto them.  I assume that due to the nature of the beast, you're merely adding, rather than changing existing files.

As for MDAM, it works well; it's obviously not as simple as most on-board 'fakeraid' solutions.

---

### Post by just_cruising on 2012-02-17
> **Grenage said:**
> If you're talking about a 'dumb' file server that's connected to a TV for desktop use, then you could use just about anything; Ubuntu should work fine, as should (I have never used) WHS.
 
NTFS tools are included in most distributions, and certainly in Ubuntu.  To enable remote access to files, you would need to configure Samba shared, which isn't that hard.  You can do basic sharing via the GUI.

There are various solutions, but for that volume of data I would probably just get some extra drives and periodically duplicate new data onto them.  I assume that due to the nature of the beast, you're merely adding, rather than changing existing files.

As for MDAM, it works well; it's obviously not as simple as most on-board 'fakeraid' solutions.

Sorry, yeah I was planning on setting up Samba.

WIth the backups I was looking at something that can do my Windows 7 desktop as well as doing the configuration of Ubunutu. Kinda like a snapshot, or ghost image so to speak.

Do you have any other recommendations other than MDAM?

---

### Post by Grenage on 2012-02-17
> **just_cruising said:**
> Sorry, yeah I was planning on setting up Samba.

WIth the backups I was looking at something that can do my Windows 7 desktop as well as doing the configuration of Ubunutu. Kinda like a snapshot, or ghost image so to speak.

Do you have any other recommendations other than MDAM?

All of our backup software is hosted on Windows servers, and my home backup experience is a direct disc copy of every drive I use.  There are however some excellent cross-platform rsync programs available; I hear good things about Unison.  If you haven't come across rsync before, it's an excellent means of mirroring data, as it only noods to transfer the data that has changed.

MDADM is quite fine, I just prefer the onboard 'raid' options available on most consumer motherboards.

---

### Post by just_cruising on 2012-02-18
anyone able to give opinions on "dump" apparently it does full disc backups and can be set to incremental?

---

