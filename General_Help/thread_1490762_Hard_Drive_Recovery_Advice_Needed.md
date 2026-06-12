---
title: "Hard Drive Recovery Advice Needed"
date: 2010-05-22
forum: General Help
---

### Post by commodianus on 2010-05-22
I'm running 10.04 LTS (64 bit)

Hello people.

During a recent attempt at dual booting Windows 7, the Windows installer made a boot partition on the wrong drive, formatting the drive, and therefore destroying all my data.

The original partition was NTFS, and the new (unwanted partition) is NTFS.

Is there something in Linux I can do to recover the data that was there, or am I going to have to install Windows on yet another drive and use some Windows tools?

The data on this drive is extraordinarily important, containing ten years of digital photos, my source codes, and musical compositions (protools sessions etc).

Thanks for any advice.

Paul S. (commodianus)

---

### Post by sille777 on 2010-05-22
Might want to look into [Spinrite]("http://www.grc.com/sr/spinrite.htm")

---

### Post by jamesisin on 2010-05-22
There are several recovery tools in Ubuntu.  Ddrescue is in the repos.  Um, there is foremost.  There is TestDisk.  There are others.  Some of them are specifically photo recovery oriented.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Paddy Landau on 2010-05-22
For  data sufficiently important, I would be tempted to purchase the services of a professional.

Once you've recovered your  data, be sure to take a backup.

---

### Post by tgalati4 on 2010-05-22
Get another TB drive to capture the recovered files.  Boot an Ubuntu Live CD.

Open a terminal:

sudo apt-get install testdisk
man photorec

You will do something like:

photorec /log -d /media/external_tb_drive /dev/sda

---

### Post by Phrea on 2010-05-22
> **paddy landau said:**
> for  data sufficiently important, i would be tempted to purchase the services of a professional.

Once you've recovered your  data, be sure to take a backup.

+1

---

### Post by commodianus on 2010-05-23
Thanks all looking over my options. I appreciate all of the suggestions.

---

### Post by aysiu on 2010-05-23
> **tgalati4 said:**
> Get another TB drive to capture the recovered files.  Boot an Ubuntu Live CD.

Open a terminal:

sudo apt-get install testdisk
man photorec

You will do something like:

photorec /log -d /media/external_tb_drive /dev/sda
Photorec is definitely the way to go (and don't worry--it recovers just about every type of file, not just photos).

Guide here (with screenshots):
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

