---
title: "SAMBA and 9.10"
date: 2009-12-01
forum: General Help
---

### Post by notsofamiliar on 2009-12-01
Hi all,

Recently started to try and get SAMBA working on my Kamic machine but I've had nothing but issues.  I've used the Nautilus plug in, tried to hack the smb.conf file, and played with firewall settings, but am getting no joy at all.  I've even gone through and removed all SAMBA packages and re-installed in case I've screwed up somewhere.

What I've done:

Read and implemented most of this: 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
Read and implemented this: [https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html)
Read and implemented this:
[http://ubuntuforums.org/forumdisplay.php?f=125](http://ubuntuforums.org/forumdisplay.php?f=125)
Read through and tried to use this:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html)

As well as reading various SAMBA doco (man page of how many lines??) throughout the web.

What I'm seeing:

I can see the share that I've defined when i map to the server from any of my Windows machines.  As soon as I try to open the share I get a generic "The network path was not found" error (from both XP and 7).

I can post up my smb.conf if needed, but please help!

---

### Post by notsofamiliar on 2009-12-03
Anyone??

---

### Post by Lumberg on 2009-12-08
I'm having the exact same problem.  Any help?

---

### Post by gglaser on 2009-12-09
I am having the same problem too.

---

### Post by audiomick on 2009-12-09
Sorry I can only give you more stuff to read.
This thread is a good place to look:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by AKADAP on 2009-12-09
Does your computer have more than one network port?
If so, try disabling the ports you are not using. 

I found that for some reason samba preferred to attach itself to the port I was not using. disabling the unused port eliminated the possibility of it connecting to that port.

---

### Post by john newbuntu on 2009-12-09
The one thing I would suggest is to disable all your firewalls.  :? 
I know it sounds weird but just to get it working disable your windows and linux(ufw?) firewalls and see if you are able to get it to work that way.  If it works, then start enabling the ports/ip for samba connections.

---

### Post by gglaser on 2009-12-11
All - thanks very much for the posts. I ended up finding something that worked for me. I'm posting it here because it's a little different than what I found in most of the how-to's:
 
In the smb.conf file, make sure your [homes] section is uncommented and contains the following lines uncommented:
 
[homes]
comment = Home Directories
browseable = no
writeable = yes
valid users = %S
 
Then do a restart (sudo /etc/init.d/samba restart).

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
There is a graphical frontend for samba that makes configuration a lot easier (IMO).
Also, for some reason 9.10 didn't like my MSHOME workgroup, so I created one called NEW and just migrated all the machines to it.

---

