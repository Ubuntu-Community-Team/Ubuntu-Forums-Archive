---
title: "schroot + debootstrap + apache = ???"
date: 2011-04-21
forum: General Help
---

### Post by earthpigg on 2011-04-21
Well, I've created a fake debian squeeze system on my ubuntu desktop 10.10 and it seems to be working:

```
fake@chris-desktop:~$ sudo apt-get update
[sudo] password for fake: 
fake is not in the sudoers file.  This incident will be reported. **<-- demonstrating that we're using Ubuntu at this point.**
fake@chris-desktop:~$ schroot -c fakedebian -u root
root@chris-desktop:~# apt-get update
Hit http://ftp.us.debian.org squeeze Release.gpg **<-- we're in Debian now**
Ign http://ftp.us.debian.org/debian/ squeeze/main Translation-en
Hit http://ftp.us.debian.org squeeze Release
Hit http://ftp.us.debian.org squeeze/main i386 Packages
Reading package lists... Done
root@chris-desktop:~# 
```

So, I can play around with apache2 and some other server stuff and have very little risk of breaking my computer - user "fake" is not a sudoer and can thus only break things for himself.

I installed apache2 in the fake debian machine and, on my real machine, went to 127.0.0.1 in the web browser:

> It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

Then, I went to my public-facing IP address [http://75.xx.xx.xxx/](http://75.xx.xx.xxx/)

and, the same web page is being served. from apache from inside a schroot debian install from a non-sudo non-root user.

Cool! that is pretty much what i wanted to be able to do.

My question now, is this:

I have a friend that has a real virtual server hosted elsewhere and, like me, really doesn't know much about what he is doing.

He'd like to let me play around on it without giving me root or sudo access (very reasonable) and I was thinking this would be the way to go. 

However, what happens when both apache2 on the VM are running, as well as apache2 on the VM inside the schroot environment? 

are we going to bump heads? 

can he configure his real ubuntu 10.04 server so that the schroot's install of apache2 is only given [http://domain.name.com/earthpigg](http://domain.name.com/earthpigg) and not [http://domain.name.com/](http://domain.name.com/) ??

Does this all make sense?

(my google abilities for this problem are limited by the fact that i cannot articulate into a single sentence.)

---

### Post by earthpigg on 2011-04-21
related question, and probably a zillion times more important:

why is this web page being served even though i've logged out of the schroot environment and, as far as i know, debian isn't running at the moment...?

```
[chris: ~]$ users
chris chris
[chris: ~]$ sudo ps -A | grep apache
19897 ?        00:00:00 apache2
19899 ?        00:00:00 apache2
19900 ?        00:00:00 apache2
19901 ?        00:00:00 apache2
19902 ?        00:00:00 apache2
19903 ?        00:00:00 apache2
20179 ?        00:00:00 apache2
20842 ?        00:00:00 apache2
[chris: ~]$ sudo service apache2 stop
apache2: unrecognized service
[chris: ~]$ 

```

I do ***not*** have apache2 installed except on the fake debian install. 

Yet, I still have to login to the fake install to shut down? and, neither 'shutdown' nor 'shutdown now' seem to be doing anything to shut down the fake debian install...

have i activated skynet?

---

### Post by bodhi.zazen on 2011-04-21
I do not know without looking at your system, but for what you are wanting (a VPS) I would suggest openvz or lxc ;)

Personally I really like openvz, and I use Proxmox. Proxmox is Debian + KVM + openvz with a very user friendly web interface.

[http://www.proxmox.com/products/proxmox-ve](http://www.proxmox.com/products/proxmox-ve)

Running apache in a chroot is also possible, but you get better isolation with either openvz (best isolation) or LXC.

It is relatively easy to break out of a chroot or LXC if you have root access, much more difficult with openvz.

A more detailed answer: How did you configure your chroot ? Did you give your chroot an ip address ? Do you know how to do that ?

In the chroot, apache is going to run on the host kernel, so it will show in ps -aux (same with LXC last I looked).

When you chroot you do not actually boot the chroot, you change root, and run bash. When you log out, the bash session ends, and apache continues to run as a daemon (if that makes sense).

Did I mention openvz will give you better isolation?

---

### Post by earthpigg on 2011-04-22
it does make sense, and you did mention openvz. ill look at that and lxc. :)

I created the chroot enviornment this way:
debootstrap squeeze /home/fake/chroot [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian)

User 'fake' is not a sudoer, but he was included in schroot.conf as being allowed to schroot into that debootstrap as root.

i did not give it an ip address, nor do i know how to.

---

### Post by bodhi.zazen on 2011-04-22
Support for LXC is supposed to have improved on Ubuntu 11.04 =)

If you stay with a chroot, I can shoe you how to set an ip address, do ou have one or more then one network card ?

---

### Post by earthpigg on 2011-04-23
> **bodhi.zazen said:**
> do ou have one or more then one network card ?

On my desktop? I have a wireless NIC, and the motherboard has ethernet on it.

On my buddies VNC that this is supposed to be a test-run for? No, I don't think he has access to more than one network card or IP address.

---

### Post by bodhi.zazen on 2011-04-24
Here is a nice blog about assigning more then 1 ip address to a NIC, I do not know if it works for wireless or not.

[http://shibuvarkala.blogspot.com/2008/10/howto-setup-second-ip-address-or.html](http://shibuvarkala.blogspot.com/2008/10/howto-setup-second-ip-address-or.html)

Using your chroot, have apache listen on the second ip address.

---

### Post by earthpigg on 2011-04-24
thank you! ill take a look over the next few days.

---

