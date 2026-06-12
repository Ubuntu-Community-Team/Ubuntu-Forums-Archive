---
title: "Giving users certain root privileges"
date: 2009-12-02
forum: General Help
---

### Post by blueshiftoverwatch on 2009-12-02
I'm trying to run Wireshark but I can't do anything with it unless I have root privledges.

When I use sudo to open up Wireshark my entire computer completely freezes several second after. Not even the virtual terminal (ctrl+alt+F5) which I use to shut down misbehaving apps works.

So I have two questions:
1. Is there a way that I can give my user permanent permission (without asking each time using sudo) to access Wireshark?

2. Is doing so that much of a security risk that I wouldn't want to do it?

---

### Post by Some Penguin on 2009-12-02
Off-hand, I suspect that you could

1) create a group called, say, sharkers
groupadd sharkers                       # this and other commands will need to be run as root

2) add yourself to it
(via editing /etc/groups) --

sharkers:x:some_number:your_user_id

3) allow sharkers and only sharkers to run wireshark
chown root.sharkers /usr/bin/wireshark            # now owned by root user/sharkers group
chmod ug+rx /usr/bin/wireshark                      # user/group: + read/execute
chmod o-rwx /usr/bin/wireshark                       # other:         - read/write/execute


4) make the wireshark binary suid-root e.g.
chmod u+s /usr/bin/wireshark                          # SUID bit (switch user id)

You will need to log out/log back in to get yourself recognized as a 'sharker'.

(this command means that running wireshark would be done effectively as root, no matter who is running it -- which is why steps 1-3 are there to limit who can run it).  Note that if there's a way to execute other programs from wireshark, that execution would also be done as root, since wireshark is probably not written to drop privileges.


Although if you're the only person with any access, you could skip 1-3.  If you *aren't*, then steps 1-3 are probably a good idea unless you very much trust wireshark and/or the other users.  Likewise, if you're already a member of group consisting only of trusted users, you could skip 1 and 2, and substitute it for sharkers.

I'm not particularly familiar with wireshark, but as long as you stop other users who lack sudo access from running the suid binary, it's not more dangerous than you running it as root via sudo.

---

### Post by bodhi.zazen on 2009-12-02
> **blueshiftoverwatch said:**
> I'm trying to run Wireshark but I can't do anything with it unless I have root privledges.

When I use sudo to open up Wireshark my entire computer completely freezes several second after. Not even the virtual terminal (ctrl+alt+F5) which I use to shut down misbehaving apps works.

Not sure why this is happening, but, you should use gksu for graphical apps.

> So I have two questions:
1. Is there a way that I can give my user permanent permission (without asking each time using sudo) to access Wireshark?

IMO easiest way is to configure sudo to allow you to run wireshard without a password, you would still use gksu ;)

Again I doubt the problem is with the sudo part.

> 2. Is doing so that much of a security risk that I wouldn't want to do it?

Well, it is a security risk as wireshark is running as root , so if wireshark is compromised you are in trouble. 

The other issue would be if you were in a multiuser environment, and anyone could run wireshark, that would mean anyone could potentially monitor your network traffic.

---

### Post by sisco311 on 2009-12-02
> **blueshiftoverwatch said:**
> I'm trying to run Wireshark but I can't do anything with it unless I have root privledges.

When I use sudo to open up Wireshark my entire computer completely freezes several second after. Not even the virtual terminal (ctrl+alt+F5) which I use to shut down misbehaving apps works.

I doubt that the problem is related to sudo.

> **blueshiftoverwatch said:**
> 
So I have two questions:
1. Is there a way that I can give my user permanent permission (without asking each time using sudo) to access Wireshark?


Yes, edit the sudoers file:

[thread=1132821]HowTO: Sudoers Configuration[/thread]

---

### Post by blueshiftoverwatch on 2009-12-02
> **Some Penguin said:**
> Off-hand, I suspect that you could
I tried what you said (only with my group, not the sharkers group) but it didn't work.
> **bodhi.zazen said:**
> Not sure why this is happening, but, you should use gksu for graphical apps.
The same thing happens when I use sudo as gksudo.
> **bodhi.zazen said:**
> Well, it is a security risk as wireshark is running as root , so if wireshark is compromised you are in trouble.

The other issue would be if you were in a multiuser environment, and anyone could run wireshark, that would mean anyone could potentially monitor your network traffic.
I'm the only user on my computer. But in reality, anything sent over my network that's not encrypted could be monitored. So if someone wanted to spy on me they would probably do so from a different point.
> **sisco311 said:**
> Yes, edit the sudoers file:
[thread=1132821]HowTO: Sudoers Configuration[/thread]
I'll look at that.

---

### Post by doas777 on 2009-12-29
it is my understanding that wireshark does require certian features that my not be found in low end cards. that may be the source of your hang, but as bodhi pointed out, you shoudl use gksu instead.

---

### Post by blueshiftoverwatch on 2009-12-29
> **doas777 said:**
> it is my understanding that wireshark does require certian features that my not be found in low end cards. that may be the source of your hang, but as bodhi pointed out, you shoudl use gksu instead.
I used Wireshark on OpenSUSE 11.2 with no problems. Although I'm switching back to Ubuntu because I can't stand RPM package management. So I'll give it another go when I get Ubuntu 9.10 back on my computer.

---

### Post by blueshiftoverwatch on 2009-12-30
I made another thread [here]("http://ubuntuforums.org/showthread.php?t=1351941") two weeks ago, as opposed to the 4 weeks ago this one was made. So if anyone's following this, post there instead of here. It's not a permissions problem.

---

