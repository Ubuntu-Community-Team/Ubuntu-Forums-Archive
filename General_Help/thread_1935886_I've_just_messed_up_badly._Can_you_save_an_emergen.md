---
title: "I've just messed up badly. Can you save an emergency?"
date: 2012-03-05
forum: General Help
---

### Post by Hikayu on 2012-03-05
> Hello, ubuntuforums. I hate to start on a depressive note, but last time I asked for assistance here... nevermind.

You see, due to my own inaptitude, I've somehow caused an absolute downfall by trying to install .deb packages off [http://packages.debian.org/sid/](http://packages.debian.org/sid/) . Stupid, huh?

Well, last useful thing I tried to do was install FlightGear. I installed it off Ubuntu's Software Center. It bugged up after a few minutes, very significantly, to the point where it was persistently unplayable because the in-game system just kept failing with numerous bugs and things that wouldn't have support or take inconsiderable effort to hunt and fix. I checked the version I installed by chance and noted it to be version 2.0.0-3. The latest version on flightgear.org happens to be 2.6.0.1. That's rather far-fetched, really, because 2.0.0-3 was released some time in early 2010. So, I tried compiling from source using packages from debian sid because they were up to date, where my repo wasn't. Ah, so the latest version should be better for me, I foolishly thought.

Now gcc has gone to /dev/null heaven, because I just press yes to everything and the dependencies have become an tangled mess and, following that, my nVidia drivers have been disabled and I can't install back the default gcc-4.5 without removing half of every package installed on my distro. Heck, apt-get even tells me if "I'm very sure about this" and to type "Yes, I am" instead of typing "y" because of its Doomsday potential. Whatdo?

This would've been my subtle rage post.

Then I realize while searching for inconsistencies that it was my own ignorance that got me into this mess. I did everything wrong from the start. Because I was a Linux noob who didn't know how to configure *synaptic* properly. Now everything seems so very lost.

I checked out the repositories for precise pangolin and found out they had all the packages I needed to compile FlightGear 2.6 *and* the complete package prebuilt for FlightGear 2.4. I could've been *very* satisfied with that. All I wanted was to fly a bug-free Cessna172 plane around in circles ;(

So it was my own incompetence that got me into this mess. The most viable solution right now seems to be to reinstall Ubuntu. That's a Very Bad solution. I don't want to spend 4 hours doing that and the volatile backing up associated with that. Please, faith. I even had a friend that coincidentally stole my only 2GB pen-drive for fun. And I live in a cardboard box with nothing else to use. My disk drive is kaput and I don't have any blank disks to burn a liveCD anyway.

Can you show a misfortunate scoundrel some pity and point me in the right direction? I'm sure you've felt the stress when you mess up your Linux distro because you've misused your sudo powers and ended up having to start with a blank slate. This is the third time I've gone through that, and it's very demotivating to use Ubuntu now. It's stressful; you will always have very little help with it because it's always a very specific issue that no one else has a clue about... or anyone willing to contribute has a clue about.

I know I sound ungrateful, because the last time I asked for technical issues here was responded with people who knew about as much as me, very little. The IRC channels are filled with gurus that take centuries to write a sophisticated response that gives me migraines trying to decipher. The interface and mono-space characters also have this migraine factor about them. This is such a last-resort measure I'm taking.

Edit: The following packages I installed from Debian Sid were: libboost1.46-dev_1.46.1-8, libicu48_4.8.1.1-3, libstdc++6_4.6.3-1, gcc-4.6-base_4.6.3-1

I know one of them caused some huge deliberate intricate messed up depending loop that has stopped me from installing core packages. What can I do to reverse this brouhaha?

---

### Post by Hikayu on 2012-03-06
A'ight, turns out there's not much I could do. In fact, there was nothing I could do. I restarted my computer an hour after starting this thread. It could not get past the boot screen. Fortunately, GRUB still starts up fine. But I believe it has reached the point where any effort I put into recovering Ubuntu will take more effort than installing Linux Mint and taking any data left over on the old partition. Seeing no one really posted, I'll just write down what I do. If anyone's interested and find out that I'm about to make a grave error, just tell me so that I don't send my PC to critical condition.

