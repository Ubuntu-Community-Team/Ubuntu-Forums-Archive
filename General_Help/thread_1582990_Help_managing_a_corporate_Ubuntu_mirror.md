---
title: "Help managing a corporate Ubuntu mirror"
date: 2010-09-27
forum: General Help
---

### Post by Hypatia2 on 2010-09-27
I've recently taken over managing my company's Linux mirrors, and found and found Ubuntu's to be the largest at nearly 700GB. That's pretty darned big!  And we're running out of room. We use a script that does the 2 pass rsync that Ubuntu recommends, but I can't figure out any way to weed out the older obsolete package versions that we don't need. We really only need the last couple releases, but packages (.deb files) are not marked with the associated release in a way that I can use to exclude them via rsync.  

Are we doomed to buying a Terabyte array just to mirror Ubuntu for our employees? I don't think I can justify that to management.

Help!?!

---

### Post by QLee on 2010-09-27
Doubt that there is any need to keep a full mirror, if this is a private mirror you could keep just the packages that have been approved by the IT dept for your system.

You might want to look into:
apt-mirror
debmirror
debpartial-mirror
apt-move

to see if one of them might suit your purpose.

---

### Post by Hypatia2 on 2010-09-27
QLee, thanks.

Well, I kind'a AM the IT department (actually I'm 1/2 the IT dept) in our mostly Linux company. Our mirror server runs RHEL and mirrors a lot more than Ubuntu. The packages you mentioned don't really do what I need. It's just that Ubuntu is a rapidly changing distro. The Debian mirror is about 400 GB. 

Is there any way to mirror just a couple on Ubuntu releases?

---

### Post by btindie on 2010-09-27
May want to take a look at [https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors), down the bottom there's a contact link to get help.

---

### Post by QLee on 2010-09-27
> **Hypatia2 said:**
> QLee, thanks.

Well, I kind'a AM the IT department (actually I'm 1/2 the IT dept) in our mostly Linux company. Our mirror server runs RHEL and mirrors a lot more than Ubuntu. The packages you mentioned don't really do what I need. It's just that Ubuntu is a rapidly changing distro. The Debian mirror is about 400 GB. 

Is there any way to mirror just a couple on Ubuntu releases?
In my opinion, you should standardise on a single release, why should a two person IT dept. have to support more than one version of each distro. Don't you go crazy when one of you is away? And, as I stated, it only has to have packages for what is used at your site, no need to mirror a complete version repository. Users don't get to choose their own software, do they?

Humm, it only took you fourty minutes to evaluate those four programs I suggested you look at, you must be a real expert, probably I don't have any further advice that would be beneficial to you. But, for example, apt-move would allow you to generate a mirror from one of your Ubuntu boxes, which would take less space than you are now using and have all the used (installed) software (and if configured correctly would keep itself "pruned"). One of the others might work better in other possible scenarios. Good luck.

---

### Post by Hypatia2 on 2010-09-27
QLee,
I appreciated your original response. Thank you for that one, but I really didn't find you second one useful or even all that friendly.
Do I have to really have to document every business decision my company makes? (here goes... Among other things, we supply a customized version of distro "A" to our customers, but our devs can use any distro they want on their desktop as long as they support it themselves. Ubuntu is the most popular distro of course). We just can't let everyone update through the firewall (I won't bother to justify that).

Because I try to do a little research before posting questions to any forum, I was already familiar with most of the packages you mentioned except for debpartial-mirror and apt-move. Simply reading the summary for those two packages on packages.debian.org told me that they were not what I was looking for. 
While apt-move is pretty interesting, I'd have to keep a VM for each supported release current, and have have ensure that EVERY available package is installed on each of the VMs (There are packages that cannot be installed side-by-side). It'd be a maintenance nightmare.



btindie,

Thanks. I'd seen that page, but hadn't noticed the ubuntu-mirrors mailing list before. I'll search the archives and if necessary, ask my question there. Of course, I'll post any solution back here.

---

### Post by btindie on 2010-09-27
There's also an [IRC]("irc://irc.freenode.net/ubuntu-mirrors") channel where you can go to ask for help, may be worth checking out first.

---

