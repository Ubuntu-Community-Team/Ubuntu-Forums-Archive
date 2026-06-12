---
title: "Standard Remote Desktop in ubuntu 10.10"
date: 2010-11-24
forum: General Help
---

### Post by elrond101 on 2010-11-24
ello

I've got 10.10 on my home server and win xp on desktop. Previoslu (in 10.04, ...) i used standard remote desktop (vino?) to access my server. I've installed tightvnc viewer on xp then 192.168.1.254 (ubuntu) and it works like a charm... now in 10.10 I'm doing the same thing but get only faild to connect.

What is wrong?

---

### Post by lmarmisa on 2010-11-24
Check the remote desktop preferences (System -> Preferences -> Remote Desktop) on your Ubuntu 10.10 home server.

---

### Post by elrond101 on 2010-11-24
yes, i've got it like on screen
also tryied with password and without password

---

### Post by lmarmisa on 2010-11-24
Do you use a firewall?.

Are you trying to connect to the remote desktop using the IP address or hostname?.

---

### Post by elrond101 on 2010-11-24
I don't use firewall (unless it is'n built in 10.10??)
i tried by name and by ip (both options are pingable)

I've also tried apt-get install tigtvncserver - then start tightvncserver and it works - but i've got problems with keybord (pressing "d" gives me "minimaze" on widows) and it is not stable for example i'am choosing some things in synaptic and it suddenly closess.

I've used standard rd in ubuntu 9.x and it never gave me problems like mentiond above

---

### Post by lmarmisa on 2010-11-24
I use the built-in VNC server of Ubuntu 10.10 and the client TightVNC in XP. It works just fine here.

Type these two commands in a XP terminal (5900 is the port for the VNC service):

```

ping 192.168.1.254
telnet 192.168.1.254 5900

```I attach the outputs of these commands that I got on my XP computer.

---

### Post by elrond101 on 2010-11-24
ok, must check

so it should work (i thoght mybe some bug in vino) - i will alsu recheck my router settings (i found in some post that disebling uPNP can help)

thx for info

---

