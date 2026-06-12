---
title: "saving preferences when updating to 9.10"
date: 2009-09-23
forum: General Help
---

### Post by djyoung4 on 2009-09-23
With the release of 9.10 coming soon i have thinking about what I am gonna do when i upgrade.  will it be easier to do a clean install or just upgrade.  I know that ext4 and grub2 are gonna be part of Karmic and I have heard good things but if I just update will it be difficult to get this working right.  If i do clean install how to I keep all of my preferences the same.  and if I were to upgrade how would I do that.

---

### Post by doas777 on 2009-09-23
well, back up the contents of your home dir, and any app config files that you have modified signifigantly.
then when you are running a liveCD to do the install, create a seperate home partiton, and copy your home files to it. 
then perform your install, creating a system and swap partition, and set the home partition to mount as /home.

after your install most of your desktop preferences will have carried over, and you can just restore your app config files.

hows that sound?

---

### Post by djyoung4 on 2009-09-23
sounds easy enough but would it be easier to just upgrade or does that bring about other problems.

---

### Post by doas777 on 2009-09-23
> **djyoung4 said:**
> sounds easy enough but would it be easier to just upgrade or does that bring about other problems.

I personally never do upgrades, under any OS. just skips a lot of potential problems.
I have heard that if you wanna upgrade ubuntu, run the upgrade halfway until it lists the packages that won't be upgraded. then remove those completely before attempting to run the upgrade again.

---

### Post by djyoung4 on 2009-09-23
ok so if i save my home directory and just do a clean install then make a separate partition for my home folder i will be able to just "load" all of my preferences or is there something else to it.

---

### Post by LowSky on 2009-09-23
yeah that will work. make sure to use the same user name, tings can get sloppy if you dont.

---

### Post by doas777 on 2009-09-23
nope, not really. 
most user config is stored in hidden files/folders in your user home. so if those files are present when it comes back up, it already knows your themes and wallpaper and panel layouts and whatnot. a lot of your apps run off configs in your user dot files as well.

---

### Post by djyoung4 on 2009-09-23
ok so this is my /home folder.  If i make this a separate partition on my next install then a majority of my preferences. (how my panels look.  what programs are installed, my themes,etc. etc.) will be able to work on 9.10.  sorry i am just a little confused as to how this works.  because couldn't i just copy the /home folder and save it over the new home folder that is made with the clean install.

---

### Post by doas777 on 2009-09-23
it won;t help with installed program but it will save everything else you mention. if your installed apps used config files in your home directory, then once you install them, they will retain your previous settings.

just FYI, the reason you want to create a new home partition on your rebuild, is so that next time, you don't have to do anything to back the data up. just format over the system drive but don't touch the home, and everything shoudl work out fine.

---

### Post by fluffman86 on 2009-09-23
I usually just copy/paste .ssh, .mozilla, and .tomboy to a thumbdrive.  My Music and Videos are already on my iPod and I just re-import them.  If you use Evolution, it has a backup function built in that you should use.

Then you can just to a full install like you did the first time you installed Ubuntu, and that will ensure you've fully upgraded to ext4, grub2, etc.

---

### Post by djyoung4 on 2009-09-23
so basically if i do a clean install then i will have to add all of the programs I want and how big should I make the home partition.  I have a 500 gb hard drive.  should I be saving everything into the home drive and just keep the system folders in a really small partition?  thanks for all the help though guys

---

### Post by fluffman86 on 2009-09-23
I set / to 20GB, and I'm only using 6gb...and I have a lot of programs installed.  The rest is /home and 1gb swap.  You'll want to have some / to spare though, because of your /tmp folder.  20GB is gracious plenty.  If you rip a lot of DVDs and install a lot of programs, 10GB may not give you enough /tmp.

---

### Post by djyoung4 on 2009-09-23
so breakdown of the 500 GB hard drive:

20 GB for /home
1gb for swap
the rest for data and stuff like that

I just would have to save all the programs to the home folder and it should be ok right?

---

### Post by doas777 on 2009-09-23
i would usually give ubuntu 10-20 GB (never needed more than 5 really), 5GB to swap, and whatever is left to the home, unless you wanna dual boot, in which case I would save 100GB or so for the other os. just remember that comes to 4 primary partitions, so you would not be able to subdivide the remaining 100GB any further.

