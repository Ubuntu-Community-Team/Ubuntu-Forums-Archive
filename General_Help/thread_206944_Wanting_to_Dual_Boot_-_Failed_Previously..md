---
title: "Wanting to Dual Boot - Failed Previously."
date: 2006-06-30
forum: General Help
---

### Post by Grogs on 2006-06-30
A few months back I tried Ubuntu on my secondary PC and loved it, and I only changed it back for other peoples use (who have now requested me to put it back on actually), but this made me want to use it myself. So I went about installing it on to my main computer  attemping to do a dual boot with my XP install. However, somehow I messed up my MBR, rendering my XP isntall unusable. Luckily I used ti for more of an excuse to reinstall Windows, but it pushed me off Linux and Ubuntu for a while. Well not I'm back, I ordered one of the free Ubuntu CDs of the new release and I put it in my computer and am using it now... and loving it. Totally wanting to try it again, especially now  since two of my friends are now interested in using it, would be nice if we could all progress and share info at the saame rate, hopefully make the transition easier for the three of us.  

Yet I really don't want to delte my MBR again. My Windows drive doesn't really have any spare space on, so instead I would like to isntall it on an other drive (a 250gig one) where I have 60GB free - I would like to use 10-30GB for the Ubuntu. Is there any guides or anything which you can giv eme or link to that will give me very detailed instructions on how to install Ubuntu as a dual boot with XP? I had a bad experience last time and I **really** don't want to repeat that again and push myself away from Linux again. At the moment I've got down to just two irriplacable  programs on Windows, so I'm most of the way there to switching.

Please, I need detailed instructions on how to setup a dual boot, on another harddrive  seperate to my Windows install one too. I'm willing to put the time in and everything, but to mess everything up again would be annoying to say the least.


Thanks for any help anyone can give, and I'm sorry if this thread is incorrectly placed or I have spelling mistakes etc..

Thanks,
Greg

(I previously used v5 [Breezy Badger?] when installing Ubuntu - now have 6, Dapper Drake.)

---

### Post by IcemanV9 on 2006-07-01
Please check wiki on [Dual Boot]("https://wiki.ubuntu.com/WindowsDualBootHowTo").

---

### Post by Herman on 2006-07-01
Hello, Greg
> Is there any guides or anything which you can giv eme or link to that will give me very detailed instructions on how to install Ubuntu as a dual boot with XP?For the 'Desktop' Install/Live CD, aysiu made an excellent webpage, [*click here*]("http://www.psychocats.net/ubuntu/windowstoubuntu.html") to see that. The rest of his website has lots of really interesting and helpful information for you also, [*click here*]("http://www.psychocats.net/ubuntu/index.php") for that, and follow links. The 'Desktop' Install/Live CD is the easiest for new people, as it features a graphical partition editor, a lot of people like that.

The 'Alterate' install CD has more options for customising your install, including a choice of Linux bootloaders (GRUB or LILO) and it allows you to specify where you would like the bootloader to install. The 'Alternate' Install CD is uses the traditional text based partitioner that you may be familiar with. The text based partitioner is easy to use when you know how, but some people found it a little confusing. That's why I made a website to explain how to use it. [*Click Here*]("http://users.bigpond.net.au/hermanzone/") for that. That site really only shows examples of installing on a single hard disk, but lots of people who have multiple hard disks use it anyway and they seem to manage somehow. 

> However, somehow I messed up my MBR, rendering my XP isntall unusableFor the vast majority of installs, Ubuntu and GRUB install on most people's MBRs just fine, but there are a few rare instances of bad luck when things don't go as planned. I'm sorry to hear you had trouble.
I made a special new article on how to use the new Dapper Desktop Live/Install CD to make a backup of your bootloader section of your MBR and restore it again. That should help you feel better. [*Click here*]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd") for that. 

it is a good idea to take the precaution of downloading a copy of GAG Boot Manager before beginning any Linux install, it will nearly always boot Windows for you if GRUB gets installed with any errors in it. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm") for that. 

Quite often the MBR has not been 'hosed' at all, Most errors in GRUB are easy to correct by editing GRUB's menu.lst if the new user knows how. I also made an illustrated GRUB Page that explains most of what I know about how to configure and use the GRUB boot loader in Ubuntu so people will not feel so stressed if they have a few problems with GRUB. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm")

I hope some of this is helpful to you, regards, Herman :D

---

### Post by Herman on 2006-07-01
Hello again, Greg, I was searching through the forums to learn more about GRUB's map commands and how they are applied. Since you are planning on using more than one hard drive I though I'd give you the link to a thread containing more links in case you need it. Here, [http://ubuntuforums.org/showthread.php?t=179902&highlight=map+commands](http://ubuntuforums.org/showthread.php?t=179902&highlight=map+commands)
You might not need any of that, especially if Windows remains as hd0,0 (first installed on your first hard drive) but just in case you might....there it is anyway.

---

### Post by Grogs on 2006-07-01
Wow, lots of links, thanks. I'll read through them all later today, and hopefully go ahead try and install again. Thank you very much, both of you, will read it all if i can.

Thanks again, 
Greg

---

