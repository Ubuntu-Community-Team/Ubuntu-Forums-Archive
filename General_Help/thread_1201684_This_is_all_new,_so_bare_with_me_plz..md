---
title: "This is all new, so bare with me plz."
date: 2009-07-01
forum: General Help
---

### Post by Pierre3400 on 2009-07-01
Hey guys n gals,

I heard about Ubuntu last night, and i figured i would try it out on one of my pc's, but before i do, i have a few questions.

The installation shouldn't be a problem, the pc is running 2x HDDs, one 20gb and one 100gb, the 100gb is a secondary drive where i have pictures, and movies and loads of other stuff stored that i dont want to lose. But as i have been runing Windows XP on the machine the 100gb is formatted in NTFS. The 20gb is only for running the pc, all i basicly use it for is for running OS, and what ever movie players i install on it. 

But my question is, will it be a problem that my 100gb will be running NTFS format? 
I heard something about it making Ubuntu run abit slower?

I would also like to know how well the movie players work on Ubuntu, or will i just need to get the useal programs i use (K-lite Codec packs/windows classic media player)?

I also use it for writing sometimes, and i use Office2007, how is this going to work on Ubuntu? 

Hope you bare over with me :)

Thnx

---

### Post by michy99 on 2009-07-01
The first thing you should do is download and burn an Ubuntu installation CD. Then you can boot from it and choose "Try it out without making changes to my computer." This will let you try Ubuntu without installing to your hard drive and you can see how well it will work with your system.

Ubuntu works great for playing movies, and there are also some good word processors like Open Office and Abi word.

---

### Post by zoomy942 on 2009-07-01
movies play great.  the first time you play one, ubuntu will auto serach out the required codecs and install them.  its a piece of cake.  i also agree with the above post that you should try the live cd first.  its a fully functioning system, running off a CD or thumbdrive, so you can have a no harm test of ubuntu.

as for typing..  openoffice works great, but if you have to use office 2007, i suggest Crossover Linux.  i use it and Office 2007 works perfectly

---

### Post by 3rdalbum on 2009-07-01
> **Pierre3400 said:**
> 

But my question is, will it be a problem that my 100gb will be running NTFS format? 
I heard something about it making Ubuntu run abit slower?

I'm not entirely clear on what you're asking; are you planning to install Ubuntu onto a disk that is currently formatted NTFS? Ubuntu will allow you to resize one of your partitions downwards, so it can create a partition of its own format.

If you're asking whether you can use an NTFS-formatted disk in Ubuntu as some sort of additional storage, the answer is yes. The speed of writing to NTFS will not be as fast as writing to a native Linux filesystem, but it will be acceptable for most uses. Merely having an NTFS-formatted disk mounted in Ubuntu will not slow the rest of the system down.

> I would also like to know how well the movie players work on Ubuntu, or will i just need to get the useal programs i use (K-lite Codec packs/windows classic media player)?

You'll be mostly leaving your Windows programs behind, on Ubuntu. If you enable the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org), instructions are there) and install the "non-free-codecs" package from Synaptic, this will install all the codecs you want or need. The codecs will work with Totem Media Player (the preinstalled video player on Ubuntu) but a lot of people prefer to install VLC.

Ubuntu doesn't really run Windows programs. There is a program called Wine that can run some Windows programs, but don't have high expectations of it's compatibility, you'll be disappointed. Try and seek out Linux alternatives wherever possible; if not possible, then try Wine.

> I also use it for writing sometimes, and i use Office2007, how is this going to work on Ubuntu? 

Reports tend to suggest that it works with Wine. I know that Microsoft Office and Adobe Photoshop compatibility tend to be the main targets for Wine compatibility.

Openoffice.org is preinstalled on Ubuntu, you might want to try that. It doesn't have the "ribbon" interface or the most advanced 2% of MS Office features, but for someone who uses it for "writing sometimes" you should be fine with Ooo.

---

### Post by Idefix82 on 2009-07-01
Maybe this is superfluous but I will clarify some of what 3rdalbum said.

