---
title: "Rename Hostname"
date: 2010-04-10
forum: General Help
---

### Post by Muhnamana on 2010-04-10
So I installed Ubuntu Server and my current hostname is "ub-srv". Is it possible to rename the hostname so it reads "ub-srv1"?

If so how'd you do this and what could it effect?

---

### Post by QLee on 2010-04-10
Muhnamana, the hostname is set during init from the information in /etc/hostname.

---

### Post by yetiman64 on 2010-04-10
Hi Muhnamana,

I've had to change my setups hostname on a previous install and at the time noted it had to be changed in 2 files, /etc/hostname & /etc/hosts.

I'm not sure of which editor you use on server, just remember you'll need to "sudo" (if completely in terminal) or "gksudo" (if graphical) the editor to change these files.

In /etc/hostname change the contents to ub-srv1, and in /etc/hosts change only the one line with "127.x.x.x        ub-srv" to read "127.x.x.x       ub-srv1" instead (just keep the formatting within the file unchanged when altering the name).

After both files are saved you will need to restart the machine, (logging off/on alone doesn't set the changes). [COLOR=RoyalBlue]Edit:[/COLOR] [COLOR=RoyalBlue]check QLee's command for setting the changes without rebooting in post #6[/COLOR].

Just tested this on 9.04 (desktop) and the changes show in both the system monitor and the gnome-terminal - I'm assuming its the same process for server. 

This change hasn't stopped any of my connectivity to internet though it may have effects on local sharing you've set up - I don't remember having any problems with local sharing the last time I did it this way. Although it may pay to check your samba or nfs config files, if you use samba or nfs, and see if they refer to the old name.

---

### Post by QLee on 2010-04-10
Strictly speaking, it isn't necessary to have a "hosts" file. Some things will depend somewhat on the topology of Muhnamana's network and how the network is used, of which we know nothing because it wasn't detailed.

Edit: It wouldn't be necessary to have a "name" other than "lo" or "localhost" for the localhost.

---

### Post by yetiman64 on 2010-04-10
> **QLee said:**
> Strictly speaking, it isn't necessary to have a "hosts" file. Some things will depend somewhat on the topology of Muhnamana's network and how the network is used, of which we know nothing because it wasn't detailed.

Edit: It wouldn't be necessary to have a "name" other than "lo" or "localhost" for the localhost.

The above is true, just to clarify my post though - is along the lines of be aware that _if _there are entries in both these files to change them both (keep them uniform). As the first time I changed only the hostname without changing the hosts file (which existed in my setup of the time & again now), further checking was required (most likey to have been done through checking out this forum - about 1&1/2 to 2 years ago - while using Hardy Heron).
 Pays to be aware, but as you say it depends soley on Muhnamana's network topology. 
 Cheers,   Nev.

---

### Post by QLee on 2010-04-10
OK, I imagine our clarifications will benefit Muhnamana.

I also might as well mention that it isn't necessary to reboot a server to change the hostname. 

hostname -F /etc/hostname , after changing the hostname file will change it on a running system.

Edit: And naturally, one has to do that with root permissions because it changes system files, so loging off and back on of a user isn't going to affect it..

---

### Post by yetiman64 on 2010-04-10
> hostname -F /etc/hostname , after changing the hostname file will change it on a running system.     Actually that's very good to know for my benefit there as well, thanks. 

Just out of interest I did just change my hostname again (it worked only changing the /etc/hostname file) however I notice on my standard Jaunty install that the hosts file still reflects the old hostname. 

@ **QLee **Any ideas what possible consequences such a setting could have on networking / filesharing (if any)?

Edit: At the time (using Hardy) I was doing a lot of testing/experimenting with both samba and nfs shares. Can't remember now (getting too old maybe!:)) what the catch with this situation was - but needed to alter it at the time. Anyway hope this is of some help, & bye for now.

yetiman64

---

### Post by QLee on 2010-04-10
I fear that we are coming close to hijacking Muhnamana's thread but ...

Hosts exists to allow you to use a hostname rather than IP address, probably more important that your hosts file contains the names of other hosts on your network that you want to navigate to by name.

Of course, a network with a DNS server isn't going to need that, etc., etc. and so on If you're using samba your router is probably aware of netbios names. As we have mentioned, specifics make all the difference. There is nothing wrong with changing both as per your first reply, I would too, in the case you cited, I'm just trying to keep my replies general.

Now, lets wait and see if Muhnamana needs more help.

---

### Post by Muhnamana on 2010-04-10
Yes you guys almost did hijack my thread...hahaha! I'll give these suggestions a try and hopefully I wont need more help. I'm still new to Ubuntu, so learning is key for me.

---

### Post by QLee on 2010-04-10
I apologise, Muhnamana, I'm glad it didn't make things harder for you, good luck!

---

