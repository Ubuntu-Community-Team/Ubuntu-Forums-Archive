---
title: "See a Windows Network"
date: 2006-04-21
forum: General Help
---

### Post by bryan4134 on 2006-04-21
First day with Ubuntu (and Linux for that matter).  Wireless working fine and can access internet via wireless router.  How do I go about "seeing" my Windows network - is this possible?

Thanks,  Bryan

---

### Post by Zorro on 2006-04-21
For sure... How is your windows network setup? just the normal windows shares? If so..  Have a look at the ubuntu wiki... [https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29) great resource, used it myself when  I was setting up mine...

---

### Post by Stealth on 2006-04-21
In places, go to "Network Servers". Then you might see your shares there, or atleast your Workgroup, in which you can start browsing the shares :)

Of course, you have to have Samba set up, in which case click the link Zorro put above.

---

### Post by mjm115 on 2006-04-21
sudo apt-get install samba

---

