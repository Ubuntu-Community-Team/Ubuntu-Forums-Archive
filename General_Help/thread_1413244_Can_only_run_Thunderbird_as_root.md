---
title: "Can only run Thunderbird as root"
date: 2010-02-22
forum: General Help
---

### Post by belnac on 2010-02-22
Hello,

I'm a newcomer to Ubuntu and my technical expertise when it comes to *nix environments is very limited.

I tried installing Thunderbird from the official package and took the following steps:
1) Download package to my home dir
2) Extract it there
3) Move thunderbird dir to /opt/
4) Create link to thunderbird executable in /usr/local/bin/ using command ln -s (link works)

Now, I can run thunderbird just fine, however only as root. Whenever I try to run on my own user name I get a pop up box stating: "Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system." 

This I find odd because I can run it just fine as root, plus I tried looking for a daemon or any running process whatsoever that would hint that thunderbird was indeed already running, but couldn't find any -- but then again why would it run as root? In despair I even set ownership of every single file in /opt/thunderbird/* to nobody:nogroup thinking that could be at the root of the issue. In addition, I should say I tried installing thunderbird in /usr/local/ but that too didn't work out very well: same result, could only run it as root.

How do I sort out this mess?

---

### Post by kellemes on 2010-02-22
It's all so much easier..
[https://help.ubuntu.com/community/Thunderbird]("https://help.ubuntu.com/community/Thunderbird")

---

### Post by NCLI on 2010-02-22
Start by undoing everything you've done in your attempt to install Thunderbird, then open the Ubuntu Software Center, search for Thunderbird, and install it.

---

### Post by cong06 on 2010-02-22
I mean, from what his post says, it sounds like he has command experience.

Run:
```

sudo apt-get install thunderbird

```
in the commandline

oh the beauty of apt-get! (or aptitude depending on what you use)

---

### Post by belnac on 2010-02-22
> **cong06 said:**
> I mean, from what his post says, it sounds like he has command experience.

Run:
```

sudo apt-get install thunderbird

```
in the commandline

oh the beauty of apt-get! (or aptitude depending on what you use)

Thanks for that, but wouldn't that install the 2.x version? I'm after the latest ver. 3.0.1 (I believe), which I could only find on Mozilla's official website. And from what I've read so far you can only install this particular version manually.

---

### Post by kellemes on 2010-02-22
> **belnac said:**
> Thanks for that, but wouldn't that install the 2.x version? I'm after the latest ver. 3.0.1 (I believe), which I could only find on Mozilla's official website. And from what I've read so far you can only install this particular version manually.

Easy..
[https://help.ubuntu.com/community/ThunderbirdNewVersion]("https://help.ubuntu.com/community/ThunderbirdNewVersion")

---

### Post by belnac on 2010-02-22
> **kellemes said:**
> Easy..
[https://help.ubuntu.com/community/ThunderbirdNewVersion]("https://help.ubuntu.com/community/ThunderbirdNewVersion")

Nice kellemes! Thanks man. :)

---

### Post by Alistair George on 2012-01-06
Not the same as the OP, but I can run TB fine, until I want to install a new extension. Please let me describe:
TB has been running fine, but due to several versions of ubuntu, I want to share a common profile which points to a Windows folder.
Thunderbird works fine but when wanting to install a new extension extensions.log shows > 2012-01-07 10:47:12 - safeInstallOperation: file extraction failed, rolling back file moves and aborting installation.
2012-01-07 10:47:12 - ExtensionManager:_finishOperations - failure, catching exception - lineno: 1609 - file: undefined - [Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)
If TB is started in sudo mode, this problem does not exist. Any suggested workaround?
Thanks,
Al.

---

### Post by ottosykora on 2012-01-06
>I want to share a common profile which points to a Windows folder.<

could it be an option for you to place the common profile on fat32 formated drive? (there are no rights on then )

Otherwise be careful with extensions particularly, they are often not compatible with different versions of TB at the same time.

---

### Post by Alistair George on 2012-01-06
> **ottosykora said:**
> >I want to share a common profile which points to a Windows folder.<

could it be an option for you to place the common profile on fat32 formated drive? (there are no rights on then )

Otherwise be careful with extensions particularly, they are often not compatible with different versions of TB at the same time.

FAT32 not a bad idea thanks; the current shared partition is running NTFS so presume permissions would apply.

---

