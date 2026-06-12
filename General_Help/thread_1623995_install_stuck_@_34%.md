---
title: "install stuck @ 34%"
date: 2010-11-17
forum: General Help
---

### Post by houndhen on 2010-11-17
I have a older pc with a 20 gig hd that was running XP. It has an amd athlon chip and 512 mb ram. Not sure about the mz of the chip. I had to wipe the hd because of information that was on it. I used gparted to make the hd one big partition. I am trying to install xubuntu 10.10 alternative. I chose to let the installer use the whole drive. The installer wanted to set up the / partition as ext4 so I went back and changed it to ext3. Everything went fine until installing the base system and it gets to 34% and just sits with seemingly no activity. It says it is 'unpacking libbz2-1.0' but I don't think it is doing anything. I have been trying to get several distros installed on this unit so I could give it to someone that needs it. In my opinion Ubuntu is so much more user friendly than say Puppy. Most people where I live know nothing about Linux.

Is there a way to get this thing started installing again? 

Should I have used ext2 rather than ext3?

---

### Post by Quackers on 2010-11-17
Have you checked the MD5SUM of the downloaded image? It could be a bad download, a bad burn or a bad read issue.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by CharlesA on 2010-11-17
What version of Ubuntu are you trying to install?

The latest versions use ext3 and ext4 by default, ext2 does not offer journally, while ext3 and ext4 does.

---

### Post by houndhen on 2010-11-17
> **Quackers said:**
> Have you checked the MD5SUM of the downloaded image? It could be a bad download, a bad burn or a bad read issue.I checked the download but haven't checked the burn. I have been trying several distros and many of them fail during install. I'm about ready to just use this box for parts. I just hate to give up on something.

---

### Post by CharlesA on 2010-11-17
Could be a problem with that machine if several distros all fail. CD rom drive going out perhaps?

---

### Post by houndhen on 2010-11-17
> **CharlesA said:**
> Could be a problem with that machine if several distros all fail. CD rom drive going out perhaps?OK, thanks. I will keep pluggin along and see what I can do with it.

---

