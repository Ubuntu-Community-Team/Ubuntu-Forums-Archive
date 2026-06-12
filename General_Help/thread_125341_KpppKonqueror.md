---
title: "Kppp/Konqueror"
date: 2006-02-03
forum: General Help
---

### Post by phil66 on 2006-02-03
Kubuntu Breezy 5.10
Dial-up external serial modem
Duel boot system W/Window ME

I had Kubuntu operating and was trying to make a change to k3b when a command for apt-get removed base system. Completely uninstalled and reinstalled.
Now I cannot get Konqueror to retreive websites Message Error when loading website unknown host.

Modem connecting to system ping shows x transmitted and x received and 0% loss. Install Knoppix and Ubuntu live cd's and configured modem the same as Kubuntu they retrieved website that Kubuntu would not.

I have not installed any firewall and cannot find any in Kubuntu.This distro was working fine prior to my screw-up.

Your help will be appreciated
Ray

---

### Post by Velvet Elvis on 2006-02-03
Do any other net aps work or is it just Konqueror?

Check your DNS settings in KPP.

Also try connecting to your ISP with wvdial.  Run wvdialconf first and then wvdial, both inside a konsole.

---

### Post by phil66 on 2006-02-04
Thanks for the reply
Apt-get or fetch update are also not working.
The dns in auto shows the same address as the manual I entered.
From Konsole the wvdial.conf shows there are no such files or directory
wvdial looks for wvdial.conf when not found exits.

Info from syslog shows all kppp systems connected sucessfully.
Any suggestions will be appreciated.

By the was I have done a complete reinstall and no difference.
Ray

---

### Post by GeneralZod on 2006-02-04
Does 

```

ping 216.239.59.104

```

work?

---

### Post by Greg2 on 2006-02-04
[QUOTE=phil66]
Now I cannot get Konqueror to retreive websites Message Error when loading website unknown host.[/QUOTE]
You could have simply borked your /etc/host file? Did you check it?

---

### Post by phil66 on 2006-02-04
Generalzod

Pinged 216.239.59.104 and before shutting it down transmitted 15 and recieved 14 with 0% loss

Yesterday I pinged addresses from google .com with same results
66.249.93.99 linux
66.249.93.104 Linux
66.102.9.104 unknown
64.233.183.147 unknwn

All pings showing good results no error messages.
Thanks 

Ray

---

### Post by phil66 on 2006-02-04
Greg 2

/Etc/host

127.0.0.1  localhost  local domain localhost ubuntu
::1      ip6 localhost ip6-loopback
fe00:0 ip6 local net
ff00:0  ip6 acast prefix
ff02:1  ip6 allnodes
ff02:2  ip6 all routers
ff02:3  ip6 all host

This is what I found should ip6 be used instead of ip4?
Thanks
Ray

---

### Post by Greg2 on 2006-02-04
That looks ok to me if ‘ubuntu’ is/was your host name? If the base system was reinstalled (as you have stated), it could have gave your system the default hostname ‘ubuntu’? In which case if you were not previously using the default hostname ‘ubuntu’, Konqueror or apt-get would not work.

There are some spaces that should not be there; 'local domain' should be 'localdomain', etc.

---

### Post by phil66 on 2006-02-04
Greg 2

The host file is not correct as far as spacing in my thread
I retyped to this thread as I could not paste and copy.
Do you need the exact spacing and wording.

I did a delete of the partition with fdisk that Kubuntu was installed on.
When I reinstalled the program told me it was formatting the disk space I wanted to use.

Yes the host name is different as I was using localhost on the previous

Thanks
Ray

---

### Post by Greg2 on 2006-02-04
[QUOTE=phil66]
Yes the host name is different as I was using localhost on the previous[/QUOTE]
When you open your terminal does it say:
ray@localhost or ray@ubuntu?
or whatever you use instead of ray?
If it says localhost then the last entry in the first line of your hosts file must match. Do you understand?

Open your terminal and do:```
cat /etc/hosts
```does it match?

---

### Post by phil66 on 2006-02-04
Greg

When I open Konsole it say username@ubuntu

First line of /etc/host is localhost       ubuntu

Hostname file  list  Ubuntu

One more bit of info I found today When using addresses from google that I used to ping If I insert then in Konqueror it opens google search page.
I can then add name to search and it opens page. When I try to click on a link it returns a unknown host error.
Ray

---

### Post by wanger123 on 2006-02-04
Hi Ray, please show us your /etc/resolv.conf, /etc/network/interfaces, and /etc/ppp/peers/kppp-options files. 

It sounds as though it is trying to use some old or incorrect DNS servers in the etc/resolv.conf file. Did you use it with wireless or ethernet at some time in the past?

[EDIT] When I say Ray of course I mean Phil (sorry about that) :-)
wanger

---

### Post by phil66 on 2006-02-04
Greg

When I open Konsole it says username@ubuntu

cat /etc/hosts  brought up Localhost   ubuntu

File hostname  also list  Ubuntu

