---
title: "Rename computer?"
date: 2006-06-05
forum: General Help
---

### Post by drfox on 2006-06-05
Is it possible to permanently rename my computer without breaking apt-get?
I tried sudo rename, and the new name stuck until reboot, but apt-get got confused until the reboot.

Larry

---

### Post by Rui Pais on 2006-06-05
Hi,
i think is just change /etc/hostname and /etc/hosts and after that reboot... dont know if has side effects by i don't think so... 
In any case do it from a terminal, after close any gnome, kde, or whatever session and any gdm session.


*EDIT:*
[COLOR="Red"]** BE CAREFUL DOING THAT SINCE PEOPLE SEEMS TO EASILY GET THEY COMPUTERS INACCESSIBLE!! **[/COLOR]
**(Read the all thread before do it!)**

---

### Post by garyng on 2006-06-05
I don't think rename is the right command and apt-get should have nothing to do with the hostname

modify /etc/hostname

then

invoke-rc.d hostname.sh start

---

### Post by viciouslime on 2006-06-05
Is there not a gui way of doing this?

---

### Post by viciouslime on 2006-06-05
Ah found it:
Goto system menu, administration, network, then it is on the general tab. :)

---

### Post by drfox on 2006-06-05
[QUOTE=garyng]I don't think rename is the right command and apt-get should have nothing to do with the hostname

modify /etc/hostname

then

invoke-rc.d hostname.sh start[/QUOTE]

OH NO. I modified /etc/hostname, and now, when I invoke-rc.d hostname.sh start, I get this error:
unable to lookup newname via gethostbyname()

I also can't use sudo

HELP!

---

### Post by Melvil on 2006-06-05
I think that "unable to lookup... gethostbyname()" is normal, because your hostname is not a registered one on the internet, but I'm not sure myself

---

### Post by garyng on 2006-06-05
check /etc/sudoers(as root) to see if it is tied to a specific hostname. Otherwise, there is no reason changing hostname would stop you from using sudo.

as for the gethostname() error, it is normal as the procedure I mentioned is exactly what the machine boot up does, it is given as a way to skip the reboot process, nothing special other than that. You can reboot if you want.

---

### Post by drfox on 2006-06-05
[QUOTE=garyng]check /etc/sudoers(as root) to see if it is tied to a specific hostname. Otherwise, there is no reason changing hostname would stop you from using sudo.

as for the gethostname() error, it is normal as the procedure I mentioned is exactly what the machine boot up does, it is given as a way to skip the reboot process, nothing special other than that. You can reboot if you want.[/QUOTE]


I can't log in as root, and I can't view or edit /etc/sudoers, and I can't edit /etc/hostname.  Any other suggestions?

Larry

---

### Post by lindsay_keir on 2006-06-07
](*,) Ah **drfox** - it looks like no one believes you. But, I believe, I believe!
Happlily, for me, I changed the hostname early into setting up a new full CD install and for some reason I did a reboot. Ah well!

But yes, I guess there's some sort of security in sudo that uses the hostname.

---

### Post by Ragazzo on 2006-06-07
[QUOTE=drfox]I can't log in as root, and I can't view or edit /etc/sudoers, and I can't edit /etc/hostname.  Any other suggestions?

Larry[/QUOTE]

Write "su" in terminal and edit the name back to what it was in /etc/hostname

---

### Post by drfox on 2006-06-07
Thanks Lindsay. I was able to solve my problem by booting from a Knoppix CD, and becoming root. I made my drive writable and then changed my hostname back to the original . I then booted Ubuntu and changed the name from System>Administration>Networking. Phew! 

Larry

---

### Post by WillLuongo on 2008-01-10
When I did this it broke my installation. I get the following error when I try SUDO: 

sudo: must be setuid root

Additionally, my apache server is having problems serving pages with mysqli now.

Not really sure what happened? Any one have any ideas?

---

### Post by MartynA on 2008-01-10
> **WillLuongo said:**
> When I did this it broke my installation. I get the following error when I try SUDO: 

sudo: must be setuid root

Additionally, my apache server is having problems serving pages with mysqli now.

Not really sure what happened? Any one have any ideas?

If you mean you've changed your hostname by modifying /etc/hostname then you need to also change the name in /etc/hosts, as sudo uses gethostbyname() 

Since you can't sudo I'd boot to the recovery console or log in as root (if its enabled).

---

### Post by WillLuongo on 2008-01-10
Ok, I did that, I still am unable to use sudo. I am able to log in as root through the recovery option in GRUB.

When I was trying to fix my apache broken-ness after changing the host name, at some point I think I accidentally changed all the permissions (careless use of * operator not realizing I was in / ) . It seems this might be related to my symptoms. 

Is there any way to restore settings, without losing the contents of var/www and mysql databases?

---

### Post by MartynA on 2008-01-10
Ah, got it. You need to redo the permissions on /usr/bin/sudo

Try chmod 4755 /usr/bin/sudo

[http://ubuntuforums.org/showthread.php?t=219767](http://ubuntuforums.org/showthread.php?t=219767)

---

### Post by WillLuongo on 2008-01-10
Thank you so much. With your help I was able to get into my system again and back everything up so I could put it on a reinstalled system!

---

