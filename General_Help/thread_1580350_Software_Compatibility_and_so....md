---
title: "Software Compatibility and so..."
date: 2010-09-23
forum: General Help
---

### Post by Chishio on 2010-09-23
I've been running Ubuntu for a few days and I really like it. I run it through Wubi now but I'm thinking of moving to Ubuntu completely and deleting Windows. But before I do so, I'd like to know some things.

**1** Is there any way (Wine or just regular installation) to get on Ubuntu software such as:
- Adobe Photoshop CS2
- VLC Player / BS Player and some Codecs (to be specific, I want it to be able to play MKV files)
- Winamp (mainly for MP3s)
- DAEMON TOOLS or any other virtual emulator for ISOs
- Skype
- FL Studio
- CCleaner
- Opera (Web Browser)

_1.1_ Is Wine capable of installing any software which would run only on Windows ? Such as those mentioned previously or even games made originally compatible with Windows only ?

**2** So, let's say I decided to remove Windows completely.
_2.1_ When I go through CD installation and choose Use the Entire Disk, would it Delete everything, including Windows ?
_2.2_ Just in case, how do I remove Windows manually ? (if it is written somewhere, link would be enough)
_2.3_ After removing Windows manually,
*2.3.1* Would it remove the disk partitions I have (C and D) ?
*2.3.2* Would it remove all the files I have on my disk or would I have to format my disk or something ?

**3** When I download something or create some files on Ubuntu and move it to my external HDD, would Windows on some other computer be able to read/open it ? Also in connection to this, can you put here also a link to some guide on those file systems such as *Ext4* ...


Ok, so.. I think that is all I would like to know for now. 

Thanks for your answers to all those questions in advance.

---

### Post by pedro_orange on 2010-09-23
> **Chishio said:**
> 
**1** Is there any way (Wine or just regular installation) to get on Ubuntu software such as:
- Adobe Photoshop CS2
- VLC Player / BS Player and some Codecs (to be specific, I want it to be able to play MKV files)
- Winamp (mainly for MP3s)
- DAEMON TOOLS or any other virtual emulator for ISOs
- Skype
- FL Studio
- CCleaner
- Opera (Web Browser)


- Photoshop - [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631)
- VLC - Comes with Ubuntu
- Winamp - Hundreds of other tools to play music with. 
-GMountISO will mount iso images for you, or you could just mount them using the mount terminal command.
- Skype works on Ubuntu
- FL Studio  - [http://appdb.winehq.org/objectManager.php?sClass=application&iId=178](http://appdb.winehq.org/objectManager.php?sClass=application&iId=178)
- CCleaner, don't really need it.
- Opera yup.

> **Chishio said:**
> 
_1.1_ Is Wine capable of installing any software which would run only on Windows ? Such as those mentioned previously or even games made originally compatible with Windows only ?


Not all but some. Check the WineHQ AppDB for more information.

> **Chishio said:**
> 
**2** So, let's say I decided to remove Windows completely.
_2.1_ When I go through CD installation and choose Use the Entire Disk, would it Delete everything, including Windows ?
_2.2_ Just in case, how do I remove Windows manually ? (if it is written somewhere, link would be enough)
_2.3_ After removing Windows manually,
*2.3.1* Would it remove the disk partitions I have (C and D) ?
*2.3.2* Would it remove all the files I have on my disk or would I have to format my disk or something ?

- Yes it would delete everything if you used the entire disk.
- Setting it to use the entire disk, will erase everything on that disk, and build Ubuntu on there from scratch
- You can alter the disk partitions in the Ubuntu installer. Also drive letters such as C: and D: are Windows terms. Everything in Linux lives under / (root)

> **Chishio said:**
> 
**3** When I download something or create some files on Ubuntu and move it to my external HDD, would Windows on some other computer be able to read/open it ? Also in connection to this, can you put here also a link to some guide on those file systems such as *Ext4* ...


Yes. If it has a program that can read the file type. Eg you can't open PDFs on Windows without Adobe Reader on it.


Enjoy Ubuntu.

---

