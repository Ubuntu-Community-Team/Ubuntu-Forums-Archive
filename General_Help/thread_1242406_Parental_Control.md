---
title: "Parental Control"
date: 2009-08-17
forum: General Help
---

### Post by marsdend on 2009-08-17
Hi all,

My partners little brother (13) is staying for a few days in a couple of weeks, we don't want to stop him from using the computer but would would like to restrict it in the sense of Web Filtering and System safety eg. cannot damage or change system settings. We will create him his own account so he can change the desktop background etc and learn the Ubuntu OS.

Can anyone recommend the best software for this?

Thanks in advance!
Dan

---

### Post by ajgreeny on 2009-08-17
Not sure about webfiltering, other than Dansguardian [http://dansguardian.org/](http://dansguardian.org/) but as regards system safety and not changing any system files etc, just make sure your own admin password is strong, and that he doesn't know it and can't find it. Also make sure he is not in the admin group.  That way he will not be able to make any system changes at all.  By default, any new users will not be added to the admin group, so you should be OK that way.

You may also want to comment out the recovery mode options from the /boot/grub/menu.lst by adding a # in front of the line like this:-
#title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
I know what 13 year olds can be like with computers, so if he is curious he could find the way to overcome that, but it seems unlikely if he is not used to linux at the moment.

---

### Post by marsdend on 2009-08-17
> **ajgreeny said:**
> Not sure about webfiltering, other than Dansguardian [http://dansguardian.org/](http://dansguardian.org/) but as regards system safety and not changing any system files etc, just make sure your own admin password is strong, and that he doesn't know it and can't find it. Also make sure he is not in the admin group.  That way he will not be able to make any system changes at all.  By default, any new users will not be added to the admin group, so you should be OK that way.

You may also want to comment out the recovery mode options from the /boot/grub/menu.lst by adding a # in front of the line like this:-
#title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
I know what 13 year olds can be like with computers, so if he is curious he could find the way to overcome that, but it seems unlikely if he is not used to linux at the moment.

Thanks for that so would a user with "Desktop User" Privileges be suitable?

Cheers
Dan

---

### Post by Psycho.mario on 2009-08-17
If you sign up to [opendns]("http://www.opendns.com/") and set the ip's it gives you as your nameservers, it will automatically block adult content. This is what i use, and it means you do not need to install anything else, just change your DNS servers in network settings.

---

### Post by oldos2er on 2009-08-17
> **Psycho.mario said:**
> If you sign up to [opendns]("http://www.opendns.com/") and set the ip's it gives you as your nameservers, it will automatically block adult content. This is what i use, and it means you do not need to install anything else, just change your DNS servers in network settings.

 +1 for opendns. [http://www.opendns.com/](http://www.opendns.com/)

---

### Post by soapBAR2 on 2009-11-04
If you're going to go the openDNS route* but still don't want to parent-protect your whole computer, just his account, then you could have the /etc/resolv.conf change per account. Simply

sudo cp /etc/resolv.conf /etc/resolv.conf.backup
sudo cp /etc/resolv.conf /etc/resolv.conf.childsafe
sudo chmod 644 /etc/resolv.conf.*

to create two backup copies of resolv.conf and protect them. Then, (sudo) open the childsafe one and put in the custom DNS entries as per above posts. Now, to make it trigger on only his account, simply (one-liner):

KDE:
```
sudo cd /home/**13yearold**/.kde/Autostart/ ; sudo echo -e "#!/bin/bash\n/etc/resolv.conf.childsafe > /etc/resolv.conf" > childsafe ; sudo chmod 711 childsafe ; sudo cd /home/**yourname**/.kde/Autostart/ ; sudo echo -e "#!/bin/bash\n/etc/resolv.conf.backup > /etc/resolv.conf" > dnsfix ; sudo chmod 711 childsafe
```

Changing each bold bit to the relevant vales. I'm not sure how to do it in Gnome or XFCE, but I think they both have a nice graphical interface for autostart (as does KDE, but copy+paste into a terminal is usually easier).

* This route has it's drawbacks - if he knows the IP address of a blacklisted website he can still go there. However, it's otherwise simple and effective.

---

### Post by AldenIsZen on 2009-11-20
Thanks for the opendns recommendation.

---

