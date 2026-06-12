---
title: "Ubuntu on SSD"
date: 2012-03-08
forum: General Help
---

### Post by eawz9999 on 2012-03-08
I have an Ubuntu 11.04 server. Sata-1 is a 1 TB HDD partitioned in 2. The first partition (70 GB) is the (/) system, the rest is /home.
I have installed in sata-2 a 60 GB SSD. This drive is recognized by BIOS and by Ubuntu, I can mount it, format it, etc.
I would like to move my system partition (/) to this new drive. It would not be any problem if I can install Ubuntu 11.04 in this SSD and tar the system partition from sata-1.
My problem is that the Ubuntu installer does not recognize this SSD. Why would Ubuntu recognize it and not the installer?
Any suggestion?
Thanks, Enrique

---

### Post by NoBugs! on 2012-03-16
What type of SSD is it? Perhaps a newer Ubuntu might support it, did you tru 11.10, 12.04 beta?

---

### Post by imachavel on 2012-03-16
so you are trying to capture the image? Obviously the drive has nothing to do with whether ubuntu will recognize it. Ok do the forum a favor. open a terminal

ctrl+alt+t

now type in sudo apt-get install boot-repair

what does it come up with? if it installs, please create a grub script, and upload it as an attachment. Also, what do you mean when you say that the OS won't recognize the drive? You mean the bios won't recognize the drive? Well how many sata ports do you have? Try reseating the sata connector, disconnect and reconnect etc. now try seeing if the ssd is recognized. 64 bit eh? Should make no difference. Remember if you are using the old hdd and have the new ssd installed side by side, then of course the pc is used to booting to the first hdd. Try disconnecting it before booting to ubuntu live cd to install.

Am I missing something? 4 gb ram? You said laptop? Or desktop? Not sure if there are details we are missing, is it called dual copy? The name of the linux program that captures the entire partition and image of the OS to transfer everything? If you already solved the problem please let everyone know how you did so......

---

### Post by imachavel on 2012-03-16
> **eawz9999 said:**
> I have an Ubuntu 11.04 server. Sata-1 is a 1 TB HDD partitioned in 2. The first partition (70 GB) is the (/) system, the rest is /home.
I have installed in sata-2 a 60 GB SSD. This drive is recognized by BIOS and by Ubuntu, I can mount it, format it, etc.
I would like to move my system partition (/) to this new drive. It would not be any problem if I can install Ubuntu 11.04 in this SSD and tar the system partition from sata-1.
My problem is that the Ubuntu installer does not recognize this SSD. Why would Ubuntu recognize it and not the installer?
Any suggestion?
Thanks, Enrique

how in the world would you put an entire OS on two partitions, one being the file system, the other being just home directory. Is that actually possible? Anyway sorry to be confused, just trying to get as clarified as possible

---

### Post by MG&amp;TL on 2012-03-16
> **imachavel said:**
> how in the world would you put an entire OS on two partitions, one being the file system, the other being just home directory. Is that actually possible? Anyway sorry to be confused, just trying to get as clarified as possible


Quite possible, just not usually given by the normal installer, you have to use advanced mode. :) [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by eawz9999 on 2012-03-17
[COLOR=black]I put the system files in one partition and /home in another. My /home partition is very large (photos, videos, music, family server, virtual servers, etc). If I really mess up my system I can reinstall Ubuntu on the system partition and return to a previous stage with the daily tar.gz files. I don't need to touch the /home partition and saves me a lot of time.
[/COLOR]
[COLOR=black]The problem with the **SSD** was not with Ubuntu or Bios. The problem was with the chipset on my motherboard, ([/COLOR][COLOR=black]nvidia MCP61 sata controller that does not recognize the **ssd**, does not support AHCI).[/COLOR]
[COLOR=black]My solution was to buy a $20 pci-express sata controller.[/COLOR]
[COLOR=black]Now the** ssd** is recognized, I was able to move the root (/) partition, resized the /home partition to occupied the whole drive.[/COLOR]
[COLOR=black]It works great!!
[/COLOR]
[COLOR=black]Thanks for your input, Enrique:p
[/COLOR]
[COLOR=black]
[/COLOR]

---

