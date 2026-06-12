---
title: "Gksu gedit problem"
date: 2012-01-17
forum: General Help
---

### Post by Neill_R on 2012-01-17
In  a terminal window I type

```


gksu gedit


```

Although the starting Administration appears in the task bar, neither the enter password window nor the gedit window appears (repeatable).

```


sudo gedit


```

works

---

### Post by sudodus on 2012-01-17
and for me ```
gksudo gedit
``` works too, but I prefer ```
sudo gedit
```

Use what works for you and enjoy :-)

---

### Post by mcduck on 2012-01-17
Check the root user's home directory, and try deleting/renaming any Gedit-related config files.

Gksudo loads root user's profile correctly, which sudo doesn't do for graphical applications, to the difference could very well be that the root's config file has problems while your own account's config is fine.

Also make sure the theme you are using is properly installed system-wide instead of just for your own user, or is linked from your home to root's home.


(and unlike what sudodus suggested, you really, really should always use gksudo for graphical applications, as using sudo for them can cause serious troubles and figuring out, and remembering, which programs work OK even with sudo and which don't is much harder than just learning the habit of using gksudo always. The same of course applies to commands like "sudo su" or "sudo -s", the one that actually works correctly is "sudo -i")

---

### Post by Morbius1 on 2012-01-17
> **mcduck said:**
> you really, really should always use gksudo for graphical applications, as using sudo for them can cause serious troubles and figuring out, and remembering, which programs work ok even with sudo and which don't is much harder than just learning the habit of using gksudo always. The same of course applies to commands like "sudo su" or "sudo -s", the one that actually works correctly is "sudo -i")
+1

---

### Post by sudodus on 2012-01-17
I read and learn, mcduck, but I have used Ubuntu since 2008 without problems with 'sudo gui-program'. Please give an example, where there would be problems!

---

### Post by BlinkinCat on 2012-01-17
> **mcduck said:**
> 
(and unlike what sudodus suggested, you really, really should always use gksudo for graphical applications, as using sudo for them can cause serious troubles and figuring out, and remembering, which programs work ok even with sudo and which don't is much harder than just learning the habit of using gksudo always. The same of course applies to commands like "sudo su" or "sudo -s", the one that actually works correctly is "sudo -i")

+2

Having a search would verify mcduck's statement

Edit: For example - [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by mcduck on 2012-01-17
> **sudodus said:**
> I read and learn, mcduck, but I have used Ubuntu since 2008 without problems with 'sudo gui-program'. Please give an example, where there would be problems!

Running a graphical program with sudo gives you root's permissions, but still uses your normal user account's environment and configuration files. Depending on how the program in question works, changing any setting would write the setting back to configuration file, but because of the root's permissions in use the file would then become owned by root. Which would then make your own user unable to change the setting in the program any more.

(same can of course happen with any files the program handles, or needs to store on the disc, not just setting files)

It is also the most common cause for people having permissions problems with the ~/-ICEauthority file, preventing them completely from logging in due to the file having become owned by root.

The problem is that some applications work fine regardless of which command you use, sudo or gksudo, but finding out which ones don't work would require you to go through every possible program, breaking your system again and again. (and of course then remembering which ones you can launch with sudo, and which ones require gksudo). And doing that really doesn't make any sense, when just using gksudo for every GUI app solves the problem more reliably and with less effort. ;)

Similar thing, and much easier to test yourself, is with the "sudo -s" versus "sudo -i". Open a terminal and run the first one, and you'll notice you are still in the current user's home directory, and checking the $PATH and other environment variables shows that they are still the ones from the normal user account. On the other hand running "sudo -i" immediately moves you to root's home, like is supposed to happen when a user logs in, and also loads the root's environment and setting files.
```

mcduck@Hyperion:~$ sudo -s
[sudo] password for mcduck: 

no brainer:
	A decision which, viewed through the retrospectoscope,
	is "obvious" to those who failed to make it originally.

root@Hyperion:~# ls
Audiobooks  Desktop    Downloads  Pictures  Programs  Public   Templates   Videos
bin         Documents  Music      Podcasts  Projects  Storage  Ubuntu One  WWW
root@Hyperion:~# exit
exit
mcduck@Hyperion:~$ sudo -i
root@Hyperion:~# ls
Desktop
root@Hyperion:~#
```
(notice how after "sudo -s" it's even running the fortune command, which is in *my user's* .bashrc, not in root's.)

---

### Post by sudodus on 2012-01-17
Thanks mcduck,

I understand, maybe I have been lucky, running the critical GUI programs from the menu system rather than from a terminal with sudo. I'm warned now, and I'll try to change my habits.

---

### Post by Morbius1 on 2012-01-17
I suppose the other thing that makes this slightly more confusing is the use of gksu instead of gksudo. In Ubuntu gksudo is an alias for gksu so it doesn't matter which one you use but I guess to be precise about it I should have bean using gksudo all this time.

[COLOR=Blue]Rather than hijack this topic from the problem at hand I'll add something here:[/COLOR]
> **satanselbow said:**
> I actually made the very same mistake  ("gksu" not "bean") in a post a while ago and took it as a lesson learnt  :wink:  It can lead to serious breakage pretty darn quickly and is akin to  playing russian roulette with your installation (or "sudo roulette"  maybe?)
There is no difference between gksu and gksudo in Ubuntu.
> ls -l /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 2010-05-18 07:19 /usr/bin/gksudo -> gksuOne is a link to the other.

---

### Post by satanselbow on 2012-01-17
> **Morbius1 said:**
> ...I guess to be precise about it I should have bean using gksudo all this time...

Nice ironic use of "been" typo too :popcorn:

I actually made the very same mistake ("gksu" not "bean") in a post a while ago and took it as a lesson learnt ;) It can lead to serious breakage pretty darn quickly and is akin to playing russian roulette with your installation (or "sudo roulette" maybe?)

---

### Post by Neill_R on 2012-01-17
I failed to do a man gksudo

where i would have found there is a debug switch 


gksu --debug gedit
No ask_pass set, using default!
xauth: /tmp/libgksu-rLdfe7/.Xauthority
STARTUP_ID: gksu/gedit/6736-0-freds_TIME23360631
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: --
buffer: --


...

buffer: --
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.

THEN IT JUST HANGS
like forever
ctrl C to escape


FYI I am using likewise-open
N-R\neill@freds:~$ pwd ~
/home/likewise-open/N-R/neill
N-R\neill@freds:~$ 


Also I turned on the AD DC computer (doh!)

N-\neill@freds:~$ gksu --debug gedit
No ask_pass set, using default!
xauth: /tmp/libgksu-gYylzJ/.Xauthority
STARTUP_ID: gksu/gedit/7065-0-freds_TIME24839196
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: -GNOME_SUDO_PASS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...

the password window appeared I gave the password and I got gedit as root 

I understand why it failed now but there must be a different mechanism to log in because I can and sometimes do log in with the DC PC powered off. Like Windows Ubuntu (likewise-open) is capable of cashing the user's password once he/she has successfully logged in (validated by the Domain controller Active Directory) 


when i exit gedit

xauth: /tmp/libgksu-PNG2xU/.Xauthority
xauth_env: /var/run/gdm/auth-for-N-R\neill-j0TzTa/database
dir: /tmp/libgksu-PNG2xU
N-R\neill@freds:~$ 


However if i switch to a local user then it still fails

going to log out of both shutdown and retry

---

### Post by Neill_R on 2012-01-17
i rebooted and that also cleared the local user's problem. I am guessing but if I do a gksu gedit while logged in as a domain user but the DC is down this locks the system. if i restart the DC then it clears it and re-logging in clears the local user account too.

Not solved but explained whether correctly or not I can not say

---