If you want to install Ubuntu, it needs its own partition. A partition is a piece of the hard drive that 'pretends' to be a separate hard drive. At the moment, my guess is that each of your two hard drives has one partition. Once you decide, which hard drive you want to install Ubuntu on, you will have to resize the corresponding partition and ask Ubuntu to install itself into the space that becomes available.

Now for resizing: to minimise the risk of loss of data, you should first defragment the partition that you want to resize a few times. Then you have two options: if you have a tool for partition management under Windows then you should use that to resize the partition. Otherwise you can ask Ubuntu to do that once you start installing.

---

### Post by Pierre3400 on 2009-07-01
Thanks for all the response :)

I have already downloaded Ubuntu and burned it on to a CD.

Yes i have been running XP on the pc im going to try Ubuntu on, but i recently made a few hardware changes and never bothered to setup XP with the changes, cos i dont use the pc much, its hooked up to my tv, and i use it for movies and such, but it use to be my main pc, so i have 5gb of pics from that past 10years, and such, that i wish to save. 

But Basically what my plan is, is to unplug my 100gb, and then run a format of the 20gb, and do a full fresh install of Ubuntu. I have tryed to use Linux based OS before, but i was not succesfull back then (about 8years ago) I gave up, and stuck with Windows, but sounds like Ubuntu is easy to use.

Just to clearify, im not a total lost cause when it comes to pc's, but i stopped caring much about then a few years ago, before that i was into, overclocking, watercooling and , 3D mark and all that. So you dont need to dumb it down to average PC user level, im abit above. 

When it comes to partition is dont care, as i said, fresh install, its getting its own harddisk. My only concern was more of a, will the movies lag cos they are stored on NTFS hdd. How slow are we talking compared with Linux formats? Couple of seconds og 30secs? 1min?

---

### Post by jmszr on 2009-07-01
Pierre3400,

