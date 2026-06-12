---
title: "My departure from linux"
date: 2010-05-31
forum: General Help
---

### Post by zolsiemanym on 2010-05-31
Hi guys and gals, im currently departing from ubuntu as i installed it alongside vista. it said on the forums that if i did that i would have a choice between the two upon startup. ubuntu then proceeded to take over my whole hdd and re formatted it. i didnt ask or allow it to do that. anyway im wondering if someone could help me switch to windows 7. ive got the files but have no disk drive to burn a cd. can someone help me to make a bootable flash drive to install windows 7. please no spiteful messages about the switch and please no false info that will harm my computer. as you know ubuntu isnt for everyone and it happens not to be for me. could someone please help me to make the switch hassle free. any help would be greatly appriciated. yours, loz

---

### Post by ajgreeny on 2010-05-31
Are you sure it wiped your vista install and did not just miss adding it to grub?

Just to make sure, run the Ubuntu live CD, start **System ->Administration ->Gparted** and see what partitions are shown on your hard disk.  Attach a screenshot as well if you think it would help.

---

### Post by absolutezero1287 on 2010-05-31
> **zolsiemanym said:**
> Hi guys and gals, im currently departing from ubuntu as i installed it alongside vista. it said on the forums that if i did that i would have a choice between the two upon startup. ubuntu then proceeded to take over my whole hdd and re formatted it. i didnt ask or allow it to do that. anyway im wondering if someone could help me switch to windows 7. ive got the files but have no disk drive to burn a cd. can someone help me to make a bootable flash drive to install windows 7. please no spiteful messages about the switch and please no false info that will harm my computer. as you know ubuntu isnt for everyone and it happens not to be for me. could someone please help me to make the switch hassle free. any help would be greatly appriciated. yours, loz

When you set up the dual boot what exactly did you do? What OS was installed first? If you just blindly hit Next a bunch of times during the installation then its possible you did something wrong. I'm assuming that you have an Ubuntu Live Cd so that's the tool we'll use.

1 - So pop in an Ubuntu Live CD and set your BIOS to boot from CD before HDD. 

Now I'm going to give you some terminal instructions....don't panic.

2 - Go to the Applications Menu and choose Terminal from the "Accessories" submenu. Type the following in the terminal. Hit Enter at the end of each line unless otherwise specified.
```

sudo -s
gparted&

```

3 - Now you are using the partition editor as root. At this point you can choose to wipe out the partitions or take note of the partitions with data that you'd like to recover.

4 - If you want to recover data from partitions then you must mount the partition and store it somewhere. 

Here's an example: On my PC I have 3 partitions (sda1-3). These are my swap, root, and home partitions. All my crucial data is on sda3, which is my home partition. So to mount sda3 I'd first make a new directory and then mount sda3 to that directory.

```

mkdir /mnt/sda3
mount -t ext4 /dev/sda3 /mnt/sda3

```
The mount syntax is as follows:
mount -t $FILESYSTEM $DEVICE $DIRECTORY

If I was in your situation, I'd make a separate NTFS partition to be shared between Ubuntu and Windows 7. You can store all your documents and media there. Remember that Linux has a learning curve simply because its something new to you. Don't give up! Half the fun of using any Linux distro is learning how to customize it and fine tune it.

5 - At this point you have the option of backing up your stuff and just installing Win7 or giving the dualboot option another shot. If you wanna try the dualboot again then let me know in the next post and I'd be happy to guide you through it. Otherwise, just continue with the Win7 install.

---

### Post by zolsiemanym on 2010-05-31
> **magneze said:**
> [http://www.microsoft.com/windows/windows-7/](http://www.microsoft.com/windows/windows-7/)

HTH

I have got the files. cant you read?

---

### Post by nothingspecial on 2010-05-31
I can`t help you because I don`t know how to install windows but....

Can you use your ubuntu install for a minute.

Go to the menu and click accessories > terminal and type

```
sudo fdisk -l
```

Post the output here.

I just want to check that you don`t still have windows, and the linux bootloader isn`t seeing it.

---

### Post by nothingspecial on 2010-05-31
> **WinRiddance said:**
> **[B]but might happen if *YOU* click next** in the wrong places such as the place where Ubuntu makes the default suggestion of using an entire hard disk for the installation. 

The default suggestion is to install ubuntu side by side, you have to change it to "use the entire disk".

---

### Post by WinRiddance on 2010-05-31
> **nothingspecial said:**
> The default suggestion is to install ubuntu side by side, you have to change it to "use the entire disk".


Ooops, didn't have that memorized, my bad. That's even worse though than since that's even more proof of the inattentiveness ...

---

### Post by mikewhatever on 2010-05-31
> **zolsiemanym said:**
> I have got the files. cant you read?

I am sorry Ubuntu didn't work for you. To install W7, use the legal media provided to you by Microsoft or other legitimate vendor. Try seeking help at [http://forums.microsoft.com/](http://forums.microsoft.com/), in case you need any.

---

### Post by nothingspecial on 2010-05-31
Give him a break. I`d have an attitude if I`d just wiped my comfort OS by mistake.

I`m hoping he hasn`t and it`s just a grub issue.

---

### Post by nothingspecial on 2010-05-31
> **Rasa1111 said:**
> Perfect, Beautiful, True. +1
cheers

Actually, as I just pointed out, this is not true.

(S)he`s wiped windows without meaning to, that`s a major thing. 

We`re supposed to be to help.

This thread sounds more at home in the gentoo forums.

---

### Post by nothingspecial on 2010-05-31
> **jerenept said:**
> 
However I am inclined to think that the bootloader did not include Windows for some reason, and all your stuff is still there.

Me too. Although if the OP actually bothers repying after this debacle, I`d be supprised.

---

### Post by Rasa1111 on 2010-05-31
> **nothingspecial said:**
> Give him a break. I`d have an attitude if I`d just wiped my comfort OS by mistake.

I`m hoping he hasn`t and it`s just a grub issue.

Yeah but that attitude should be focused on ones own ignorance.
not everyone else who had nothing to do with it.

and if one cannot accept and admit to their own ignorance..
they belong where they are, wherever that may be. 

 So, if you cause something that's your own fault~
it's ok to get pissy with everyone else? because of your own stupidity?

 and then have the guts to ask for help, while
calling people jackass and saying things like "can't you read?"

 I dont care if I could help with the push of one button~
I would not bother to help such an ignorant person.

---

### Post by nothingspecial on 2010-05-31
> **Rasa1111 said:**
> 
I would not bother to help such an ignorant person.

So don`t bother replying.

---

### Post by cariboo on 2010-05-31
This thread doesn't seem to be going anywhere, plus we don't support piracy on the forums. Closed.

---

