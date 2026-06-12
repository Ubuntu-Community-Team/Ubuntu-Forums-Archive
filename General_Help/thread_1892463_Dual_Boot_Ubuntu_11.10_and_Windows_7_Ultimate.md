---
title: "Dual Boot Ubuntu 11.10 and Windows 7 Ultimate"
date: 2011-12-08
forum: General Help
---

### Post by plp85 on 2011-12-08
Hi guys;

I am looking for help in getting my dual boot working.

I have installed Windows 7 (64bit) to my SSD, I then installed Ubuntu 11.10 to the left over space on the same SSD. The installation seems to go fine.

However when I restart after the installation, I get no GRUB2 menu to select an OS, it just boots straight into Windows 7.

My partitions:

sda1 100MB System Reserved (WIN)
sda2 74GB NTFS (WIN)
sda3 29GB EXT4 (Ubuntu)
sda4 6.5GB swap area (ubuntu)

I have searched online and cant find a solution to remedy this for me.

If anyone can help with this, or suggest another thread with another solution I can try, I would much appreciate it.

Many Thanks

plp85

---

### Post by satanselbow on 2011-12-08
Where did you install the bootloader? (GRUB2)

If you put it anywhere other than /dev/sda the Windows bootloader will get precedence when you power up the machine :(

If this is a clean virgin Ubuntu install (ie no data to recover) then the simplest & fastest solution would be to re-run the installer and be mega-careful that you install the bootloader to /dev/sda (no postfix number at all). 

If you fancy a more educational solution you could repair it from a LiveCD - but in a clean install it is frequently easier (and quicker) just to start again.

As your Ubuntu partitions have been "pre-created" you can just re-use them (get the numbers right!) by using the "do something else" option in the Ubuntu installer and point sda3 to "root", sda4 as swap ;)

---

### Post by plp85 on 2011-12-08
Thanks for such a quick reply.

When carrying out the install I'm pretty sure I wasn't asked where to install GRUB2... I have reinstalled it twice, and no point do I remember it giving me the option to specify.

I clicked install and the only information it asked for was 

Language / region / User Name / System Name / password etc

I created the partitions, but dont remember any options in there for the bootloader.

I selected sda3 for the install partition... as it doesn't let me install to sda

Thanks

plp85

---

### Post by Mark Phelps on 2011-12-08
If you want to continue to use Win7, I would strongly suggest that you use the Win7 Backup feature to create and burn a Win7 Repair CD.  Messing around with GRUB installations runs the risk of corrupting the Win7 boot -- this CD will provide you the means of restoring that.

---

### Post by oldfred on 2011-12-08
+1 on Mark Phelps's suggestion of Windows repairCD, a few things you can fix from Linux, but to repair Windows it is often best to use Windows tools.

This will show where everything is at. If you used manual partitioning (Something Else), then just below the partitioning screen was a combo box on where to install grub2's boot loader. Normal default is sda.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

This also runs boot info script and can do some minor repairs.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by plp85 on 2011-12-08
This is a completely new system with fresh windows too, so I can just reinstall Windows 7 if anything does go wrong. So I don't think I need a repair cd?

I will try another install and see if I missed the bootloader option, and then I will the Boot Info Script.

Any further suggestions for now?

Thanks Guys

plp85

---

### Post by plp85 on 2011-12-08
Ok I am reinstalling currently having found the bootloader option (thanks oldfred)

However it was already set to ***sda*** (with no prefix)
As I never changed it from the default last time (not having seen it) I assume this will replicate the previous issue once installed.
If so I will try the Boot Info Script.

Sidenote: I noticed that the Windows Loader is installed on sda[COLOR="Red"]***1***[/COLOR] I assume that is what is booting windows on boot, and not allowing grub2 to function...
I assume this is what grub2 points at when it wants to load Windows, so installing grub2 to that location wouldn't help me dual boot. correct?

---

### Post by plp85 on 2011-12-08
Ok, re installing didn't work..
Will try boot info script now

