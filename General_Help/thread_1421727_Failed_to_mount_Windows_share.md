---
title: "Failed to mount Windows share"
date: 2010-03-04
forum: General Help
---

### Post by gratefulfrog on 2010-03-04
Hi!
I'm trying to access shared directories on a WIN/XP box in my home lan and get that message.

I can access other shared directories on a Win-7 box, but not those on the old WIN/XP box.

Any ideas of where to start to debug this?

Thanks,
GF.

---

### Post by Morbius1 on 2010-03-04
That's different. It's usually the other way around - you can access WinXP but not Win7.

Here's a set of commands that will aid in the diagnosis:

On the Ubuntu box:

Open **Terminal**
Type **smbtree**
Type **findsmb**
Type **nmap -sT 192.168.0.100/22**
*[COLOR=Blue]Change 192.168.0.100 to the ip address of the ubuntu machine you're using.[/COLOR]*

You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do. Once it's installed run the nmap command again.

smbtree / findsmb will show you your entire network all all available shares. More importantly it will also output error messages if something isn't right. With the error message either someone here has seen that  before and found a fix or can be searched in this forum or googled.

The nmap command will list all your network machines by ip address and also list open ports. This is an indirect way of finding out if the WinXP has a firewall or in some cases an overactive antivirus in the way.

BTW, have you tried to access the WinXP box directly by either machine name or ip address instead of browsing for it.

---

### Post by gratefulfrog on 2010-03-04
Thanks for your help, Morbius1.

I ran those commands and the results are even worse than I expected. I don't even see the Win/7 machine (172.19.3.3). But I do see the router (172.19.3.1) and my skype phone (172.19.3.5)

Here's the results:
```

~$ smbtree
Password: 
~$ 
~$ findsmb
                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
~$
$ nmap -sT 172.19.3.4/22

Starting Nmap 4.53 ( http://insecure.org ) at 2010-03-04 22:52 CET
Interesting ports on 172.19.3.1:
Not shown: 1707 closed ports
PORT     STATE SERVICE
23/tcp   open  telnet
80/tcp   open  http
443/tcp  open  https
992/tcp  open  telnets
8080/tcp open  http-proxy
8443/tcp open  https-alt
8888/tcp open  sun-answerbook

Interesting ports on 172.19.3.4:
Not shown: 1708 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
901/tcp  open  samba-swat
8081/tcp open  blackice-icecap

Interesting ports on 172.19.3.5:
Not shown: 1711 closed ports
PORT    STATE SERVICE
23/tcp  open  telnet
80/tcp  open  http
443/tcp open  https

Nmap done: 1024 IP addresses (3 hosts up) scanned in 44.868 seconds
~$

```

At the same time, in gnome, I can enter "smb://172.19.3.3/users/" and open the files there!

I have no idea what is wrong or where to start...

Thanks for any more ideas!
GF.

---

### Post by Morbius1 on 2010-03-04
Well that's very confusing output.

smbtree shows nothing - not even the Win7 machine that works.

The only machine not listed in nmap is 172.19.3.3 ( I'm assuming that's the WinXP machine ? ) and yet you just accessed it.

Until I or someone else can figure this one out I have a suggestion:

Once you go to smb://172.19.3.3 in Nautilus, Bookmak it.
On the top of nautilus there is a tab labeled "Bookmarks" > Add Bookmark.

It will then show up under "Places" sort of like a "mapped drive" does in Windows. You can even rename it there to WinXP or something.

---

### Post by gratefulfrog on 2010-03-05
> **Morbius1 said:**
> 
The only machine not listed in nmap is 172.19.3.3 ( I'm assuming that's the WinXP machine ? ) and yet you just accessed it.


Actually, both the Win/XP and the WIN/7 machines are not listed.

I can **only **access the WIN/7 machine. 

I can see the shared directories on the WIN/XP machine in gnome, but get the "Failed to mount Windows share" message after the password dialog, when I double-click them.

172.19.3.4 is the Ubuntu machine.

Thanks for your help, I'm not holding my breath while waiting for a solution ;-)
GF

---

