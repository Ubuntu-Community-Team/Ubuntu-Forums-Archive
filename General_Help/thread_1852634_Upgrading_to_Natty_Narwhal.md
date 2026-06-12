---
title: "Upgrading to Natty Narwhal?"
date: 2011-09-30
forum: General Help
---

### Post by beanco on 2011-09-30
So, I was given a new laptop today at work... an HP ProBook 4330s and the head of our IT department was nice enough to transfer everythign from my old and dying laptop, lucid lynx and all...

However, there are some problems and he suggested I upgrade to the newest adn best Ubuntu....

I assume that would be Natty Narwhal. Well, now how do I do this from the CL?

Thanks

Robi

---

### Post by OpEn_SoUrCe_RoCkS on 2011-09-30
```
sudo do-release-upgrade
```

Another way is:
```
update-manager -c
```

That gives you the GUI...

---

### Post by Blasphemist on 2011-09-30
Maybe you should pass us information on any issues you are having and whether or not all is working before we start. That said, I'd recommend download a live cd of the newest version and install from that. Before you do any upgrade, do ensure that all of your data is backed up. When prompted during the installation, choose to upgrade without loosing any settings. This usually works but be safe by being backed up.

There is a new release in 2 weeks so keep that in mind. You are on the current LTS, long term support, release now and there really isn't any issue with staying on that. It is still being updated so unless you are having issues you may not choose to upgrade at all.

---

### Post by seawolf167 on 2011-09-30
[Upgrade from 10.04 -> 11.04]("https://help.ubuntu.com/community/MaverickUpgrades")
[Upgrade from 10.10 -> 11.04]("https://help.ubuntu.com/community/NattyUpgrades")

That said, what specific issues are you having which required the distro upgrade?

Blasphemist's post gives good advice about the upgrade cycle too...

---

### Post by beanco on 2011-10-01
There were some issues with the hardware in this new laptop... the IT guy says.... he fount some *patch* to fix it but then when he tried to log onto the school's novell network the computer crashed, had to reboot, he had been working on it for a long time and was late for sg... said I should just upgrade to the newest version when I have the time....

I have done upgrades before, using live CDs... I just wanted to try ti from the CL this time......

Thanks


Robi

---