Additionally, do I need to need to put a mount point in for the Swap partition? (I put / in for my ext4 partition for root correct?)

Thanks

plp85

---

### Post by asvestomix on 2011-12-08
I would suggest you to use this method (see the link above) to make your dual boot using windows boot manager, note that this guide is for 11.4 but it has no difference with 11.10 too

[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/2/]("http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/2/")

---

### Post by bluexrider on 2011-12-08
> **plp85 said:**
> Ok, re installing didn't work..
Will try boot info script now

Additionally, do I need to need to put a mount point in for the Swap partition? (I put / in for my ext4 partition for root correct?)

Thanks

plp85

please make reference to this

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by plp85 on 2011-12-09
Hi

I tried boot-repair which also didn't work, I will try boot info script next.

> **bluexrider said:**
> please make reference to this

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


Thats the guide I followed to the letter 4 times, and no luck

Cheers

Phil

---

### Post by asvestomix on 2011-12-09
> **plp85 said:**
> Hi

I tried boot-repair which also didn't work, I will try boot info script next.




Thats the guide I followed to the letter 4 times, and no luck

Cheers

Phil

Did it gave you any message that saying grub failed to  install when finished with the set up?

---

### Post by asvestomix on 2011-12-10
> **plp85 said:**
> Hi

I tried boot-repair which also didn't work, I will try boot info script next.




Thats the guide I followed to the letter 4 times, and no luck

Cheers

Phil

you have to install grub to your "/boot" partition and then from windows add an entry using easybcd

---

### Post by Mark Phelps on 2011-12-10
> **asvestomix said:**
> you have to install grub to your "/boot" partition and then from windows add an entry using easybcd

That's OK ... as long as it is not the WINDOWS boot partition.  IF you install GRUB there, you will break the Win7 boot loader so it won't boot anymore.

---

### Post by crackpotfox on 2011-12-10
did you install windows then linux, or linux then windows...

---

### Post by psycko2012 on 2011-12-11
ive spent a few hours now trying to find an answer to what i thought would be an easy question (but i may unconciously be the most masochistic person in the entire world)

dual boot/install everything worked perfect.  encrypted home, had everything installing so smoothly.  finally i get to where i enter my new admin password.  i swear i chose something simple and even wrote it down after passwords matched.  then i had left for work, and on return, the password i had written was wrong.  i tried every password combo i could think of.   i had nothing saved in that install of ubuntu, and finally i understood the post stating encrypted home accounts cannot reset passwords.  but i could find no options linked to this advice,  i assume its simply reinstalling the ubuntu OS, an i am somewhat a beginner at touching partitions (and i simply CANNOT lose or corrupt my windows 7 os or its memory)   

my question is,  can i simply just reinstall or is it going to be a requirement that i have to chance corrupting my mbr.. and on top of that i cannot understand how my password was wrong, and how none of my other attempts were correct either, since ive got a grip of passwords used in the past ill use at first until i can secure whatever it is with a random password.  

anyways, thank you for any of your help,  and yes i have been through many post regarding this topic but all of them have different methods and that does not settle well with my concern for my windows os.

 thanks again.

---

### Post by oldfred on 2011-12-11
As long as you have no information to lose, then you can just reinstall. You do want to use the manual install (Something Else) and choose the same partitions for / (root) and /home and reformat them.

---

### Post by plp85 on 2011-12-23
Ok I am at a loss....

I have tried all the suggestions in this thread, with no joy.
No matter what I try grub has never appeared at boot, and windows always starts by default.

I will perhaps try again after the christmas period.

If any one has any other ideas I would be grateful?

Thanks

plp85

---

### Post by oldfred on 2011-12-23
Sometimes too many different suggestions can cause issues. To best know where you are at and then we can make specific suggestions on what to do, you need to run boot script. Sometimes you are booting, it has not found Windows so it does not show menu & then it is a video issue.

---