Right now I have only one partition: /dev/sda1. This contains the messed up Ubuntu Partition. It also contains the Linux Mint iso on my Desktop directory. Jolly good. And remember that stolen thumbdrive? Got it back. 'Negotiation'. Good, so I have an Ubuntu liveUSB, which I am, in fact, using right now to write here. So, I resize /dev/sda1, originally encompassing the entire HD, until there's only 5 GB of free space left on it, and I'm going to install a second copy of Ubuntu in the remaining free space, approx. 50GB.

---

### Post by techvish81 on 2012-03-06
you can remove those problematic packages by booting through recovery and using console.

---

### Post by Hikayu on 2012-03-06
> **techvish81 said:**
> you can remove those problematic packages by booting through recovery and using console.

It wouldn't work. I wouldn't have to cope with any problem if a problematic package was what I was dealing with. The problem at hand was that all the core packages I had were linked to the wrong thing. Now reinstalling the default would result in the removal of half of the default packages and reinstalling them -- I don't want that.

So, I have installed Linux Mint on a small partition. I can handle only so much from here on out, but one thing I'm concerned with is:
What happens if I delete the first partition of the HDD? Will this mess up the MBR and cause problems booting?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-06
You can also use Live CD or a USB install of Ubuntu to get data back. Id you have another computer available to create them, that is.

More info here under number 2:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by Bucky Ball on 2012-03-06
I would boot from a live CD, backup any valuable data you have on there to somewhere safe (preferably an external device) and start again. Wipe the drive, make a plan, install. The thought of fishing through the mud of your current situation is giving me a migraine!

Partitions;

/ = 20Gb plenty;
/home =large as you like;
/swap = 2Gb fine;

... are advisable. Having your data on a separate /home partition means if you ever need to reinstall again you can just kill the / partition and reinstall Ubuntu there, leaving all your personal data in /home (make sure /home is not marked to format during install but / is). 

Good luck. ;)

---

### Post by Hikayu on 2012-03-06
> **&#1058 said:**
> You can also use Live CD or a USB install of Ubuntu to get data back. Id you have another computer available to create them, that is.

More info here under number 2:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I appreciate the effort, but I've already stated I knew how to handle this, having gone through this three times already. I know I am quite too detailed when it comes to giving an account of what happened, so it's alright that you missed it out.

> 
I would boot from a live CD, backup any valuable data you have on there to somewhere safe (preferably an external device) and start again. Wipe the drive, make a plan, install. The thought of fishing through the mud of your current situation is giving me a migraine!

Partitions;

/ = 20Gb plenty;
/home =large as you like;
/swap = 2Gb fine;

... are advisable. Having your data on a separate /home partition means if you ever need to reinstall again you can just kill the / partition and reinstall Ubuntu there, leaving all your personal data in /home (make sure /home is not marked to format during install but / is).

Good luck.


Thanks for your sympathy, but I can handle it... superfluously. Make a small partition, install temp OS, install new OS, copy config files, copy data files, reinstall some core packages, delete old partition, expand original partition, reconfigure GRUB

Yea, I've been through the drill a bit too many times for my own liking. :popcorn:

> What happens if I delete the first partition of the HDD? Will this mess up the MBR and cause problems booting? 

This question is my only concern right now.

Also, here's another question to prevent repeating that pathetic problem that resulted in my initial problem: How do I reconfigure synaptic to take packages from [http://packages.ubuntu.com/precise/](http://packages.ubuntu.com/precise/) only?

---

### Post by Hikayu on 2012-03-06
> Also, here's another question to prevent repeating that pathetic problem that resulted in my initial problem: How do I reconfigure synaptic to take packages from [http://packages.ubuntu.com/precise/](http://packages.ubuntu.com/precise/) only? 

Ah, how silly of me. Software Sources > Add APT line "deb [http://packages.ubuntu.com/](http://packages.ubuntu.com/) precise main"

Other problem still needs answering though.

EDIT: NO, sorry. I've just realized that precise pangolin's repositories are still not meant to be used with synaptic. I'll have to get each deb manually then. I'll just be twice as careful not to cause the same ruckus.

---

### Post by Bucky Ball on 2012-03-06
You will delete the MBR if it is on the partition you delete, obviously. 

You will install grub when you install Ubuntu, but grub doesn't need to be installed to the first partition. You get a choice. It can be installed anywhere; the partition you are installing Ubuntu in is a good start.

---