Addational info I can use a google address in Konqueror the same ones I used to ping and it will open google I can add a name to the search bar and it will open a page. I try to click on a link and it brings back Host unknown.

Ray

---

### Post by phil66 on 2006-02-04
Wanger

No problem with name familar name is "Ray"

I have only dial-up no wireless or ethernet no networks

/etc/resolv.conf
nameserver 216.119.128.9
nameserver 216.119.128.10
These were give to me by ISP when problem evolved
When using auto detect syslog show the same adddresses

/etc/network/interface
# The loopback network interface auto lo
iface lo inet loopback

/etc/ppp/peers/kppp-options
#noauth

Thanks for the reply all suggestions welcomed
Ray

---

### Post by wanger123 on 2006-02-04
Ok, I don't think this will work for you, but I had to remove the # from noauth.

My etc/ppp/peers/kppp-options file is:

noauth
defaultroute
replacedefaultroute

the last two entries are because I use an ethernet card at work.

But I think your connection would crash immediately if you really needed to remove the # from #noauth

Stick with us but, and we'll sort it!

wanger

---

### Post by wanger123 on 2006-02-04
Just another thought, what happens if you comment out your first nameserver in etc/resolv.conf?

wanger

---

### Post by Greg2 on 2006-02-05
[QUOTE=phil66]
I have only dial-up no wireless or ethernet no networks

/etc/resolv.conf
nameserver 216.119.128.9
nameserver 216.119.128.10
These were give to me by ISP when problem evolved[/QUOTE]
Wanger's post has me thinking that perhaps your /etc/resolv.conf has lost the write permission for kppp?

So open your terminal and do:```
sudo chmod 644 /etc/resolv.conf
```
Then make a new connection with your isp and check it again. It should have 'something' like this:

nameserver 216.119.128.9  #kppp temp entry
nameserver 216.119.128.10  #kppp temp entry

It could also say # ppp temp entry

Give that a try.

---

### Post by phil66 on 2006-02-05
Morning Greg

Summary of permissions before and after sudo chmod 644 /etc/resolv.conf
Before
Ownersip- User-root  Group-root
Access permissions - owner-view-modify   group-can view  other-can view
Advanced-user show entry-write entry-enter-no setuid
               group-show entry-write entry-enter no gid
               other-show entry-enter no sticky
After entering sudo chnod 644 /etc/resolv.conf
 Enter from group and user removed-write enter from group removed
Current permission code drw-r--r-- Unfamiliar with number code how does it relate to alphabet.

Opened kppp and attemped to load websites from Konqueror error message unknown host error in loading websites.

opened /etc/resolv.conf  file named resolv.conf.tmp when opened no data on screen. file before opening showed dns addresses without any addition data

Thanks for the suggestions they are always welcome and appreciated
Ray

---

### Post by phil66 on 2006-02-05
wanger

Tried both suggestions with no success.

Thanks for the continued help
Ray

---

### Post by Greg2 on 2006-02-06
[QUOTE=phil66]
Opened kppp and attemped to load websites from Konqueror error message unknown host error in loading websites.[/QUOTE]
I still believe the problem is in the hostname.

I did a little searching and found you were trying to get help on cnet forums... I would suggest you also try linuxquestions.org.

I'm sorry I can't offer any more help (I'm out of ideas), so I'm going to give you a few links to check out:
[http://www.linuxquestions.org/questions/](http://www.linuxquestions.org/questions/)
[http://www.cpqlinux.com/hostname.html](http://www.cpqlinux.com/hostname.html)
[http://gershwin.ens.fr/vdaniel/Doc-Locale/Outils-Gnu-Linux/Kde/kppp/kppp-4.html](http://gershwin.ens.fr/vdaniel/Doc-Locale/Outils-Gnu-Linux/Kde/kppp/kppp-4.html)
[http://www.maxpc.co.uk/tips/default.asp?pagetypeid=2&articleid=4550&subsectionid=714](http://www.maxpc.co.uk/tips/default.asp?pagetypeid=2&articleid=4550&subsectionid=714)

Good luck, and let us know what the problem was.

---

### Post by phil66 on 2006-02-06
Greg

Thanks for the help it was much appreciated.

When I finally solve this mystery I will let everyone in on the solution

Thanks again
Ray

---

### Post by phil66 on 2006-02-18
Greg

I finally found the problem with no web from Kppp

When starting Kppp you have to make a file /etc/resolv.conf

This file ended up in the wrong directory. When I redone it in the correct directory all problems were corrected.

This post is being submitted using Kubuntu Breezy.

Thanks again for your help

Ray

---

### Post by Greg2 on 2006-02-18
[QUOTE=phil66]Greg

I finally found the problem with no web from Kppp

When starting Kppp you have to make a file /etc/resolv.conf

This file ended up in the wrong directory. When I redone it in the correct directory all problems were corrected.

This post is being submitted using Kubuntu Breezy.

Thanks again for your help

Ray[/QUOTE]
I’ve been thinking that maybe you gave up on it... but you didn’t.

I’m glad you have things sorted out, and it’s working for you! :D

---

