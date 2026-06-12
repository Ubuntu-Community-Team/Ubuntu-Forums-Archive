---
title: "dual booth, but differently"
date: 2012-06-06
forum: General Help
---

### Post by tnob on 2012-06-06
Greetings all,

I own an old Dell desktop, in use for daily requirements. It's currently running as an Ubuntu 10:04 LTS/XP dual-booth, but 10.04 LTS will be replaced with 12:04 LTS shortly. 

For things like music production and video editing, however, it has never really been up to scratch, so my eye is on a powerful Asus laptop (Intel core;i3 231 0M;CPU@ 2-10 GHz;4Gb RAM;500 GBHDD). I'm also toying with the idea to make it a dual booth as well,

What I have in mind is to put Ubuntu 12.04 in one partition  and the latest version of Dream Studio in the other for. Is that technically feasible?

tnob

---

### Post by oldfred on 2012-06-06
Sure you can dual boot.

This fellow seems to want to do a bit more than dual boot. :)

[http://ubuntuforums.org/showthread.php?t=1985184](http://ubuntuforums.org/showthread.php?t=1985184)

I have multiple Ubuntu installs on my system. You do have to keep track of which system's bootloader is in the MBR and in control. You have to decide if you want to share data or not. So some partition planning in advance is worthwhile. I use 25GB / (root) partitions for every install including /home but have all data in data partitions. 

If you are doing Video editing, it is my understanding you cannot have enough RAM. So I might suggest more especially since cost is pretty low now for RAM. I do not do Video editing and my 4GB of RAM never seems to go to swap, but I do not load lots of programs at once.

---

### Post by tnob on 2012-06-08
> **oldfred said:**
> Sure you can dual boot.

This fellow seems to want to do a bit more than dual boot. :)

[http://ubuntuforums.org/showthread.php?t=1985184](http://ubuntuforums.org/showthread.php?t=1985184)

I have multiple Ubuntu installs on my system. You do have to keep track of which system's bootloader is in the MBR and in control. You have to decide if you want to share data or not. So some partition planning in advance is worthwhile. I use 25GB / (root) partitions for every install including /home but have all data in data partitions. 

If you are doing Video editing, it is my understanding you cannot have enough RAM. So I might suggest more especially since cost is pretty low now for RAM. I do not do Video editing and my 4GB of RAM never seems to go to swap, but I do not load lots of programs at once.

> **oldfred said:**
> Sure you can dual boot.

I have multiple Ubuntu installs on my system. You do have to keep track of which system's bootloader is in the MBR and in control. You have to decide if you want to share data or not. So some partition planning in advance is worthwhile. I use 25GB / (root) partitions for every install including /home but have all data in data partitions. 

If you are doing Video editing, it is my understanding you cannot have enough RAM. So I might suggest more especially since cost is pretty low now for RAM. I do not do Video editing and my 4GB of RAM never seems to go to swap, but I do not load lots of programs at once.


Thank you very much for your advice and the link, oldfred. I see what you mean now.

I haven't got my dream laptop yet, though; at the moment, I'm just trying to figure out what best to put on. And minutes after posting my last submission, another option sprang to mind: since I'd also like to take this laptop along whilst traveling, I'm wondering now if it could be a dedidicated Ubuntu Dream Studio unit, too, with daily essentials from my desktop (such as mobile internet, Opera, Thunderbird, Writer and Gedit)  added on.

What do you think?

tnob

---

### Post by oldfred on 2012-06-09
My laptop used to be XP and my Desktop Ubuntu dual booted with XP. But I shared Firefox & Thunderbird profiles on my Desktop. But Samba kept having issues between XP updates, XP's firewall updates, XP's virus checker updates & my Ubuntu updates. I just converted laptop to Ubuntu and use NFS to copy profiles t my install on the laptop & back again when I get home. Then I have the same email & bookmarks when I travel as I have at home.

---