---

### Post by djyoung4 on 2009-09-23
not dual booting.  im good with just ubuntu.  I just want to update when it comes to that and I want to make sure everything is ok.  My current swap is only a gig.  y do i need 5 gigs for it and what does the swap even do.

---

### Post by doas777 on 2009-09-23
> **djyoung4 said:**
> not dual booting.  im good with just ubuntu.  I just want to update when it comes to that and I want to make sure everything is ok.  My current swap is only a gig.  y do i need 5 gigs for it and what does the swap even do.

weoll to hibernate/suspend correctly you need at least the amount of ram you have available in your swap, free, so if you have swap in use, you need to account for that too. the traditional recomendation is 1.5X where X is your amount of ram. i prolly go overboard, but it's been a long time since i felt like that 5GB was missing/needed.

swap is like a pagefile in windows. Swap allows you to treat a peice of your hard disk as ram (kinda), and used to be called virtual memory or paging. Data in ram is arranged in Pages, but putting data in a page is an expensive operation. when you lack sufficient free ram, the system will take some of the ram pages off the chips and stores them on the disk, (but still in pages). if that page is needed the system pulls it off the swap drive and puts it back on the ram chips for access.

---

### Post by fluffman86 on 2009-09-23
Swap is the equivalent to the Windows page file.  If you run out of RAM, you computer starts using swap.  Opinions differ, but I've read that the "one and half times the RAM" rule was only valid up to 512MB of RAM or so, and having more than 1GB swap would hurt performance.  That could be wrong, though.  But if you have 2GB+ of RAM, you probably won't ever even need swap. :-\

---

### Post by doas777 on 2009-09-23
> **fluffman86 said:**
> Swap is the equivalent to the Windows page file.  If you run out of RAM, you computer starts using swap.  Opinions differ, but I've read that the "one and half times the RAM" rule was only valid up to 512MB of RAM or so, and having more than 1GB swap would hurt performance.  That could be wrong, though.  But if you have 2GB+ of RAM, you probably won't ever even need swap. :-\
unless you hibernate/suspend, I would agree with this entirely, save that, for a pagefile to hurt performance, it would have to me seriously used.

---

### Post by djyoung4 on 2009-09-24
ok so on my hp dv4 that i am using i have 4 gb of ram and 11 gigs of swap with the 9.04.  when i clean install i would want to have about 5 gigs of swap or is that too much

---

### Post by doas777 on 2009-09-24
> **djyoung4 said:**
> ok so on my hp dv4 that i am using i have 4 gb of ram and 11 gigs of swap with the 9.04.  when i clean install i would want to have about 5 gigs of swap or is that too much

5 sounds good to me. with 4GB you won't be paging all that much anyway.

---

### Post by djyoung4 on 2009-10-04
what about for my add ons for firefox.  is there a directory they are saved in or should i just write them all down and just re install all of them.

---

### Post by kendrick on 2009-10-08
I don't know if your add ons would be backed up when you back up your home directory....
but you could try a firefox add on called siphon which saves a list of the add ons you have and facilitates installing them again.

---

### Post by djyoung4 on 2009-10-10
ok that seems to be what i was looking for.  I just dont want to do a clean install of 9.10 and have to start over.  I finally just got my install how i want it and I want to update.  is suppose it will be good because it will give me a little project to do.  I have been playing with my conky too much  anyway.

---

### Post by louieb on 2009-10-10
> what about for my add ons for firefox.
there in ~/.mozilla/

Currently my laptop dual boots Jaunty and Karmic Beta. I'm getting Karmic setup the way I want. And if I break it I still have Jaunty to use. 

If your going to repartition for a home directory anyway  - might as well partition it to dual boot. lol - that will give you something to do.

---

### Post by djyoung4 on 2009-10-10
true.  ive done the dual boot thing before though.  I didn't like it.  don't ask me why.  I had xp and 9.04 and i got a new laptop and said screw it to windows after two days with vista.  god that OS is so bad.  i do have 7 coming to me though so maybe I could play with that.  its supposed to get here the day 9.10 comes out so I will have my hands full.  O well just back to making my conky awesome

---

