---
title: "[SOLVED] Problem with KDM or memory corruption?!"
date: 2006-05-08
forum: General Help
---

### Post by RavenOfOdin on 2006-05-08
Hi. . .Just today I've started getting these little messages in syslog which say:

"kdm_greet: Couldn't open default user face"
"kdm_greet: Internal error: memory corruption detected."
"kdm_greet: Couldn't open default user face"

I'm using the 2.6.12-10.32 kernel with KDE 3.5.2 and am able to get in to KDM as well as the desktop without any black screens - as seems to be happening to other users with this problem via a forum search.  GRUB works fine, and memtest86+ after one pass didn't detect any errors.

My PC is a Hewlett Packard Pavilion 523n with 1.8GHz, 512MB DDR SDRAM, 80 GB of disk space, and ATI Radeon 128MB graphics card.

Should I be concerned about this?

(It's better to post this here than in a reply to a dev thread, IMO :p)

---

### Post by Ptero-4 on 2006-05-08
IIRC. This problem is b/c for some reason KDM 3.4.x themes fail under KDM 3.5.x (At least it was a problem I faced when I tried KDE 3.5.1 on breezy).

---

### Post by RavenOfOdin on 2006-05-08
Hmm. I'm using the "Beauty of Darkness" theme atm with "Dead Rat" splash screen.  I'll try and change that as well as the KDM splash and see what happens.

---

### Post by kson on 2006-05-08
I have the same problem. GDM works and startx from the terminal works. Failsafe login in KDM works to but not Gnome or KDE. Even root are disallowed (Root has a password and KDM is configured to allow root to login). I also get errors to my .xsession-errors file: *"Ingen profil för användaren "martin" hittades"*. That means: *"No profile for user "martin" found"*. What profile does kdm need?

I also should mention that I started with ubuntu dapper and installed the kubuntu packages.

---

### Post by RavenOfOdin on 2006-05-09
[QUOTE=Ptero-4]IIRC. This problem is b/c for some reason KDM 3.4.x themes fail under KDM 3.5.x (At least it was a problem I faced when I tried KDE 3.5.1 on breezy).[/QUOTE]

Beauty of Darkness apparently depends on 3.5.x so there goes that idea out the window.  Nowhere in my .xsession-errors file am I finding "no profile for user <name here> found" . . .

[http://www.kde-look.org/content/show.php?content=21124](http://www.kde-look.org/content/show.php?content=21124)

This is the KDM theme I have and it also depends on 3.5.x!

*shrugs*

---

### Post by kson on 2006-05-19
I fixed it! I had to ad my user to a group in /etc/desktop-profiles/users.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<profiles>
  <user name="martin" profile="users"/>
</profiles>
```

---

### Post by BROKEN_LADDER on 2006-06-24
[QUOTE=kson]I fixed it! I had to ad my user to a group in /etc/desktop-profiles/users.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<profiles>
  <user name="martin" profile="users"/>
</profiles>
```[/QUOTE]

I HAD A SIMILAR PROBLEM, AND YOUR FEEDBACK WAS VERY HELPFUL.  IN MY SITUATION I GOT SIMILAR ERRORS, WHICH EVOLVED A BIT AS I WORKED ON THE PROBLEM.  ONE OF THEM WAS AS FOLLOWS:

> 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "brokenladder"
/etc/gdm/Xsession: Beginning session setup...
Failed to start message bus: Failed to read directory "/usr/local/share/dbus-1/services": No such file or directory
EOF in dbus-launch reading address from bus daemon 


Ultimately, I fixed this by going to /etc/dbus-1/session.conf, and removing the line

<servicedir>/usr/local/share/dbus-1/services</servicedir>

leaving only the latter,

<servicedir>/usr/share/dbus-1/services</servicedir>

That fixed it right away.

---

