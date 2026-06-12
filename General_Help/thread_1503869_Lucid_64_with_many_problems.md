---
title: "Lucid 64 with many problems"
date: 2010-06-07
forum: General Help
---

### Post by Unkuiri on 2010-06-07
Hi, I'm having some trouble in lucid. Almost nothing seems to function. When the system starts it shows many errors saying that the panel applets are giving errors, most of them. Only works the menu and the starters. When I try to start firefox it quits automaticcally, when I try to start firefox from the comand line it says "Segmentation failed" or something like that and also quits. The same happens sometimes with gedit. The firefox works only when I delete the profile config, opens normally but when I try to move to another page it quits again...:(..Can someone help me?

Thanks in advance

---

### Post by 666f6f on 2010-06-07
What you describe isn't Ubuntu 10.04 Lucid Lynx, it's WWII. I bet the installation CD is corrupt. Can you verify its checksum? Here are the correct values: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Do you have access to any working operating system, and if yes, which one? Do you have a USB stick? If yes, what's its capacity?

---

### Post by Unkuiri on 2010-06-08
Hi, I'm working with Ubuntu 10.04 Lucid Lynx for a month I think and everything worked fine until yesterday...:(...so I think we could reject the currupt cd possibility...:(
The Ubuntu is half-functional, at least the nautilus program and others, I can move files and even see movies, but not internet (I don't know how to activate it from command line, but i think it is possible). I'm now using Win Xp...:(...I don't like to use it but I can't find other way...:(...

---

### Post by 666f6f on 2010-06-08
If everything is messed up, which seems to be the case, I'd suggest a fresh install. If only some things don't work, we need to tackle them one by one.

For the record, if your system run fine until yesterday, I can think of five possible reasons for a complete mess.. 1. You changed something accidentally 2. Someone else changed something on purpose (you've been hacked, which seems unlikely) 3. An update broke your system 4. a hardware failure 5. your filesystem became corrupt. I can't really tell which one is correct.

---

### Post by Unkuiri on 2010-06-08
I've tried to install something, maybe it broke the system. I tried to install [zlib]("http://www.zlib.net/") and [rtmpdump]("http://rtmpdump.mplayerhq.hu/") and with zlib I've done the command "sudo make install", do you think it changed any important files in the system?
Can I be hacked in linux?..:$..I thought that it wasn't possible...The problem with firefox really seems to me like a worm or virus, but the rest..

---

### Post by 666f6f on 2010-06-08
> **Unkuiri said:**
> I've tried to install something, maybe it broke the system. I tried to install [zlib]("http://www.zlib.net/") and [rtmpdump]("http://rtmpdump.mplayerhq.hu/") and with zlib I've done the command "sudo make install", do you think it changed any important files in the system?

Anything you run with root privileges may do system wide damage. I think that zlib exists in the repositories, you could install it by running ```
sudo apt-get install zlib-bin
```

> **Unkuiri said:**
> Can I be hacked in linux?..:$..I thought that it wasn't possible...

[Sure you can]("http://www.google.com/search?q=hacking+linux").

> **Unkuiri said:**
> The problem with firefox really seems to me like a worm or virus, but the rest..

I'm not aware of any viruses or worms that run on Linux, but I may be mistaken (that doesn't mean that Linux can't be hacked!). Unfortunately, I don't have a better explanation :(

---

