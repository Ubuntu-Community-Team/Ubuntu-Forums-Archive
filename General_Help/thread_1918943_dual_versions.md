---
title: "dual versions"
date: 2012-02-02
forum: General Help
---

### Post by Ron O on 2012-02-02
I plan to load 12.04 LTS in April but do not want to lose my current 10.04 Lucid installation, which is good till April 2013. I have an empty 30G ext4 partition on my hard drive that I plan to use for 12.04.

The question is whether I can do the usual install considering that Lucid already has a version of GRUB on the system. Will the new install try to install a later version of GRUB and cause conflicts or other issues, or can I just expect to see Grub as usual with both 12.04 and 10.04 on the list?

---

### Post by raja.genupula on 2012-02-02
> **Ron O said:**
> I plan to load 12.04 LTS in April but do not want to lose my current 10.04 Lucid installation, which is good till April 2013. I have an empty 30G ext4 partition on my hard drive that I plan to use for 12.04.

The question is whether I can do the usual install considering that Lucid already has a version of GRUB on the system. Will the new install try to install a later version of GRUB and cause conflicts or other issues, or can I just expect to see Grub as usual with both 12.04 and 10.04 on the list?

Hi man 
         No problem you gonna get with the GRUB , because same GRUB version (GRUB 2)  for both 10.04 and 12.04 .I am sure , everything will be fine .

---

### Post by trollger on 2012-02-02
worst case you can just boot back into your 10.04 installation and reinstall grub just make sure you over write where the new grub was installed. when I installed Ubuntu I did not see an option to not install a boot loader so I had to overwrite it.

just make sure to reinstall grub in another OS if you decided you don't like 12.04 and remove it.

---

### Post by raja.genupula on 2012-02-02
dont worry about the grub . if you dont like any version of your Ubuntu then boot into other versions which you like and then do this 
```
sudo dpkg-reconfigure grub-pc
```

that will install the grub to your desired version . before removing you have to do it and after removing what ever the version you dont like open the terminal and 

```
sudo update-grub 
```

this will remove the entry of version which you removed by updating your grub .

---

### Post by Ron O on 2012-02-02
Thanks all! I guess I am reasonably safe. No reports of a horror show so far.

Comment: I had thought of trying 12.04, then later most likely switching to Mint, since I am addicted to Gnome 2, like so many other users. But this help request is a reminder of why Ubuntu is so good and why I should give an earnest attempt to transition to Unity- Ubuntu Forums are excellent with fantastic community support.

---

### Post by raja.genupula on 2012-02-03
I think you can do on gnome 3 what ever you did on gnome 2  by switching your environment to gnome-classic by installing gnome-shell in your system .

after installing gnome-shell , do logout and at login screen settings you can choose the required sessions i mean classic for you and which makes you feel like gnome 2 . 

All the best .

---

### Post by Ron O on 2012-02-03
Yep, there are a lot of comments out there about Gnome 3. It seems like most of the people who hate Unity do not like Gnome 3 much better. They want Gnome 2 back. I guess the look and feel of Gnome 3 is closer to Unity than it is to Gnome 2, which is a comfortable environment for old Windoze users. But Mark Shuttlesworth is holding his ground on the Unity/Gnome 3 environments, and he may be on to something despite the uproar. I heard there is always an uproar when significant change is initiated, but later people calm down and actually like the changes.

I can't say until I've tried it. All I know right now is that Unity looks like a smart phone environment and it looks kind of silly on a 27 inch desktop monitor. I only use LTS releases, which is what 12.04 will be, and they made a wise decision extending support to 5 years instead of 3.

---

### Post by satish_j on 2012-02-03
iam desperately waiting for 12.04 and i will be installing it over 10.04..:)

---

### Post by 3rdalbum on 2012-02-03
> **Ron O said:**
> I heard there is always an uproar when significant change is initiated, but later people calm down and actually like the changes.

I can't say until I've tried it.

You're using 10.04, right? Well, I remember when 10.04 was released, there were two major issues that people complained about. The reaction to these issues was the equivalent of Unity in its day, and these two issues were bad enough to force people to abandon Ubuntu in droves (or so was threatened).

The first issue was that, by default, the window buttons were on the left instead of the right of the window.

The second issue, and this is a real showstopper for some people: The default wallpaper is purple instead of brown.

Sarcasm aside, people will settle down. They'll threaten to move to Mint or Fedora or something, but they'll all be back when Unity gets a hot new feature. By 12.10 everyone will be complaining about some other new change, and praising 11.10 as "perfection".

---

### Post by ptsubin on 2012-02-03
It is not that I hate unity. But gnome-shell felt elegant and much more usable for me. I am not very fond of keyboard shortcuts while not using editors. Also in many places unity takes extra clicks. After all, it is just a matter of preference. The issue is there is not much to customize with both unity and gnome-shell. Or at least not yet there. Regular Linux users are very used to tuning and personalizing, not just the appearance. So I keep along with the upgrades and stick to gnome-shell. I am very happy I can just apt-get it..

---

### Post by Ron O on 2012-02-03
Satish- Probably the only similarity between Windoze and Ubuntu is that "load over" upgrades do not work out too well- at least according to a lot of people online. That is why I am doing a fresh install of 12.04 on it's own partition, then I can move documents etc from 10.04 and finally remove 10.04. If you download the Parted Magic CD (GParted that boots and runs from the CD so your current system partition remains unmounted), you can add a partition for 12.04 and do a fresh install. Then later you can remove 10.04 and merge it's partition with 12.04. From all I have read, I would definitely not do a load over upgrade, although you will find some people that claim it works fine.

3dalbum- I remember the reversed window controls- all I did was load a different Ubuntu Theme that put them back where they originally were. Whenever something comes up in Ubuntu that people do not like, someone always makes a fix in pretty short order because the community is so large and has some real world-class geeks working in it- better than the pros at Microsoft. So I agree with you and do not see any negative features as anything to get hysterical about.

I try diligently to switch people over to Ubuntu, but it is a hard, hard sell. The more they are invested in Windoze, the less they are willing to change, no matter how bad Windoze gets. They think you are hosing them when you tell them you have a rock-solid stable system because we all know that computers are finicky,unreliable, and un-secure. This is Bill Gates' enduring contribution to humanity!

---

### Post by afz12 on 2012-02-03
FYI - I am running Ubuntu 12.04 Alpha on a virtual machine at the moment and for an "alpha' it is excellent! I haven't come across any issues yet. Also, I agree as others have posted, a fresh install from scratch is always the best option. I might repartition this win7 machine later and Ubuntu 12.04, even in its present state, would be my first choice.

---

### Post by Ron O on 2012-02-04
I have a feeling the release version of 12.04 will be great, especially after the community starts doing a few work-arounds for items that are a little aggravating.

If you are going to repartition and have not tried Parted Magic, it's great. I've used it over and over on Linux and Windoze partitions and never had a problem.

Somewhat off-topic rant--I just spent ALL night trying to fix a Windoze 7 computer for a friend- it just stalls when it tries to install updates and I have had zero success fixing it. I have never had issues anything like this with Ubuntu.

---

