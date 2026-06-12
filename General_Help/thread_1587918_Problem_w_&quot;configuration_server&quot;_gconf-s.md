---
title: "Problem w &quot;configuration server&quot; gconf-sanity-check-2 exited w status 256, ?need fix?"
date: 2010-10-04
forum: General Help
---

### Post by rocksockdoc on 2010-10-04
**Any idea how to "repair" "the configuration server" ?**

I'm only a month into Ubuntu and I have this fatal inability to create a new user from the Gnome GUI. For any new user I create, I get the following fatal errors upon rebooting and trying to log in to that user.
- Purple clouds for about a minute.
-- then --
- Could not update ICEauthority file /home/user_encrypted/.ICEauthority
**[COLOR=DarkRed] - There is a problem with the configuration server. [/COLOR]**
- (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
-- then --
- Nautilus could not create the following required folders: 
- /home/user_encrypted/Desktop, /home/user_encrypted/.nautilus
- Before running Nautilus, please create these folders, or set permissions such that Nautulus can create them.
-- then --
- Purple clouds forever.

**Any idea how to FIX this problem?**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171272&d=1286189110[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171273&d=1286189110[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171274&d=1286189110[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171275&d=1286189110[/IMG]

---

### Post by rocksockdoc on 2010-10-04
I should note I already tried the following reputed fixes:

TMP fix:
$ sudo chown -rwx root:root /tmp
$ sudo chmod 1777 /tmp

REGISTRY fix:
$ sudo apt-get remove gconf2 gconf2-common
$ sudo rm -rf /etc/gconf
$ sudo apt-get install ubuntu-desktop

GDM fix:
$ sudo chmod 775 /etc/gconf*
$ sudo apt-get install --reinstall gdm

XML fix:
$ sudo chmod 755 /etc/gconf.xml.system

CHOWN fix:
$ chown -R user ~/.ICE* ~/.kde

OWNERSHIP fix:
$ su
$ chown user -R /home/user

DEBUG hint:
$ sudo /usr/lib/libgconf2-4/gconf-sanity-check-2 (simply reports nothing)

**Is there a fundamental way to test WHERE the problem lies?**

---

### Post by rocksockdoc on 2010-10-04
The strangest thing is happening in the /etc/passwd file.

I can't log in directly to root for some reason.

I can sudo just fine; I just can't "be" root. 
Here's what transpired:
```

user@donna:~$ **whoami**
user
user@donna:~$ **id**
uid=1000(user) gid=1000(user) groups=4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),119(admin),122(sambashare),1000(user)
user@donna:~$ **ecryptfs-mount-private**
Enter your login passphrase: **foobar**
Inserted auth tok with sig [2a1860e7cb545c30] into the user session keyring
**[COLOR=DarkRed]open: Read-only file system[/COLOR]**
Error locking counteruser@donna:~$ 
user@donna:~$**su **
Password: **rootfoobar**
[COLOR=DarkRed]**su: Authentication failure**[/COLOR]
user@donna:~$** rlogin root**
[COLOR=DarkRed][B]/etc/ssh/ssh_config: line 53: Bad configuration option: PermitRootLogin
/etc/ssh/ssh_config: terminating, 1 bad configuration options[/B][/COLOR]
user@donna:~$ s**udo chmod 1777 /tmp ** <--I just did this to prove I had root access
user@donna:~$

```Here is the /etc/passwd file (I highlighted root, user & the 3 newly created test users):
```
[B][COLOR=DarkRed]
root:x:0:0:root:/root:/bin/bash[/COLOR][/B]
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:107::/var/run/dbus:/bin/false
avahi-autoipd:x:103:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:105:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
speech-dispatcher:x:106:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
usbmux:x:107:46:usbmux daemon,,,:/home/usbmux:/bin/false
haldaemon:x:108:114:Hardware abstraction layer,,,:/var/run/hald:/bin/false
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:110:115:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:111:117:RealtimeKit,,,:/proc:/bin/false
saned:x:112:118::/home/saned:/bin/false
hplip:x:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:114:120:Gnome Display Manager:/var/lib/gdm:/bin/false
[COLOR=DarkRed]**user:x:1000:1000:user,,,:/home/user:/bin/bash**[/COLOR]
smmta:x:115:123:Mail Transfer Agent,,,:/var/lib/sendmail:/bin/false
smmsp:x:116:124:Mail Submission Program,,,:/var/lib/sendmail:/bin/false
debian-tor:x:117:126::/var/lib/tor:/bin/bash
guest:x:118:127:Guest,,,:/tmp/guest-home.9gMEUd:/bin/bash
privoxy:x:119:65534::/etc/privoxy:/bin/false
[COLOR=DarkRed]help:x:1001:1001:Help,,,:/home/help:/bin/bash
user_encrypted:x:1002:1002:user_encrypted,,,,:/home/user_encrypted:/bin/bash
user_500:x:1003:1003:user_500,,,,:/home/user_500:/bin/bash[/COLOR]

```BTW, as additional data, a "sudo -s" was suggested here:
- [Manual Data Recovery with Ecryptfs and Ubuntu]("http://cole.mickens.us/2010/08/09/manual-data-recovery-with-ecryptfs-and-ubuntu/"), by Cole Mickens, on 2010/08/09

And THAT "**sudo -s**" worked just fine:
```

user@donna:~$ **sudo -s**
[sudo] password for user: **foobar**
root@donna:~# **id**
uid=0(root) gid=0(root) groups=0(root)

```**How do I fix the error:**
```

user@donna:~$ **rlogin root**
[COLOR=DarkRed][B]/etc/ssh/ssh_config: line 53: Bad configuration option: PermitRootLogin
/etc/ssh/ssh_config: terminating, 1 bad configuration options[/B][/COLOR]

```

Is it as simple as changing that last line of the 53-line ssh_config file from "no" to "yes"?
```

# This is the ssh client system-wide configuration file.  See # ssh_config(5) for more information.  This file provides defaults for # users, and the values can be changed in per-user configuration files # or on the command line.  # Configuration data is parsed as follows: #  1. command line options #  2. user-specific file #  3. system-wide file # Any configuration value is only changed the first time it is set. # Thus, host-specific definitions should be at the beginning of the # configuration file, and defaults at the end.  # Site-wide defaults for some commonly used options.  For a comprehensive # list of available options, their meanings and defaults, please see the # ssh_config(5) man page.  Host * #   ForwardAgent no #   ForwardX11 no #   ForwardX11Trusted yes #   RhostsRSAAuthentication no #   RSAAuthentication yes #   PasswordAuthentication yes #   HostbasedAuthentication no #   GSSAPIAuthentication no #   GSSAPIDelegateCredentials no #   GSSAPIKeyExchange no #   GSSAPITrustDNS no #   BatchMode no #   CheckHostIP yes #   AddressFamily any #   ConnectTimeout 0 #   StrictHostKeyChecking ask #   IdentityFile ~/.ssh/identity #   IdentityFile ~/.ssh/id_rsa #   IdentityFile ~/.ssh/id_dsa #   Port 22 #   Protocol 2,1 #   Cipher 3des #   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc #   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160 #   EscapeChar ~ #   Tunnel no #   TunnelDevice any:any #   PermitLocalCommand no #   VisualHostKey no     SendEnv LANG LC_*     HashKnownHosts yes     GSSAPIAuthentication yes     GSSAPIDelegateCredentials no **[COLOR=DarkRed]    PermitRootLogin no[/COLOR]** 
```

Should I change line 53 to:
**[COLOR=DarkRed]    PermitRootLogin yes[/COLOR]**

---

### Post by abnaxus on 2010-10-08
hey everyone :( i have a small problem... :( maybe someone can help? :-s
it look like i can't login in my ubuntu...aparently Nautilus has gone bad! :((
my system is a dual boot 32 bit ubuntu/64 bit win7... :( 

i'm getting there errors: 
1. [could not update ICEauthority file /home/prometeus/.ICEauthority]
2. [There is a problem with thte configuration servers (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with estatus 256)]
3. [Nautilus could not create the following required folder: /home/prometeus/Desktop and /home/prometeus/.nautilus Before running Nautilus, please create these folders or set permisions such that Nautilus can create them.]

i've tried to create them via recovery console but no luck! :(

reinstalling isnt's a option because of the documents i've got left in the doc folder...also the home dir supposed to be encrypted... :((

i wonder if this solution worked out for you... :(

> **rocksockdoc said:**
> I should note I already tried the following reputed fixes:

TMP fix:
$ sudo chown -rwx root:root /tmp
$ sudo chmod 1777 /tmp

REGISTRY fix:
$ sudo apt-get remove gconf2 gconf2-common
$ sudo rm -rf /etc/gconf
$ sudo apt-get install ubuntu-desktop

GDM fix:
$ sudo chmod 775 /etc/gconf*
$ sudo apt-get install --reinstall gdm

XML fix:
$ sudo chmod 755 /etc/gconf.xml.system

CHOWN fix:
$ chown -R user ~/.ICE* ~/.kde

OWNERSHIP fix:
$ su
$ chown user -R /home/user

DEBUG hint:
$ sudo /usr/lib/libgconf2-4/gconf-sanity-check-2 (simply reports nothing)

**Is there a fundamental way to test WHERE the problem lies?**

---

### Post by DarkRedman on 2010-10-08
I've exactly the same bug, I mean this error "(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

How could I fix it ?

---

### Post by Ryland on 2010-11-03
I have this problem but I can't get to any GUI screens. I can log in as root via the Recovery option from the grub screen. Then when I am in the console screen I can't use the mount command and can't log into my encrypted user account.

Could this problem be related to having an encrypted home directory for the only user and issues relating to upgrades that require a reboot and then can't write to the encrypted user files?

---

### Post by abnaxus on 2010-11-03
i've gave up to try to find a solution at that point. i managed to get my data out of my hdd and reinstalled ubuntu without any encryption of my home dir. that's sucks though cause i'm moving alot and i need encryption... :(

---

### Post by wavesailor on 2010-11-29
I found this which solved the problem for me:
[http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/)

It turns out there was not enough space on the file system - bad error messages :-(

---

### Post by abnaxus on 2010-11-29
that cant be right...

i had space at that time on my hdd (about 50 or so Gb)...

i dont think that was the problem...
somehow the encryption engine had gone haywire...that was my problem at that time...

---

### Post by Qwertinsky on 2011-01-06
I just had to deal with this exact problem. 

In my case it was a corrupt file system. 

Booting from a Ubuntu install disk(flashdrive) and running fsck with the -fy option on my hard drive (/) fixed several things and cured the error message.

In my case fsck needed the -f to force it to run because the "clean flag" was set meaning fsck would not do anything on it's own.

---

### Post by bricebu on 2012-06-29
This worked for me:[INDENT][FONT=Courier New][COLOR=Black]sudo apt-get --reinstall install ubuntu-desktop[/COLOR][/FONT]
[/INDENT]To get to a command line I had to interrupt the boot (hold down left-shift) and choose Recovery Mode, which gave me a root shell. (The "sudo" is optional (and harmless) in that case, of course, but would be necessary if logged in as a regular user.)

---

### Post by oldos2er on 2012-06-29
Old thread closed.

---

