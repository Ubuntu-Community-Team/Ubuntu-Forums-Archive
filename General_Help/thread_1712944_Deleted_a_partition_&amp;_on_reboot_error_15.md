---
title: "Deleted a partition &amp; on reboot error 15"
date: 2011-03-23
forum: General Help
---

### Post by texas.chef94 on 2011-03-23
sda6 is 10.04 sda 7 was dreamlinux. Deleted DL and on reboot received error 15. Tried super grub but all Linux options fail.
Can only get to win 7
Please tell me I do not have to re-install. I have data galore on 10.04 and not backed up. Yea dumb. Please advise

---

### Post by muteXe on 2011-03-23
Fire up a live CD and paste results of

```

sudo fdisk -l

```

---

### Post by alphaamanitin on 2011-03-23
If you are worried about losing data you could use a live disk to clone the drive in question.  That way, no matter what you do you wont damage your chances of recovering the 10.04 files.  Or you could use something like TestDisk or PhotoRec to recover the data to a new drive and try recovering, secure that you won't lose the data.

AlphaA

---

### Post by oldfred on 2011-03-23
Were you using DL's grub to boot. It must be grub legacy as err 15 is an old grub message.

You probably just have to reinstall grub2's bootloader to the MBR. But lets see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

