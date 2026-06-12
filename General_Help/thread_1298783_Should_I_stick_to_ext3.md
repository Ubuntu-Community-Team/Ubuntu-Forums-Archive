---
title: "Should I stick to ext3?"
date: 2009-10-23
forum: General Help
---

### Post by arnab_das on 2009-10-23
Karmic's coming out next week, so am excited. however what dampened my spirits was the fact that karmic now has support for etx4. now thats supposed to be better than ext3, isnt it? except that i dont think i am in a position to format my hard drive right now. however i heard someone saying on this forum that ext4 is quite unstable and in beta. is that true? Is ext4 worth all the hype? or is ext3 the safer way out at this stage?

---

### Post by kellemes on 2009-10-23
Using ext4 for some time now, never had any trouble..
Not sure if it's faster in my case. But maybe others notice better performance.

---

### Post by Mawoon on 2009-10-23
I haven't noticed any differences since I switched to Karmic, I noticed the nautilus opens faster though, in 9.04 I had a little delay, here that delay is less, but I think it's the new nvidia driver that covers that.

One thing I noticed though, unmounting external drives is WAY faster, if that's a help

---

### Post by lovinglinux on 2009-10-23
I have been using ext4 on all my partitions since the release of Jaunty and it has been stable for me. No problems whatsoever and there is indeed a performance boost when switching from ext3 to ext4.

When Jaunty was released there were some issues that could result in data loss after a power failure, system crash, excessive disk activity or when moving/resizing partitions. I have experienced all of those scenarios without any data loss, but other users reported the opposite. Anyway, this has been fixed in the latest kernel versions, otherwise they wouldn't make it default in Karmic.

Bottom line. Go for it.

---

### Post by doomsword2001 on 2009-10-23
been using ext4 for a while no problems at all, i think also in karmic ext4 is the default so it should be ok

---

### Post by tarps87 on 2009-10-23
I have not had any problems so far, been using it since Jan on my Arch system and since Jaunty on my desktop. Including improper shutdown when my battery went flat without power management setup

---

### Post by arnab_das on 2009-10-23
thanks for ur responses. looks like i'll have to do the format.

btw, if i "mark" the softwares from synaptic and then install it from the saved/marked file after i have installed karmic, would it work well? coz many softwares might change versions with karmic isnt it?

---

### Post by P4man on 2009-10-23
First of all, jaunty supports Ext4 as well. Its not new to Karmic, the only difference is that by default Karmic uses ext4, but you could manually select Ext4 with jaunty just as well.

> **arnab_das said:**
> 
btw, if i "mark" the softwares from synaptic and then install it from the saved/marked file after i have installed karmic, would it work well? coz many softwares might change versions with karmic isnt it?

I guess it will work for the most part, since apt will take care of any changed dependencies. If anything I guess you may end up with some packages you no longer really need, but I don think it would break anything.

---

### Post by lovinglinux on 2009-10-23
> **arnab_das said:**
> thanks for ur responses. looks like i'll have to do the format.

btw, if i "mark" the softwares from synaptic and then install it from the saved/marked file after i have installed karmic, would it work well?

Make sure you use "Save Markings As" and tick the option "Save full state, not only markings", otherwise it won't save anything. You can use my Umarks extension to make more than one backup of your markings. More info [here](http://ubuntuforums.org/showpost.php?p=8113316&postcount=3).

> **arnab_das said:**
> coz many softwares might change versions with karmic isnt it?

This question has been bothering me for a while :) I'm not sure how it would behave, but as far as I know, if you are upgrading from Jaunty to Karmic, then most of the old packages should have dummies pointing to the new ones. For example, firefox-3.0 package is a dummy for installing firefox-3.5 in Karmic. So when you import your markings that have firefox-3.0 you will end up with firefox-3.5 instead. 

Nevertheless, I have decided to start from fresh with Karmic, without importing my markings, because I probably installed a lot of stuff in Jaunty that I won't need in Karmic. Now I'm logging every single package I install and it's dependencies, so I can better control what I will need when 10.04 comes out.

---

### Post by aromo on 2009-10-23
> **lovinglinux said:**
> 
Nevertheless, I have decided to start from fresh with Karmic, without importing my markings, because I probably installed a lot of stuff in Jaunty that I won't need in Karmic. Now I'm logging every single package I install and it's dependencies, so I can better control what I will need when 10.04 comes out.

This is a good idea!

In regards to the original question, I have 2 laptops with exactly the same hardware running Jaunty.  Mine is ext4, my wife's is ext3 and we've had no problems at all or noticeable difference in terms of performance (we both are light users).  So, if you don't want to install fresh you might as well stick with ext3.  But if you do, go for ext4.

