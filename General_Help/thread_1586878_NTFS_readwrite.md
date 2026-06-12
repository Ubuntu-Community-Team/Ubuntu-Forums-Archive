---
title: "NTFS read/write"
date: 2010-10-02
forum: General Help
---

### Post by |Enraiha on 2010-10-02
Can anyone tell me the most simple and effective way to enable Ubuntu to read and write to external NTFS drives? I'm installing ubuntu on another machine and I want the process to go as smoothly as possible. 

I've had some success with the NTFS configuration tool on my current machine but that was through luck rather than judgement. I don't really understand what the tool is doing, so can someone please guide me through the process step-by-step?

Thanks.

---

### Post by coffeecat on 2010-10-02
> **|Enraiha said:**
> Can anyone tell me the most simple and effective way to enable Ubuntu to read and write to external NTFS drives?

You mean an external USB drive formatted NTFS? The simplest and most effective way I know is to plug the drive in, switch it on, let it be automounted and - um - read and write to your heart's content. :)

Ubuntu has supported read-write of NTFS filesystems and automounting of NTFS USB drives for more than 2 years now.

Which configuration tool was that and what were you using it for?

---

### Post by |Enraiha on 2010-10-02
Oh really:shock:. Thanks for the reply, i've must have read some old posts when I set it up the first time:oops:

---

### Post by Morbius1 on 2010-10-02
You're going to be sorry you asked :wink:

***STEP 1: Find out how the system sees your partitions***
In a Terminal:
```
sudo blkid -c /dev/null
```This will output , among other things the following partition that I want to mount at boot:
> [COLOR=DarkGreen]/dev/sda1[/COLOR]: UUID="DA9056C19056A3B3" LABEL="WinXP" TYPE="ntfs"***STEP 2: Create a mount point for your partitions to live in***
```
sudo mkdir [COLOR=Blue]/media/WinC[/COLOR]
```***STEP 3: Add a line to /etc/fstab/ to have that partition mount at boot:***
Edit fstab as root:
```
gksu gedit /etc/fstab
```And add a line at the end of it to mount the partition at boot:
```
/dev/sda1 /media/WinC ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0
```This will mount the ntfs partition to /media/WinC with ownership set to you ( the uid=1000 part ), and with read / write access to you and all other local login users ( the gid=46 part ) but no access to anyone else.
***Step 4: Mount it by executing the new fstab***
```
sudo mount -a
```You can vary the fstab line depending on how you plan to use it or if you plan on sharing it over your home network.

[COLOR=Blue]EDIT: Sorry, I need to read any responses before I submit my ramblings. I thought the requirement was to automount the ntfs partition. Never mind[/COLOR] :P

---

### Post by coffeecat on 2010-10-02
> **|Enraiha said:**
> Oh really:shock:. Thanks for the reply, i've must have read some old posts when I set it up the first time:oops:

Easily done. There's a lot of obsolete stuff out there. I was researching something earlier today and came across a google hit which I thought was going to be useful but then I saw it was talking about the 2.4.8 kernel which would have last been used sometime around the building of the pyramids. :|

By the way, if that was ntfs-config you were using - be very careful. Better still, don't use it. It's a dead project that hasn't been developed since it was first coded and has some nasty rough edges.

For external USB drives, just plug in as above. If you format an internal partition NTFS, you can mount it read-write as and when you need it simply by going to the Places menu. If you want an internal NTFS partition automounted on bootup, it's far safer to hand edit the system file /etc/fstab than rely on ntfs-config. If you need to do this, just start a support thread and someone will help you.

Good luck! :)

**Edit:**

> **Morbius1 said:**
> You're going to be sorry you asked :wink:

Seems like someone anticipated me. :lol:

---

### Post by coffeecat on 2010-10-02
@Morbius1, sorry to start a conversation over the OP, but...

> **Morbius1 said:**
> ```
/dev/sda1 /media/WinC ntfs defaults,nls=utf8,umask=007,uid=1000,gid=46 0 0
```

You might want to test those options by  copying a file from an ext3/4 partition to the mounted NTFS partition. If you use the manual option in the Ubuntu installer and specify a mountpoint for an internal NTFS partition, it comes up with:

```
device    mountpoint    ntfs    defaults,nls=utf8,umask=007,gid=46 0 0
```If you do an ext3/4 > NTFS copy the date/time changes to current, which is data corruption in my book. If you use cp from the terminal, you actually get an error message. I filed a Launchpad bug report and guess what? It's been ignored.

I find that:

```
device    mountpoint    ntfs    defaults,nls=utf8 0 0
```... with or without the nls option works just fine without data corruption. Your uid=1000 might prevent this, but it's certainly worth testing.

---

### Post by Morbius1 on 2010-10-02
coffeecat,

That's interesting. I've never noticed it. I'll have to check it out when I get back to my dual boot system. I'm glad I set the umask to 227 on my Windows system partition though :wink:

---

### Post by coffeecat on 2010-10-03
> **Morbius1 said:**
> That's interesting. I've never noticed it.

Here's another interesting thing. I'm posting from Maverick on a laptop with a shared data partition. I let the installer set up the fstab entry as usual from the manual partitioning option (just to see what it would do) and:

```
# /media/Data was on /dev/sda3 during installation
UUID=3C034B17236A5E09 /media/Data     ntfs    defaults,umask=007,gid=46 0       0
```Clearly, someone in development has made a change to the installer because the nls=utf8 option has now gone. But you still get the date/time corruption. That's bad. Very bad.

Here's some discussion I was involved in back in Karmic days. You'll see that others confirmed this.

[http://ubuntuforums.org/showthread.php?t=1330407](http://ubuntuforums.org/showthread.php?t=1330407)

---

### Post by Morbius1 on 2010-10-03
I'm still not in front of my dual boot machine but I just remembered that I have a VirtualBox setup with an NTFS data partition and Linux Mint Debian ( LMDE ) installed as a guest OS.

I set up the following line in fstab in LMDE:
```
LABEL=DataN    /DataN    ntfs    defaults,nls=utf8,umask=007,uid=1000,gid=46    0    0
```I copied a file ( copy and paste in Nautilus ) to /DataN and the timestamp is preserved. 
Change fstab to remove uid=1000:
```
LABEL=DataN    /DataN    ntfs    defaults,nls=utf8,umask=007,gid=46    0    0

```And the timestap is not preserved.

Don't know if the same thing would happen on Ubuntu since Debian and Ubuntu are incompatible but this is all very curious.

---

### Post by coffeecat on 2010-10-03
> **Morbius1 said:**
> Change fstab to remove uid=1000:
```
LABEL=DataN    /DataN    ntfs    defaults,nls=utf8,umask=007,gid=46    0    0

```And the timestap is not preserved.

Don't know if the same thing would happen on Ubuntu since Debian and Ubuntu are incompatible but this is all very curious.

What you've ended up there with is what the Karmic and Lucid installer would set up so, yes, it would happen in Ubuntu. My guess is that this is an upstream ntfs-3f bug being unmasked by the umask=007,gid=46 options. Next time I'm in Fedora 13 on my laptop I'll do some investigation there. It wouldn't surprise me if I get the same.

My irritation about this is that, notwithstanding an upstream bug, the Ubuntu installer issue is easily solved by using different options. Interesting that UID=1000 avoids the problem.

---

### Post by Morbius1 on 2010-10-03
That may be why I never noticed it. In a dual boot all my Windows system partitions are mounted with umask=227 to prevent me from writing anything to them. But all the other NTFS / FAT32 partitions have uid=1000 in case I decide later on to share something on them using Nautilus-share.

---

