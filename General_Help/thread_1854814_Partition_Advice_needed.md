---
title: "Partition Advice needed"
date: 2011-10-05
forum: General Help
---

### Post by Frazer on 2011-10-05
Hello,

I have very recently installed Ubuntu 11.4 on a computer that had an existing windows 7 partition.  After my wife had a test to see if she could use Ubuntu I removed the Windows 7 partition 
with the intention of increasing the size of the Ubuntu one.

  Is there a way to easily move the Ubuntu partion to ths start of the disk so I can resize it this way?  I cannot resize into the space left by the Windows partition on the left.  It is ext4 if that helps.

  Would it maybe be better to just create a large Home partition and use the main ubuntu one for just system files and software?

ps. I know a lot of people dont like it but im loving Unity.

---

### Post by dcstar on 2011-10-05
> **Frazer said:**
> Hello,

I have very recently installed Ubuntu 11.4 on a computer that had an existing windows 7 partition.  After my wife had a test to see if she could use Ubuntu I removed the Windows 7 partition 
with the intention of increasing the size of the Ubuntu one.

  Is there a way to easily move the Ubuntu partion to ths start of the disk so I can resize it this way?  I cannot resize into the space left by the Windows partition on the left.  It is ext4 if that helps.

  Would it maybe be better to just create a large Home partition and use the main ubuntu one for just system files and software?

ps. I know a lot of people dont like it but im loving Unity.

Do a forum search for the many posts already on resizing or moving partitions.

---

### Post by coffeecat on 2011-10-05
In theory, there should be no reason why you can't resize an ext4 partition to the left, but I can think of several reasons why you might be unable to do so at the moment. So that we can see exactly what is going on, post the output of these two terminal commands:

```
sudo fdisk -lu
mount
```

Please post the output between [noparse]```
 and 
```[/noparse] tags for clarity.

Not essential but you might also want to post a screenshot of a Gparted window showing your partition layout.

PS. A lot of people do like Unity. Myself included. :wink:

---

### Post by Frazer on 2011-10-06
Thanks for the, tips. I have since managed to kill my ubuntu partition when moving it as the computer lost power at the wrong moment.  Ill just go for a clean install tonight.

---

### Post by zhogan85 on 2011-10-06
Sorry, that is one of the dangers of resizing active partitions. You might want to consider installing Ubuntu to a 20ish GB partion and then keep your data on a seperate data parition. If you're hard drive has excess space, you could consider creating a seperate, 20 Gb hard drive for testing other distros on. Then any future distros you install can all share the data partition. And if you ever have to reinstall Ubuntu, all your data will be fine. Just one option, of many.

---

### Post by Frazer on 2011-10-06
What I have done is one large partition and a swap partition.  I will look for some backup software, something like synctoy and every week or so use that to send data to a usb disk.  The problem is I like to mess with stuff and figure it out as I go instead of learning it.

I don't know how it works out but I work in windows support and something like this would be a 'chore' but when its my home system its 'fun' :guitar:

---