My 2 cents.  :guitar:

---

### Post by arnab_das on 2009-10-23
if i format right now and reinstall jaunty with ext4, can i continue using karmic in the same format or will ext4 of karmic change by the time it releases? is this a good idea?

btw what do u think of this: [http://webupd8.blogspot.com/2009/04/convert-your-ext3-file-system-to-ext4.html](http://webupd8.blogspot.com/2009/04/convert-your-ext3-file-system-to-ext4.html)

---

### Post by kimda on 2009-10-23
Why not install Karmic instead of Jaunty? (next week it will be released) Also if you install Karmic you can use encrypted home dir and swap. I would not install ext4 on Jaunty! If you have the wrong kernel it will eat your data. Not kidding. I've done both conversions and fresh. I would recommend fresh instead of conversion. Because only newly created files will have the extends function of ext4.

---

### Post by tarps87 on 2009-10-23
> **kimda said:**
> Why not install Karmic instead of Jaunty? (next week it will be released) Also if you install Karmic you can use encrypted home dir and swap. I would not install ext4 on Jaunty! If you have the wrong kernel it will eat your data. Not kidding. I've done both conversions and fresh. I would recommend fresh instead of conversion. Because only newly created files will have the extends function of ext4.

You can use an encrypted home dir in Jaunty, also ext4 is supported in Jaunty it's just not set as the default format.
I would recommend waiting as it will probably save you time and you wont have to install grub2 separately.
The files do not new to be newly created so to speak, you can achieve the same effect by modifying (re-saving) or moving the files. I presume you mean the extents feature.

---

### Post by asdir on 2009-10-26
One thing that would maybe keep me from using ext4 is that some (all?) Windows-drivers for ext2/3 do not work with ext4 yet. So, in a dual-boot setup I could not access my ext4 drive from Windows, which would be a shame.

On that note: It is still possible to install ext3 instead of ext4 with simply setting a tick/dropdown menu/whatever, right?

See [here]("http://ubuntuforums.org/showthread.php?t=1145598&page=3") for a discussion of methods for accessing ext4 through windows. Looks grim, though.

---

### Post by sarin_cv on 2009-10-26
I have created a separate partition for home. When I install Karmic, I don't  want to lose all my data in that directory. Can I convert the file system to ext4 without losing data?  

Anyways I will be formatting the root partition. I can get all the applications back by taking backup of /var/apt/cache/archives right?

---

### Post by lovinglinux on 2009-10-26
> **sarin_cv said:**
> I have created a separate partition for home. When I install Karmic, I don't  want to lose all my data in that directory. Can I convert the file system to ext4 without losing data? 

There is a conversion method, but I never tried it. I would recommend a backup tho.

> **sarin_cv said:**
> Anyways I will be formatting the root partition. I can get all the applications back by taking backup of /var/apt/cache/archives right?

To get  all your applications back see [http://ubuntuforums.org/showpost.php?p=8113316&postcount=3](http://ubuntuforums.org/showpost.php?p=8113316&postcount=3)

---

### Post by khelben1979 on 2009-10-26
Depends on your kernel version. I have chosen to stick with ext3 because of my kernel version (2.6.26) which is standard in Debian Lenny. Newer kernels offer better stability where you actually need to be prepared for data loss otherwise.

I know there's a possibility to mount the [ext3]("http://en.wikipedia.org/wiki/Ext3") partitions as [ext4]("http://en.wikipedia.org/wiki/Ext4") as the filesystem is compatible from what I've read. I haven't tried it myself and as someone else stated in this thread: do backup first, always be prepared for the worst.

---

### Post by pveurshout on 2009-10-26
> **khelben1979 said:**
> I know there's a possibility to mount the [ext3]("http://en.wikipedia.org/wiki/Ext3") partitions as [ext4]("http://en.wikipedia.org/wiki/Ext4") as the filesystem is compatible from what I've read. I haven't tried it myself and as someone else stated in this thread: do backup first, always be prepared for the worst.

Perhaps this is a stupid question, but just to be sure: I'm currently using a separate partition for my media files (Ext3). Can I simply mount&use it (as Ext3) in Karmic if I create an Ext4-partition for Karmic, or will I end up risking data loss because it, for instance, automatically mounts it as Ext4 because it's on Ext4 itself?

---

### Post by khelben1979 on 2009-10-26
I think it's safer to mount ext3 partitions as ext4 than the other way around. Then again, I have never tried it myself.

---

