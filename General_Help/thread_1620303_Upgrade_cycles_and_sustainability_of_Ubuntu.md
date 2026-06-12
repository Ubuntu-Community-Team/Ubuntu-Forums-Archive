---
title: "Upgrade cycles and sustainability of Ubuntu"
date: 2010-11-12
forum: General Help
---

### Post by bluelightav on 2010-11-12
Dear Ubuntu community,

Blue Light are a bunch of open source enthusiasts in Auroville, south India. During the last 2 years we migrated 70 computer systems in offices, kindergartens, schools etc. in our community services starting with Hardy. When Lucid came out we faced an unexpected challenge that made us reflect a bit how to use software.
The main concern is that in a developing country like India computers are still very expensive and most computers have to be used as Desktops computers while they at the same time run server software.
An update cycle of 2-3 years for LTS seems on one hand needed as soft- and hardware develops fast these days. On the other hand a 5 years server update looks pretty good to us but we can't use server editions as users have to work on these machines, too.
Then there is another very important aspect. OpenOffice, Thunderbird and Firefox being the main applications in an office environment don't upgrade fast enough on LTS versions and it was a pain to see TB, FF and OOo 2 versions on Hardy while the users on Karmic for example enjoyed already the much better 3 versions.
Then we were faced upgrading 70 computers. That kept us busy for many, many hours. It was not just an upgrade from Hardy to Lucid. Changing the file system from Ext3 or Raiser to Ext4 required new installations. The old home directories (from Hardy) often caused lots of problems in the new Lucid Gnome environment so we had to be much more selective which folders to use on Lucid. Many Desktop settings got lost.
The outlook that in one year we have to go through a similar process with an ever increasing number of migrated computers is not very appealing and we are wondering if other people have similar experiences and might have already have solutions.
Is a 3 /5 years update cycle feasible form the point of maintaining systems? If you earn money with it it might good but what if you don't? What if like we in Blue Light the work is internal? How many more computers can one put on Ubuntu if this massive upgrade event hits every 2 years?
Being XP what it is, one aspect was pretty good: 10 years of XP without any changes (don't comment on all the disadvantages - I am aware of most of them)  and all hardware kept on working on it and applications could be upgraded easily. 
What is a sustainable solution for Ubuntu (Linux)?

I invite everybody to post their feedback and experiences

---

### Post by dcstar on 2010-11-12
> **bluelightav said:**
> 
..........
I invite everybody to post their feedback and experiences

**Not here**, this forum is specifically for:

*All your **general support questions** for Ubuntu, Kubuntu, Edubuntu and Xubuntu*

Find a more appropriate forum for other things.

---

### Post by Dex73 on 2010-11-12
> **bluelightav said:**
> 

It was not just an upgrade from Hardy to Lucid. Changing the file system from Ext3 or Raiser to Ext4 required new installations. The old home directories (from Hardy) often caused lots of problems in the new Lucid Gnome environment so we had to be much more selective which folders to use on Lucid. Many Desktop settings got lost.


If your talking about very specific settings, what I tend to do is take a screen shot of what I have setup and since I know enough about Ubuntu, I can recreate it quickly.

Perhaps a sync system interlaced with a program that seeks to copy what is there (not just GUI but all settings). Then save that data somewhere on an internet server or on a CD/flash-drive/whatever and then open it on that same program on the new install.

Obviously not every thing would be compatible, but a lot of it could then be replicated and then anything that the computer detects is different would appear in a list that is then presented to the user.

This could even be done before the install to show what the main issues would be. Like an automated Ubuntu Live session. With a system set up not for file conversion but file reconstruction using a new system.

The more I do it manually, the more I realize, that automation is the way to go for this task. Something that runs all night and solves the problem. I'm not super experienced with Ubuntu, but I took a crack at it.

---

### Post by bluelightav on 2010-11-14
> **dcstar said:**
> **Not here**, this forum is specifically for:

*All your **general support questions** for Ubuntu, Kubuntu, Edubuntu and Xubuntu*

Find a more appropriate forum for other things.

From my point of view this is a general support question. I checked all the places available and this one is the most appropriate for me.

---

### Post by bluelightav on 2010-11-14
> **Dex73 said:**
> If your talking about very specific settings, what I tend to do is take a screen shot of what I have setup and since I know enough about Ubuntu, I can recreate it quickly.

Perhaps a sync system interlaced with a program that seeks to copy what is there (not just GUI but all settings). Then save that data somewhere on an internet server or on a CD/flash-drive/whatever and then open it on that same program on the new install.

Obviously not every thing would be compatible, but a lot of it could then be replicated and then anything that the computer detects is different would appear in a list that is then presented to the user.

This could even be done before the install to show what the main issues would be. Like an automated Ubuntu Live session. With a system set up not for file conversion but file reconstruction using a new system.

The more I do it manually, the more I realize, that automation is the way to go for this task. Something that runs all night and solves the problem. I'm not super experienced with Ubuntu, but I took a crack at it.

Presently we are working with this tool which looks already very promising.
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by bluelightav on 2010-11-14
The other thought we had was to use an Ubuntu server edition and put an Ubuntu Gnome Desktop on top. Does anybody have experience with this? Is it recommended or are there some real drawbacks with this solution. That way the upgrade cycle could be pushed 2 years further away which is something more feasible for us.

---

### Post by bluelightav on 2010-12-10
Have a look at this post as well. We are experimenting a bit :-)
[http://forums.linuxmint.com/viewtopic.php?f=141&t=61663](http://forums.linuxmint.com/viewtopic.php?f=141&t=61663)

---

### Post by mastablasta on 2010-12-10
a roling distro is ok if oyu can support it. note that even Linix Mint is currently still not using testing releases which i think it will later on. and things can go donwhill in stability then.
 
you could go maybe Debian (or stay with Ubuntu) and then just upgrade the programmes with PPA's. Then only upgrade those that really mean a change to the people using them. i mean often the differences are rather small. sometimes they birng new much needed fixes and features. otherwise they just bring new features that are not really necessary.
 
take Skype for instance. Linux version looks a lot different than windows ones. I just upgraded windows version from 3 to 5 and i know it has more new features, it's just i dont' use them anyway. so i might have just stayed with version 3. just as i am not bothered by the way linux verison looks like. as long as it works....

---

### Post by bluelightav on 2010-12-10
> **mastablasta said:**
> a roling distro is ok if oyu can support it. note that even Linix Mint is currently still not using testing releases which i think it will later on. and things can go donwhill in stability then.


I think this is the way to go: Find a balance between stability and features. In our offices we don't ned the latest everything but to work under Hardy OOo 2.1 and TB 2 when the versions 3 are out since long and bring needed improvement and features. PPA are good but for example in FF and TB they don't work. They disable all plug-ins and don;t integrate well into the system. As I said - it doesn't need tobe too new but to upgrade every 2 years a whole system eventually creates way more work than we can handle in our set-up.

---

### Post by seanbw on 2011-02-07
You may want to look at the bitnami.org approach. [http://bitnami.org/stack/lampstack](http://bitnami.org/stack/lampstack) and adopt a Linux/Windows structure. OS, Application and Data. OS is upgraded as and when you think its necessary. Applications to be updated by the std update manager while data stays the same. This way, you split the roles and responsibilities between all of you. I know that the internet technology in developing countries are not as advanced and cheap as developed ones but perhaps a kind of batch processing may be adopted for OS upgrades using the net. Something to think about. GoodLuck.

---

