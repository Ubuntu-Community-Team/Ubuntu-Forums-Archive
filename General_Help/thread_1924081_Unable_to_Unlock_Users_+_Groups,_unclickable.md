---
title: "Unable to Unlock Users + Groups, unclickable"
date: 2012-02-11
forum: General Help
---

### Post by Aliarse on 2012-02-11
Hello people, me again. ^_^ Had this issue for a little while now and its bugging me quite a bit.

Basically as the title states i cannot unlock users and groups due to it being greyed out. I've done a google for the issue and it seems a few have had it but no solution to it.

So far i've tried :

updating
changing user passwd via CLI
changing root passwd via CLI
removing ./Xauthoriy via CLI
updating policykit (already newest)
Tried running user-admin from CLI via sudo and while it loads, it never shows any users, like it hangs while searching..

These were all suggestions posted on the things i could find on this issue, and still its broken. I'm getting to the point of simply formatting and starting from scratch, which i'd rather not do as its taken me a while to set it up exactly how i wanted it..

I have no issue with updating or installing new software, but i think this issue also relates to me not being able to mount my usb mp3 player, which gives me a "not authorized" pop up dialog...

So here i am asking for help, which i try to avoid as i like trying to figure out the issues i have myself but i'm at my wits end with this one. Hoping you nice people can help me out and get this issue sorted before i lose all of my hair i'd appreciate it.

---

### Post by jamesisin on 2012-02-12
You shouldn't use sudo with a graphical application (such as users-admin).  Instead run gksudo users-admin.  That ought to open the Users Settings dialog as root.  Be cautious.  Hope that helps.

---

### Post by Aliarse on 2012-02-12
Thanks for the reply, yeah i meant i tried gksudo to open users-admin, while it opens, it constantly tries to load the users but fails to do so, all i get is the spinning icon and nothing else happens, theres no errors showing up in the terminal while doing this either.

---

### Post by jamesisin on 2012-02-12
I don't suppose it should matter as you ought to be able to open users-admin without gksudo...

Do you see any similarities here?

[https://bugs.launchpad.net/ubuntu/+source/policykit-gnome/+bug/183673](https://bugs.launchpad.net/ubuntu/+source/policykit-gnome/+bug/183673)

---

### Post by jayshomebrew on 2012-02-12
Are you connecting remotely, via NX ?  I think the default policy is to have that box greyed out for remote connections.
try a remote connection like this:

assuming your remote IP is: 192.168.1.100
```
ssh -X 192.168.1.100
gksu users-admin
```

and you should be able to edit your users
[IMG]http://www.techotopia.com/images/a/a1/Ubuntu_11_user_settings.jpg[/IMG]

linky:
[http://www.techotopia.com/index.php/Managing_Ubuntu_11.04_Users_and_Groups]("http://www.techotopia.com/index.php/Managing_Ubuntu_11.04_Users_and_Groups")

---

### Post by Aliarse on 2012-02-12
Just tried all of the commands in that bug report.

Installing gnome-system-tools returns with its already the newest version, running gnome-system-tools returns a command not found error
polkit-gnome-authorization returns a command not found error, trying to install returns a package not found error.
gksudo time-admin opens fine but i cannot lock the "click to prevent changes" button, no errors in terminal while doing this.
gksudo network-admin returns the same as time-admin. I had to install it first though...
gksudo shares-admin returns the same as the above two.
services-admin returns a command not found error.

david@admin $ locate policykit
/usr/lib/policykit-1
/usr/lib/policykit-1-gnome
/usr/lib/policykit-1/polkit-agent-helper-1
/usr/lib/policykit-1/polkitd
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
/usr/lib/python2.7/dist-packages/aptdaemon/policykit1.py
/usr/lib/python2.7/dist-packages/aptdaemon/policykit1.pyc
/usr/share/doc/policykit-1
/usr/share/doc/policykit-1-gnome
/usr/share/doc/policykit-desktop-privileges
/usr/share/doc/policykit-1/NEWS.gz
/usr/share/doc/policykit-1/README
/usr/share/doc/policykit-1/changelog.Debian.gz
/usr/share/doc/policykit-1/copyright
/usr/share/doc/policykit-1-gnome/AUTHORS
/usr/share/doc/policykit-1-gnome/NEWS.gz
/usr/share/doc/policykit-1-gnome/README
/usr/share/doc/policykit-1-gnome/TODO
/usr/share/doc/policykit-1-gnome/changelog.Debian.gz
/usr/share/doc/policykit-1-gnome/copyright
/usr/share/doc/policykit-desktop-privileges/changelog.gz
/usr/share/doc/policykit-desktop-privileges/copyright
/usr/share/polkit-1/actions/org.freedesktop.policykit.policy
/usr/share/pyshared/aptdaemon/policykit1.py
/var/lib/dpkg/info/policykit-1-gnome.conffiles
/var/lib/dpkg/info/policykit-1-gnome.list
/var/lib/dpkg/info/policykit-1-gnome.md5sums
/var/lib/dpkg/info/policykit-1.conffiles
/var/lib/dpkg/info/policykit-1.list
/var/lib/dpkg/info/policykit-1.md5sums
/var/lib/dpkg/info/policykit-1.postinst
/var/lib/dpkg/info/policykit-1.prerm
/var/lib/dpkg/info/policykit-desktop-privileges.list
/var/lib/dpkg/info/policykit-desktop-privileges.md5sums

ck-list-sessions output

Session3:
    unix-user = '1000'
    realname = 'David'
    seat = 'Seat1'
    session-type = ''
    active = FALSE
    x11-display = ':0'
    x11-display-device = '/dev/tty7'
    display-device = ''
    remote-host-name = ''
    is-local = TRUE
    on-since = '2012-02-12T18:19:17.076039Z'
    login-session-id = ''
Session1:
    unix-user = '1000'
    realname = 'David'
    seat = 'Seat1'
    session-type = ''
    active = TRUE
    x11-display = ':0'
    x11-display-device = '/dev/tty7'
    display-device = ''
    remote-host-name = ''
    is-local = TRUE
    on-since = '2012-02-12T18:18:19.735363Z'
    login-session-id = ''

Im stumped. :(

---

### Post by Aliarse on 2012-02-12
> **jayshomebrew said:**
> Are you connecting remotely, via NX ?  I think the default policy is to have that box greyed out for remote connections.
try a remote connection like this:

assuming your remote IP is: 192.168.1.100
```
ssh -X 192.168.1.100
gksu users-admin
```and you should be able to edit your users
ssh -X 192.168.1.100

Im running ubuntu 11.10 on my laptop im typing this on now, so no remote connection or anything like that as far as i know?

Edit - Whenever i open users-admin via terminal using sudo, all i get is the ubuntu spinning loading icon. The icon never stops spinning and no users are shown. Users are shown when opening it via the gui dropdown but then i cannot edit anything due to the unlock box being greyed out...

---

### Post by jamesisin on 2012-02-12
It sounds like something might be borked in sudo land.  Hopefully a sudo expert will happen along as this is not an area of great facility for me.

---

