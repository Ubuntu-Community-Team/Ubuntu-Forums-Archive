---
title: "How to disable ipv6 in karmic?"
date: 2009-10-31
forum: General Help
---

### Post by AussieGuy69 on 2009-10-31
I need to disable ipv6 in karmic. Ive had strange DNS issues as a result of it. I know this because as soon as I disable ipv6 in firefox everything works.

Konqueror, other internet applications think most popular domain names have the ip of 1.0.0.0 .

How do I remove ipv6 from my machine?

-Aussieguy

---

### Post by AussieGuy69 on 2009-10-31
Fixed it.

Added the option to turn ipv6 off at the grub boot line for my kernel.

---

### Post by Sinsemila on 2009-10-31
May I ask how you fixed it. I can't work out how to edit the new Grub 2 file. Before I could just use gksudo gedit /boot/grub/menu.lst but that doesnt work anymore with Grub 2.

---

### Post by Laminebean on 2009-10-31
Yes I also need to disable it. Could you share how you managed to disable it in Grub?

---

### Post by grandtoubab on 2009-10-31
sudo gedit  **/etc/default/grub** 
add **ipv6.disable=1**  between "" at the  **GRUB_CMDLINE_LINUX=""** 
run command **update-grub**

refer to
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Laminebean on 2009-10-31
When I type in that command, gedit opens a blank document and Terminal just hangs on me. I know the grub file is there because I can see the contents in 'read only'...

Anyone got any ideas on how to get around this problem?

---

### Post by jessjesseeee on 2009-11-01
You need super user privileges to edit the file.

try: ```
gksu gedit /etc/default/grub
```

---

### Post by grandtoubab on 2009-11-01
that one is ok too for Karmic
[http://www.webupd8.org/2009/05/how-to-disable-ipv6-in-ubuntu-jaunty.html](http://www.webupd8.org/2009/05/how-to-disable-ipv6-in-ubuntu-jaunty.html)

---

### Post by nilarimogard on 2009-11-02
You forgot the .html part of the above link :)

---

### Post by AussieGuy69 on 2009-11-04
To disable ipv6 I added ipv6.disable=1 to the end of the "kernel" line in the section for my favorite kernel in /boot/grub/menu.list.

Mine is below (do not copy and paste the entire code as it has the wrong UUID for your device), just copy the ipv6.disable=1 part.

title           Ubuntu 9.10, kernel 2.6.31-14-generic no ipv6 
root            (hd0,1) 
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=94cffa36-dff0-4eb8-85b7-8aca88cda3f5 ro quiet splash ipv6.disable=1 
initrd          /boot/initrd.img-2.6.31-14-generic 
quiet

---

### Post by jago25_98 on 2009-11-28
I've done this... and this:
[http://digitizor.com/2009/11/04/ubuntu-karmic-internet-connection-woes-3-ways-to-disable-ipv6/](http://digitizor.com/2009/11/04/ubuntu-karmic-internet-connection-woes-3-ways-to-disable-ipv6/)

yet firefox works now that ipv6 is disabled and I'm still getting 1.0.0.0

```
j@idpp-0644:~$ ping yahoo.com
PING yahoo.com (209.131.36.159) 56(84) bytes of data.
64 bytes from yahoo.com (209.131.36.159): icmp_seq=1 ttl=56 time=159 ms
^C
--- yahoo.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 159.724/159.724/159.724/0.000 ms
j@idpp-0644:~$ sudo apt-get update
0% [Connecting to archive.ubuntu.com (1.0.0.0)]

```

So I had to ping what I wanted to connect to first, to clear the DNS cache I presume

---