You might wish to try Wubi: [http://wubi-installer.org/](http://wubi-installer.org/) this installs Ubuntu wihin Windows and can be removed through Windows Add/Remove. No partioning necessary. This link will provide guidance: [http://psychocats.net/ubuntu/wubi](http://psychocats.net/ubuntu/wubi) . Please read all of psychocats as it has a lot of excellent information. If you decide to dual-boot (preferable) the psychocats guide and this: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) will give you good advice. 

_Always_ back up your data before partitioning!

Edit: Hadn't read your latest post yet. I would recommend having a separate /home partition for ease of later Ubuntu upgrade. You should have no problems with movie speed, you will need to install (easy) ntfs-3g for ntfs read/write access.

---

### Post by Pierre3400 on 2009-07-01
> **jmszr said:**
> Pierre3400,

You might wish to try Wubi: [http://wubi-installer.org/](http://wubi-installer.org/) this installs Ubuntu wihin Windows and can be removed through Windowa Add/Remove. No partioning necessary. This link will provide guidabce: [http://psychocats.net/ubuntu/wubi](http://psychocats.net/ubuntu/wubi) . Please read all of psychocats as it has a lot of excellent information. If you decide to dual-boot (preferable) the psychocats guide and this: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) will give you good advice. 

_Always_ back up you data before partitioning!

Thanks, will read it, but i got nothing apart from the OS on the HDD im plaing on useing, so im not scared, and if all fails i have en extra 20gb somewhere :P

---

### Post by Idefix82 on 2009-07-01
> **Pierre3400 said:**
> you dont need to dumb it down to average PC user level, im abit above. 


Sorry, I didn't want to be patronising.

> **Pierre3400 said:**
> How slow are we talking compared with Linux formats? Couple of seconds og 30secs? 1min?

I think it shouldn't be more than fractions but why don't you just try it out. If the lag is too great, then create an ext3 partition on the 100 GB hard drive, copy your movies there, then delete the ntfs partition and increase the ext3 to occupy the whole disc.

One more thing: don't unplug the 100GB hard drive when you install Ubuntu. Its presence will not disturb the installation, as long as you don't accidentally choose that as the installation hd.

---

### Post by Pierre3400 on 2009-07-01
> **Idefix82 said:**
> Sorry, I didn't want to be patronising.



I think it shouldn't be more than fractions but why don't you just try it out. If the lag is too great, then create an ext3 partition on the 100 GB hard drive, copy your movies there, then delete the ntfs partition and increase the ext3 to occupy the whole disc.

One more thing: don't unplug the 100GB hard drive when you install Ubuntu. Its presence will not disturb the installation, as long as you don't accidentally choose that as the installation hd.

Will it make a big difference if its unplugged?

Another question, will Ubuntu be able to work with my vista laptop, over network, cos i use my laptop mostly, being that its the fastest machine i got. But i store big things on the other pc. Just wondering if they can talk together over a netwrok?

---

### Post by Pierre3400 on 2009-07-01
Right guys, som im trying to install Ubuntu, i boot the cd, it comes in right away to the menu where you can choose, try ubunto without making changes, and the others. I chose Ubuntu Install. It moves on and then comes to a screen that looks like dos, and this is where i gotta admit, im stuck. I dont understand what i have to write?

---

### Post by Idefix82 on 2009-07-01
Are you sure you have downloaded the Desktop edition and not the server edition? The desktop edition of Ubuntu should give you a graphical and very easy to follow installer. Also, you might want to check the MD5 sum on the burnt image to make sure that the CD is not corrupt.

---

### Post by jmszr on 2009-07-01
Pierre3400,

This may be of help: [https://answers.launchpad.net/ubuntu/+question/27647](https://answers.launchpad.net/ubuntu/+question/27647) .
Perhaps this also: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Pierre3400 on 2009-07-01
> **Idefix82 said:**
> Are you sure you have downloaded the Desktop edition and not the server edition? The desktop edition of Ubuntu should give you a graphical and very easy to follow installer. Also, you might want to check the MD5 sum on the burnt image to make sure that the CD is not corrupt.

Yeh, i got the 9.04 Desktop for 32bit.

When i boot up the pc, it boots into a nice graphic state, i choose Install Ubuntu, its then says Ubuntu, and the yellow dot scans back an forth in the red line.

Then i goes into its "dos look" mode (part of the screen i cant see, dunni why?) but at the the top it says:

Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter "help" for at list of built-in commands

Xinteramfs) _

The x is cos i cant make out what it says.

Its does this even if i choose Try it without making changes. When i type help it gets real confusing. I have to admit i use to be pretty good with Dos, but this is just confusing beyond anything, the commands are just in a row, with no idea what they do?

---

### Post by Idefix82 on 2009-07-01
Have you checked [the MD5 sum]("https://help.ubuntu.com/community/HowToMD5SUM")?

You might want to try to just burn the image again. Make sure to burn it at minimum speed and do the integrity check as explained in the link.

---

### Post by michy99 on 2009-07-01
How much ram does this computer have? If it is less then 256 Meg, you will have to use the alternative cd.

---

### Post by Pierre3400 on 2009-07-01
Im running 2x512mb, so should be plenty.

The disk was burned at 12x, but ill try 8x tomorrow. 

But thanx so far guys, i'll read up on all the links and so on during the night as i got work then, and nothing to do at work. Then tomorrow, we try all over again.

---

### Post by zoomy942 on 2009-07-02
> **Idefix82 said:**
> Have you checked [the MD5 sum]("https://help.ubuntu.com/community/HowToMD5SUM")?

You might want to try to just burn the image again. Make sure to burn it at minimum speed and do the integrity check as explained in the link.

agreed.  check on that.  sounds like x isnt starting right.  if you cant get the install to begin, you dont want to force it then have a botched install

---

### Post by Pierre3400 on 2009-07-02
Right guys, i burnt ubuntu once more 2day, at 8x, and now im getting the graphics u all talked about. So far so good. I noticed that when i mounted the cd, in my laptop it would say it was a blank cd, but i would boot the start menu on the other pc, but once in windows, empty once more, so i think the cd was the problem.

Thnx for all ur help so far!

---

