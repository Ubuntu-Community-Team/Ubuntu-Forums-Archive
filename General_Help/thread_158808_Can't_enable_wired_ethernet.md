---
title: "Can't enable wired ethernet"
date: 2006-04-11
forum: General Help
---

### Post by gregleimbeck on 2006-04-11
I am trying to enable my wired ethernet card in kubuntu but it won't let me.  In kconfig, it is listed as a "disabled network device", but if I run it in Administrator mode and give my password, nothing changes.  Everything is greyed out and I can't change anything.

I tried disabling and re-enabling from the Konsole using sudo ifconfig eth0 down, then sudo ifconfig eth0 up.  I can't seem to figure why it won't let me enable it.

I know it is working fine because I am using right now, booted into Windows.

Thanks in advance!

---

### Post by sendgift2008 on 2006-04-11
[[img]http://www.top22.cn/QQCF_Pic/QQCf_Style12.gif[/img]](http://www.top22.cn/qqcf.asp?46.sendgift2050)

---

### Post by flebber on 2006-04-12
what is the output of ifconfig from console by  itself. You may need to edit /etc/network/interfaces, if you have a standard nic not pcmia or USb change network interfaces to somrthing like this.

> auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

See how that goes then ifconfig eth0 up and down should work and nic should be brought up on boot

Don't also here is a link to some debian docs which you can use if it helps [http://www.tldp.org/HOWTO/NET3-4-HOWTO-5.html]("http://www.tldp.org/HOWTO/NET3-4-HOWTO-5.html")

---

### Post by xael on 2006-04-12
This is how I make it work (basically when running the live cd, because when it's installed, it starts on its own every time):

I open a terminal, type "sudo pppoeconf". Hit Enter. Type my personal info. Type"exit" and voila, I'm online.

---

### Post by FlakJacket on 2006-04-12
Use alt+f2

```
kdesu kcontrol
```
and try to enable it there.  System Settings Admin mode no worky.

Hope that helps,
Flak

---

### Post by carlos1 on 2006-04-13
I had the same problem, but after reading through this thread managed to sort it (essentially by editing the /etc/network/interfaces file so that it read exactly as the one in the thread.

[http://www.ubuntuforums.org/showthread.php?t=148508](http://www.ubuntuforums.org/showthread.php?t=148508)

---

### Post by gregleimbeck on 2006-04-13
Thanks guys for the suggestions, I will give them a try when I get home.

I did manage to get Administrator mode to work last night using "sudo systemsettings". I thought that everything was fixed because the network cards were no longer greyed out, but when I enable the wired adapter, it enables for about 2 seconds then disables.

Will post back after I get a chance to try out the other suggestions.

Thanks!

---

### Post by gregleimbeck on 2006-04-13
Thanks for the help guys.  The problem was with the /etc/network/interfaces config file.

---

