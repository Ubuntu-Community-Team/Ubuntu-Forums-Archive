---
title: "Multiple Boot Questions :)"
date: 2006-04-21
forum: General Help
---

### Post by katiad on 2006-04-21
Just a few quick questions. I've been researching multi-boot for a few hours, but I'd like a bit of feedback to some lagging questions... I've ordered a second hard drive for my linux box. Currently running Kubuntu 5.10 and taking up the entire drive in two partitions (root & /home). The second drive would be used for several other linux distros, mostly for playing and testing. I'd like to peek into Dapper, check out MEPIS... whatever else catches my eye. And since I've only /looked/ at the grub config files. I'd like some hands on experience - but perhaps without hosing my current setup. *laugh*

1) Bootloaders - I assume that most distros ask if you'd like to install the bootloader or give you the option of installing it to the first sector of its partition, right? I'm a bit worried about installing something, and then... losing what I had, I guess.

2) Sharing /home - I've read that it's okay to share the /home partition, but not to share the /home directory between distros, for various reasons. How, then, should I share files without any permissions problems? Files such as my sylpheed email, all of my regular... stuff - documents, graphics, etc. 

Thanks!

---

### Post by goatflyer on 2006-04-21
Re grub...

During (re)installation of grub it should detect your other oses and add them all into grub's menu.lst

Re sharing...

You may not realize it, but In a way, you've already made the decision how 'others' will access your regular stuff.

Very likely, the permissions on most of your current stuff is set to allow 'everyone else' read permission.  Only the owner has read+write. 

This turns out to be a good thing, since you will become 'somebody else' when you boot another distro and try to access files on the ubuntu /home.  (To prevent confusion, run with a completely different username when playing with other distros)

Mepis will have its own seperate /home directory for its own Mepis users.  You would 'share' your data by mounting the ubuntu volume containing the ubuntu /home, which Mepis should regard as foreign and not be fooled with the ubuntu userids and groupids.

---

