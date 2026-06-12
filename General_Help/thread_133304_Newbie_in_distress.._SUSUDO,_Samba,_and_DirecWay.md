---
title: "Newbie in distress.. SU/SUDO, Samba, and DirecWay"
date: 2006-02-19
forum: General Help
---

### Post by asbo on 2006-02-19
Hey there,

I'm pretty much brand new to Linux as a whole -- I have a little bit of experience but nothing substatial.

I recently put Breezy on one of my boxes to act as an ICS host for my DirecWay 1-Way Dish setup, and I've had some troubles so far. Let's begin, shall we? :)


**1)** I've read up on the whole root issue with Ubuntu, and I'm fairly certain I understand it and how to use sudo properly and all that. However, when I try to run anything that requires root privledges, i.e. anything under System > Administration, I can't get anything to launch. The prompt comes up, and to my understanding this is where I enter MY password, and so I did. Except that it takes it, and not a thing happens. With some programs, `Start xyz` shows up in the taskbar, but then goes away and all is quiet. Just for kicks I tried the root password, and as expected it returned an invalid password error. I've circumvented this problem by opening up a terminal, su'ing to root, and running what I need that way, which returns (from network-admin in this case):> (network-admin:18344): GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.but launches network-admin anyhow. So what am I doing wrong??

**2)** I know that samba can be used for sharing on a Windows/Linux network, and I actually installed both file-sharing possibilities when Ubuntu prompted me (I don't recall the name of the other Unix/Linux one ..). Anyhow, I managed to create a share, and my Windows boxes can see it, but when any of them try and browse to it, they get:
[img]http://www.iserv.net/~asbo/dwulogin.jpg[/img]
I've tried all combinations of usernames with their proper names, prefixed by the workgroup name and not, and no good whatsoever. What am I doing wrong HERE?

**3)** This is probably my biggest hangup. I've searched around a little bit so far, but I've not found a whole lot of information on the [DirecPC Linux drivers](http://sourceforge.net/projects/direcpc), specifically with Ubuntu. I've tried to go through the INSTALL file, but I get hung up before I really get anywhere. I've got the White dish, and I'm pretty lost as to which values I need to assume, or how I'd go about retreiving and converting said values from my ACM files. Additionally, where is the Linux source in Ubuntu; it's not in /usr/src/linux. After that .. what are `make` and `make install`? I figure that's something like compiling, but from the terminal neither are recognized by bash. The author talks about KBuild, but that sounds like a KDE program, which I don't have anyhow. So what do I do here?


I know the solutions to these are probably ridiculously simple, and I expect I might even earn the coveted RTFM but I thought I oughta post where there's people who actually know what they're doing anyhow. Anyway, I appreciate you taking your time to read this.

Thanks in advance.
[] asbo

---

### Post by mr_ed on 2006-02-20
I don't know what to say for #1.  My root account is disabled.

#2, I can happily give you some answers.  Unfortunately it's not obvious.

Firstly, do you want usernames and passwords at all?  If you don't, then edit 
/etc/samba/smb.conf with your favourite editor and change security=user to security=share.  Then restart samba (sudo /etc/init.d/samba restart) and add a share.

If you want user authentication, I'm not exactly sure of the details, but you need to add usernames and passwords with smbpasswd.  Why they don't use the standard UNIX account is beyond me.

#3, I don't own a DirecPC, but if you want to be able to build stuff, you have to run "sudo apt-get install build-essential" to get past that.  The Linux source isn't actually installed by default.  If you just need the headers, install linux-kernel-headers.  If you need the whole source tree, install the linux-source package.

HTH,
Jeramy

---

### Post by asbo on 2006-02-20
Thanks for replying.

I've looked around a bit more, still nothing on #1.

#2: Yeah, I was looking around and I found the bit about 'security = user' in addition to an option like so: 'allow users = 192.168.0'. The login box still comes up but as long as I enter a proper user then all is dandy. Ideally I could skip the login dialog altogether, but that's just being nit-picky. The fact that it works is good enough.

#3: Thanks for the advice, I'll look into that and get back to you.


Thanks,
] asbo

[edit: I attached my smb.conf, for reference/review]

---

### Post by RAOF on 2006-02-20
[QUOTE=asbo]...Just for kicks I tried the root password, and as expected it returned an invalid password error. I've circumvented this problem by opening up a terminal, su'ing to root, and running what I need that way, which returns (from network-admin in this case):but launches network-admin anyhow. So what am I doing wrong??...[/QUOTE]
Wait, you **have** a root password?  Did you use the "expert" install, or something like that?  By default, Ubuntu doesn't allow you to login as root.  Does sudo work for you at all?  If not, check that your /etc/sudoers file looks like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root        ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin        ALL=(ALL) ALL
```
and that you are a member of the admin group, by running "groups" on a terminal.

---

### Post by asbo on 2006-02-21
Yes, I chose the expert install and specified my own root password. And I can't technically login as root without disabling all the mechanisms designed to prevent me from doing so first.

Using [FONT="Courier New"]sudo[/FONT] has the same result I describe pertaining to the System > Administration menu .. I enter, for example, [FONT="Courier New"]sudo network-admin[/FONT] and then my password, and not a thing happens. No error, no program, I just return to the prompt.

My [FONT="Courier New"]/etc/sudoers[/FONT] file didn't have the line about the [FONT="Courier New"]admin[/FONT] group, so I added it, but apparently my normal user ([FONT="Courier New"]dwserver[/FONT]), isn't in the group anyway:
[FONT="Courier New"]dwserver adm dialout cdrom floppy audio dip video plugdev lpadmin scanner[/FONT]

So what do I do now? :\

---

### Post by asbo on 2006-02-23
Status update:

**1)** I've completely resolved the issue. Taking what RAOF gave me and wisening up a little bit, I added my user (dwserver) to my /etc/sudoers file in a fashion simular to root and all was fine and dandy. My /etc/sudoers:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
dwserver	ALL=(ALL) ALL
```

**2)** Resolved thanks to help from mr_ed, except for the login dialog at which I have to enter dwserver and no password. No biggie, but if someone knew how to get rid of it entirely, I'd appreciate enlightenment.

**3)** Well, I can compile now, but it graces me with a billion and a half errors, so I think I'm going to contact the author about this one.


] asbo

---

