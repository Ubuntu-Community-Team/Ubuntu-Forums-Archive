---
title: "I changed my host name, and now I get an error message from sudo."
date: 2011-08-01
forum: General Help
---

### Post by ninjaaron on 2011-08-01
sudo still works, but every time I run it, it says it's unable to resolve the host.  I tried to change stuff in visudo, but there wasn't anything about the host as far as I could tell.

---

### Post by CharlesA on 2011-08-01
Edit /etc/hosts so that it has the new hostname.

---

### Post by tredegar on 2011-08-01
In my experience, changing the hostname requires a reboot.

---

### Post by CharlesA on 2011-08-01
> **tredegar said:**
> In my experience, changing the hostname requires a reboot.

I don't think you need to reboot, just restart networking, but a reboot wouldn't change the entry in the hosts file. :)

I reboot after a hostname change, just to be safe, but that's just me.

---

### Post by oldfred on 2011-08-01
Did you change both files?

Computer Name
Must do both & reboot right away
sudo gedit /etc/hostname
sudo gedit /etc/hosts
or
Ubuntu Tweak
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by ninjaaron on 2011-08-01
I did it with Ubuntu Tweak...  Anyway, sudo still works, I just get this message every time I run it:

[FONT="Courier New"]sudo: unable to resolve host CQ61[/FONT]

and I don't like it.

---

### Post by CharlesA on 2011-08-01
Post the output of this:

```
cat /etc/hosts
```

---

### Post by ninjaaron on 2011-08-01
> **CharlesA said:**
> Post the output of this:

```
cat /etc/hosts
```

There it was. Changed the file and it's fixed. Thanks!

---

### Post by ninjaaron on 2011-08-03
he... just kidding... "unsolved"

the file /etc/hosts keeps reverting every time I reboot...  I am wondering if this has any connection to the fact that the default icon set keeps appearing in my Unity launcher every time I reboot, and, most recently, my weather applet forgets my information and also has to be reset on boot.

P.S.  I'm installing Debian right now via netinstall. I have every expectation that it will be meh, but one has to try these things.  It has a "graphical" frontend, but it doesn't even recognise the proper screen resolution, and everything is just reading text and entering text.  Its the most direct "cli to gui" port I've seen, though I will admit that staring at the clean graphical layout for half an hour is easier on the eyes than the console... Oh... it just got done!  I am totally prepared to be under-whelmed by the boringness of stability!

edit: yeah... so those wifi drivers that were in the install environment... they don't come with the system... so I guess I'll just have to nab some debs with another os and drag them on over to Debian.  On the upside, it does come with twm as an available session from gdm...  hmm... I wonder if I could rip the unpacked kernel modules for the drivers right out of the installation medium and stick them in Debian... let's see if I can break the most stable distro out there on my first day with it... :p

edit edit:  Hold that thought, they are there... wlan0 just isn't talking to network manager for some reason, but it can be manually configured... hmm... Oh Debian, how you toy with me.

---

### Post by CharlesA on 2011-08-03
Sorry but lol @ Debian. It's great when it works, but sometimes there are problems. ;)

Hmm. Are you running any other software on this box outside of the OS? I read a post where cPanel was interfering with changing the hostname.

---

### Post by ninjaaron on 2011-08-04
> **CharlesA said:**
> Sorry but lol @ Debian. It's great when it works, but sometimes there are problems. ;)

Hmm. Are you running any other software on this box outside of the OS? I read a post where cPanel was interfering with changing the hostname.

I decided to snoop around the file system this morning. There is a file called /etc/hosts.ac, and it seems to rewrite the /etc/hosts file at boot.  Not sure what benefit this could possibly provide, but I changed it, and now life is wonderful, kinda.

Debian: shortly after this post, I accidently set on gnome panel on top of another and it made gnome freeze (I've done the same in Ubuntu with no problem), and made it freeze every time it tried to load the desktop, so I deleted gnome and installed KDE.  Then I remembered that KDE drives me crazy and I wiped the partition and started installing Gentoo, but I got bored while editing all of the system config files and so I wiped that too and restored my Ubuntu partition to it's original size.  What't the point of a "distro" if I'm doing all the work myself? Might as well be LFS...

---

### Post by CharlesA on 2011-08-04
> **ninjaaron said:**
> I decided to snoop around the file system this morning. There is a file called /etc/hosts.ac, and it seems to rewrite the /etc/hosts file at boot.  Not sure what benefit this could possibly provide, but I changed it, and now life is wonderful, kinda.

Interesting. I couldn't find any info on "hosts.ac."

---

### Post by ninjaaron on 2011-08-04
> **CharlesA said:**
> Interesting. I couldn't find any info on "hosts.ac."

Things have been a little weird on this machine lately.  I'm still all the default icons every time I boot.  I tend to tweak things until they break... but I'm not sure what could have generated a file like that. :(

---

### Post by paschy on 2011-08-11
I have the same "problem" and after putting an auditwatcher on this hosts.ac file i came to the conclusion that my cisco anyconnect vpn daemon is reading the .ac and overwriting the hosts file when it is startet:

```

type=PATH msg=audit(11.08.2011 23:10:27.869:24) : item=0 name=/etc/hosts.ac inode=266084 dev=08:07 mode=file,644 ouid=root ogid=root rdev=00:00 
type=CWD msg=audit(11.08.2011 23:10:27.869:24) :  cwd=/ 
type=SYSCALL msg=audit(11.08.2011 23:10:27.869:24) : arch=i386 syscall=open per=400000 success=yes exit=23 a0=9429254 a1=0 a2=1b6 a3=9420100 items=1 ppid=1 pid=1537 auid=unset uid=root gid=root euid=root suid=root fsuid=root egid=root sgid=root fsgid=root tty=(none) ses=4294967295 comm=vpnagentd exe=/opt/cisco/vpn/bin/vpnagentd key=hosts-watcher

```the question now is WHY.

WHY is Cisco VPN-Daemon touching my hosts file?!

---

