---
title: "Using Server edition on desktop machines"
date: 2009-06-30
forum: General Help
---

### Post by charstar on 2009-06-30
Hi,

Were i work we are currently looking at upgrading our linux distro.  One option that i brought up is to use Ubuntu.  The only problem is that we want to do the upgrade in October so we are out of phase with the desktop LTS release.  To maximize the amount of time we stay at our next version, I was thinking of using the server edition and then install gnome and the other packages that we need.  

Is this a good idea?  One concern i have is that since i am installing gnome and other apps on my own, can i assume that what i install today will be the same as what i install a year from now?

Any sugestions are welcome.

Thanks,

---

### Post by upbeat.linux on 2009-06-30
In a server environment your best bet would be to stay with the LTS version, but it's up to you.  You are guaranteed updates for that version for at least 18 months and 5 years of support ([https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)).  

If you pay attention to the EOL date for LTS updates you'd be able to upgrade the current LTS before updates become unavailable.

IMO, I wouldn't install gnome/X on server (edit: although it is possible and stable), but depending on your needs install a web based console like webmin and use iptables or your hardware based firewall to restrict access.

Take a good look at the applications you are hosting, the hardware specs of your box, and what your trying to accomplish and go from there.  In some cases the minimal server install is a good starting point for older hardware or a platform that you wish to tailor to your needs

Another thing to keep in mind is applications have mutual dependencies.  apt will make sure to upgrade an application if a dependency is altered and there is an update available, but you have complete control over what gets installed on your system.

So, my short answer is stay with LTS for server releases.

---

### Post by t4thfavor on 2009-06-30
I have installed server and put X on top of it, not that I recommend it. Just saying it is possible, and it has been done.

---

### Post by charstar on 2009-06-30
Ok, I see I was not all that clear.  I actually would prefer to use the desktop edition, since that is how it will be used.  The reason for using the 8.04 LTS server edition is that it has support until 2013.  This would minimize the frequency that we would have to update versions.  That's all i am really after.

The way I did this on my test machine is to install the 8.04 server edition with none of the server packages selected, then install ubuntu-desktop.  I am curious as to why installing x/gnome on the server edition is not recommended?  Seems ominous that you both mention this.

---

