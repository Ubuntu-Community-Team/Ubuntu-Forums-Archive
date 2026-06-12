---
title: "Advice re creating a backup disc"
date: 2012-01-31
forum: General Help
---

### Post by crs501 on 2012-01-31
Probably gonna get a bunch of you laughing, but whenever I don't know something I ask. I recently had a Windows XP OS, when It became (for some unknown reason, unusable - never knew for sure.) I made sure I had no Virus infestation and went back to a handy Ubuntu disc (8.04 LTS) that I had purchased and first used back in '08/'09. I then Installed 8.04 and proceeded to get all the updates (which were many) and in the process I upgraded to Lucid Lynx 10.04LTS, which I am enjoying today. I'm not having any problems and I'm eagerly anticipating the new LTS coming this Spring. Although I have the disc containing Ubuntu 8.04, what I think would be wise is to burn a backup disc, just in case. I see there are a number of choices however. My GUESS is that I should download and burn the one listed as " **10.04.3-desktop-i386.iso.torrent** " If I am correct OR if I should be downloading a different version, would somebody please advise. PLUS, if there are any hazards I should watch for as I'm burning this backup, could you also give me a head's-up? Sorry to sound so lame, I'm neither a programmer or developer, just an 'old guy User' who sees the wisdom of using Ubuntu. I'd appreciate any comments, just please don't get too technical with me, put 'em in 'old guy User' terms please! Thanks for taking the time to read and reply!  Richard...

---

### Post by lechien73 on 2012-01-31
There are no stupid questions...only stupid answers :) so ask whatever you need to ask.

If you want a re-installation disc for your operating system, and you have a fast Internet connection, then download: [http://releases.ubuntu.com/lucid/ubuntu-10.04.3-desktop-i386.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04.3-desktop-i386.iso)

You can burn it to a CD-R and use it to boot if your system becomes corrupted.

Before you burn it to a CD, run the following command against it:

```
md5sum ~/Downloads/ubuntu-10.04.3-desktop-i386.iso
```

Compare the resulting checksum code with the following code:

```
f63028da38308d917cd1460e14fb8540
```

If they're the same, then the image downloaded successfully, and you can burn it to a CD. I use *brasero* on Ubuntu to burn .iso images to CD or DVD.

---

### Post by Megaptera on 2012-01-31
If you want an exact copy of your 10.04.3 as you've set it up for yourself (rather than the option explained by lechien above), have a look at Remastersys.
From their site "Remastersys is a tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation.
It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it."

Here: [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by crs501 on 2012-01-31
To Both **Megaptera** & **lechien73**: Understood, Thank you!

---

### Post by Megaptera on 2012-02-01
You're welcome!!

---

