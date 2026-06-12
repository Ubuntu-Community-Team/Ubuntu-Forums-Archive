---
title: "Complete Switch"
date: 2009-08-05
forum: General Help
---

### Post by dino1515 on 2009-08-05
I have been using Ubuntu as a dual boot with Vista now for a few weeks and having been a Windows user beforehand I absolutely love Ubuntu.
The reason for my switch to Linux is that I was fed up with constant crashes and overall slowness of Vista.

Anyway I wish to switch permanently to Ubuntu but I am being held back by one major thing and one minor thing. The minor thing is games which I can live without. The major thing is my iPhone which I always sync and use.

Does anyone know anyway around this because I would love to get Vista off my computer because even with the dual boot it is hogging a lot of hard drive space.

---

### Post by soapBAR2 on 2009-08-05
Unfortunately, Apple seems to despise linux, and will not put linux drivers out for anything (if I had a nickel for every problem I've had with my iPod..). If your problem is the stability/speed of Vista, you could always switch to Linux and install Vista in a virtual machine (VirtualBox is good - 

```
sudo apt-get install virtualbox-ose
``` )

Or better yet, install XP in a virtual machine. From what I've heard, Microsoft were offering a downgrade option for Vista users.

Or, you could give WINE a go - but don't count on it working, it's extremely flaky, especially for drivers.

---

### Post by ithanium on 2009-08-05
The iPhone part will always remain a problem. You can try using VirtualBox to sync you iPhone from a Virtual Windows Xp which is running inside Ubuntu without the need of a restart!

---

### Post by 3rdalbum on 2009-08-05
You won't be able to directly use any USB device with the open-source edition of Virtualbox. Better off to go to virtualbox.org and look at their downloads page - they have a repository for the closed-source edition, that supports USB passthrough.

---

### Post by dino1515 on 2009-08-05
The virtualbox idea seems good, does anyone know how exactly to get this to work, I am fairly new at this sort of thing and could use all the help i can get!

---

### Post by hibliss on 2009-08-05
I suggest in the future that you boycott Apple products.

They have a Unix based OS that they put on decent machines and then rape customers for every dime possible, but they can't port iTunes to another Unix-like OS?

They took plenty of time to design iTunes for Windows (and it sucks of course).

Instead of finding a workaround, solve the problem by avoiding their products, we all should.

---

### Post by scouser73 on 2009-08-05
I'm not an iPhone user so I can't say this is fact but I think the media player Songbird offers iPhone/iPod compatibility, perhaps it's worth having a look. [[COLOR="Red"]**Songbird**[/COLOR]]("http://getsongbird.com/")

---

### Post by hibliss on 2009-08-05
> **scouser73 said:**
> I'm not an iPhone user so I can't say this is fact but I think the media player Songbird offers iPhone/iPod compatibility, perhaps it's worth having a look. [[COLOR="Red"]**Songbird**[/COLOR]]("http://getsongbird.com/")

ipod yes, not so sure about the iphone.

Check out this page -- [https://help.ubuntu.com/community/PortableDevices/iPod]("https://help.ubuntu.com/community/PortableDevices/iPod")

It says you have to jailbreak it in order to SSH in to the iPhone due to it not showing up as removable storage.

---

### Post by Chrisj303 on 2009-08-07
> **hibliss said:**
> I suggest in the future that you boycott Apple products.

They have a Unix based OS that they put on decent machines and then rape customers for every dime possible, but they can't port iTunes to another Unix-like OS?

They took plenty of time to design iTunes for Windows (and it sucks of course).

Instead of finding a workaround, solve the problem by avoiding their products, we all should.

Thats all well and good.

BUT please tell me the names of Linux software that *honestly* as good as;

Final Cut Studio.
Logic Pro.
Ableton Live.
Motion.

I've been using Ubuntu for years (as well as OS X and Windows) - and haven't found a "soloution" that hasn't been laughably bad.

BTW - we've met before ;-)

---

### Post by hibliss on 2009-08-07
> **Chrisj303 said:**
> Thats all well and good.

BUT please tell me the names of Linux software that *honestly* as good as;

Final Cut Studio.
Logic Pro.
Ableton Live.
Motion.

I've been using Ubuntu for years (as well as OS X and Windows) - and haven't found a "soloution" that hasn't been laughably bad.

BTW - we've met before ;-)

I hear you on the software. I actually agree. While I am not the biggest Apple fan, or MS fan, Apple clearly wins out there. 

When it comes to MP3/Video players though, there are much more Linux friendly solutions. I will amend my statement to say you should boycott Apple products that you plan to use in Linux. I just don't understand why they would make something less Linux friendly over time:-k

---

### Post by P4man on 2009-08-07
For the iPhone have a look here:
[https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x](https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x)

---

