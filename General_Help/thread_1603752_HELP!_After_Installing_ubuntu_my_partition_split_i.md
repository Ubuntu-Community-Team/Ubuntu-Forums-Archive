---
title: "HELP! After Installing ubuntu my partition split in half"
date: 2010-10-23
forum: General Help
---

### Post by kantagara on 2010-10-23
Few weeks ago I installed ubuntu on my old PC (celeron 2.4ghz, 2x40GB HDD,etc.) but when I enter to ubuntu for the first time I saw two partitions each of them have 20GB. I thought it was normal. But when my brother ask me to put windows 7 home basic i saw that there were 2 partitions. One of them is logical :confused: so I really need those second 20 gigs and i don't know how to return them. Any advice? Thank you!

---

### Post by d3v1150m471c on 2010-10-23
not sure what you're asking. did you install it along side of w7?

---

### Post by kantagara on 2010-10-23
no I didn't. I installed ubuntu then formated a how can I say... non-logical partition where it was installed. so I have only win 7. The other 20gigs are invisible.
and also i couldn't format or extend that logical 20 gb partition

---

### Post by Hippytaff on 2010-10-23
You should be able to reinstall ubuntu on the free space with the liveCD if that's what your asking?

---

### Post by kantagara on 2010-10-23
I'm asking how to return it to previous state (40GB HDD one partion) or at least how to make that logical partition visible im my computer in win 7

---

### Post by kantagara on 2010-10-23
Any1?

---

### Post by Hippytaff on 2010-10-23
Get rid of the partition you don't want and extend the one you do to fill the HDD. So if you want rid of ubuntu use the windows partition software or Geparted for the other way around :-)

---

### Post by oldfred on 2010-10-23
Windows will see and use as a data  partition even if logical if it is NTFS. Windows does not like to install in logical partitions. Do you have any data in the partition. If so back it up and use gparted to reformat to NTFS. Windows & Ubuntu can then use it as a shared data partition.

To know for sure what the partition is:

```
sudo fdisk -l
```

---

### Post by Hippytaff on 2010-10-23
> **oldfred said:**
> Windows will see and use as a data  partition even if logical if it is NTFS. Windows does not like to install in logical partitions. Do you have any data in the partition. If so back it up and use gparted to reformat to NTFS. Windows & Ubuntu can then use it as a shared data partition.

To know for sure what the partition is:

```
sudo fdisk -l
```

I agree, but the op seems to want to rid him/herself of an os...but I can't quite decipher the question :-)

---

### Post by akand074 on 2010-10-23
I can't quite decipher the question either.. I'm thinking perhaps in windows he can't see some partitions, but in Ubuntu/partitioning tools they appear? So he's confused..? Or not, I come up with something else he might mean every time I read it.

Though as stated before, this would be a good start to get some help:

sudo fdisk -l

---

### Post by d3v1150m471c on 2010-10-23
while in ubuntu can you give me the output of the following commands:
```

cat /etc/fstab

df -h

```

---

### Post by kantagara on 2010-10-24
I'm right now on ubuntu 10.04 live CD and it appears that it shows that second 20gigs and I think that there is ubuntu installed on it. so I think that the GRUB is broken or something like that.

---

### Post by Manifest on 2010-10-24
When you turn on your computer does it ask which thing to boot?


example
[IMG]http://www.dedoimedo.com/images/computers/dual_boot_boot_loader.jpg[/IMG]

---

### Post by kantagara on 2010-10-24
nope. It goes straight to windows 7

---

### Post by d3v1150m471c on 2010-10-24
i take it you have 2 different hard drives. you probably need to go into you bios menu and set it to boot from the different disk if that's the case. it looks to me like you have w7 on the default hdd and ubuntu on the other.

---

### Post by kantagara on 2010-10-25
Yes I have 2HDD-s but only one of them is splited. do you understand?

---

### Post by Hippytaff on 2010-10-25
Maybe try [http://ubuntuforums.org/showthread.php?t=1604123](http://ubuntuforums.org/showthread.php?t=1604123) post #2

---

### Post by oldfred on 2010-10-25
Post this so we can understand.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by kantagara on 2010-10-25
I've done something :) In partition manager (win 7) I've found the "lost" 20 gb and I formated it to NTFS. Now I want to install ubuntu to that partition again :D 
but how to do that? I've tried with wubi but it only asks me to install on C: partition.

---

### Post by Hippytaff on 2010-10-25
> **kantagara said:**
> I've done something :) In partition manager (win 7) I've found the "lost" 20 gb and I formated it to NTFS. Now I want to install ubuntu to that partition again :D 
but how to do that? I've tried with wubi but it only asks me to install on C: partition.
You need to do a fresh install with a liveCD or USB. Burn the iso to disc, then run the installation once its booted. (Might be a good idea to read up on partitioning and having a seperate /home partition)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by kantagara on 2010-10-25
i have one more question and you can edit this topic with prefix solved :)

Is there any possible way to install [ArtistX]("http://www.artistx.org/site2/") with WUBI?

---

### Post by oldfred on 2010-10-25
Wubi is a modified Ubuntu to allow Windows users to try it. It looks like ArtistX is just a standard install. You will have to create / (root) and swap partitions to install that distribution.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

### Post by Hippytaff on 2010-10-25
> **oldfred said:**
> Wubi is a modified Ubuntu to allow Windows users to try it. It looks like ArtistX is just a standard install. You will have to create / (root) and swap partitions to install that distribution.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

Which means really partitioning your HD rather than installing it 'inside' windows like wubi does :-)

So back-up stuff if you plan to do this :-)

---

