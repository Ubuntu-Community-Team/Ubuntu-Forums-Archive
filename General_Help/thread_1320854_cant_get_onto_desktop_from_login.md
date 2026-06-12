---
title: "cant get onto desktop from login"
date: 2009-11-09
forum: General Help
---

### Post by BeingLostMayVary on 2009-11-09
I was messing with new karmic yesterday and decided to change my log in to something that had a / before the letters like //me. I tried to log in and it gives me this error:


Cannot enter home directory using /.

(then afterwards it gives me this)

xsession: warming: unable to symlink "xmp/xession-//me" to "tmp/fileN5u53"; look for session log/errors in "/tmp/xsession-//me".


Thats the end I hit okay on it and it just stays at the new karmic background with nothing else.

Is there anyway to change the log in name through recovery?

---

### Post by BeingLostMayVary on 2009-11-09
Anyone??

---

### Post by michy99 on 2009-11-09
You can change the login name with```
usermod -l new_login_name
```where 'new_login_name' is the name you want to use. You will have to change the name of your home directory in /home to match.

---

### Post by Steve Roscio on 2009-11-09
What about Ctrl+Alt+F1 (thru F6) to get a console login.  From there you get a shell prompt and can fix/change things at the command line.  You might begin with 'adduser' to add another user that you can login with.

---

### Post by Steve Roscio on 2009-11-09
Oh... ctrl+alt+F7 gets you back to a graphical screen.

---

### Post by BeingLostMayVary on 2009-11-09
Thank you for the replies I'll try that now.

---

### Post by BeingLostMayVary on 2009-11-09
Ok I was able to made a new user and log in under that now I'm trying to go to the advanced tab to fix the other account but whenever I put in my pass for the for the password prompt it does nothing.

---

### Post by jnew93 on 2009-11-09
Yeah, it's a very bad idea to put slashes into a username. When creating your home directory, your username is used, for instance /home/yourname. If you add a slash, then your home directory would be /home//yourname. Thats not a correct path, errors will be all over the place, and you wont be able to login.

But if you login as root, whether on the host computer (if you set up a root account), or off of a recovery disk (livecd is fine) you can run the command to change your username. Cheers! :p

EDIT: this thread can help [http://ubuntuforums.org/showthread.php?t=821685&page=2]("http://ubuntuforums.org/showthread.php?t=821685&page=2")

---

### Post by BeingLostMayVary on 2009-11-09
Hmm I've tried some of the stuff on there. Is there a way to check the names of my user accounts through recovery. So I make sure that I haven't accidently changed it with a command. I tried the sudo -i on this new user I made but it said something about not having sudo power. Is there a way to change the main holder of sudo power to another UID through the root?

---

### Post by michy99 on 2009-11-09
Post the output of these commands.```
ls /home
cat /etc/passwd
cat /etc/group
```

---

### Post by BeingLostMayVary on 2009-11-09
```
ls /home : guest linuxpm phil

root:x:0:0:root:/root:/bin/bash
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
dhcp:x:101:102::/nonexistent:/bin/false                                
syslog:x:102:103::/home/syslog:/bin/false                              
klog:x:103:104::/home/klog:/bin/false                                  
hplip:x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false           
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
messagebus:x:106:115::/var/run/dbus:/bin/false                                  
avahi:x:107:116:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false           
polkituser:x:108:118:PolicyKit,,,:/var/run/PolicyKit:/bin/false                 
haldaemon:x:109:119:Hardware abstraction layer,,,:/var/run/hald:/bin/false      
unkown:x:1001:1001:no one:/home/guest:/bin/bash                                 
lastfm:x:110:121::/home/lastfm:/bin/false                                       
lastfmproxy:x:111:122::/var/lib/lastfmproxy:/bin/false                          
landscape:x:112:125:Landscape Client Daemon,,,:/var/lib/landscape:/bin/false    
dictd:x:113:123::/var/lib/dictd:/bin/false                                      
saned:x:114:124::/home/saned:/bin/false                                         
kernoops:x:115:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false                
pulse:x:116:126:PulseAudio daemon,,,:/var/run/pulse:/bin/false                  
wnn:x:117:65534:FreeWnn jserver,,,:/var/lib/wnn/ja_JP:/bin/false                
phil:x:1002:1003:,,,:/home/phil:/bin/bash                                       
d:x:1000:1002::home/theworld:/bin/bash                                          
phil@world:~$ cat /etc/group
root:x:0:                   
daemon:x:1:                 
bin:x:2:                    
sys:x:3:                    
adm:x:4:d                   
tty:x:5:                    
disk:x:6:                   
lp:x:7:                     
mail:x:8:                   
news:x:9:                   
uucp:x:10:                  
man:x:12:                   
proxy:x:13:                 
kmem:x:15:                  
dialout:x:20:unkown,d       
fax:x:21:                   
voice:x:22:                 
cdrom:x:24:unkown,d         
floppy:x:25:unkown,d        
tape:x:26:                  
sudo:x:27:                  
audio:x:29:unkown,pulse,d   
dip:x:30:d                  
www-data:x:33:              
backup:x:34:                
operator:x:37:              
list:x:38:                  
irc:x:39:                   
src:x:40:                   
gnats:x:41:                 
shadow:x:42:                
utmp:x:43:                  
video:x:44:unkown,d         
sasl:x:45:                  
plugdev:x:46:unkown,d       
staff:x:50:                 
games:x:60:                 
users:x:100:                
nogroup:x:65534:            
libuuid:x:101:              
dhcp:x:102:                 
syslog:x:103:
klog:x:104:
scanner:x:105:hplip
nvram:x:106:
fuse:x:107:d
ssl-cert:x:108:
lpadmin:x:109:unkown,d
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
admin:x:114:d
messagebus:x:115:
avahi:x:116:
netdev:x:117:
polkituser:x:118:
haldaemon:x:119:
linuxpm:x:1000:
guest::1001:
winbindd_priv:x:120:
lastfm:x:121:
lastfmproxy:x:122:
dictd:x:123:
saned:x:124:
landscape:x:125:
pulse:x:126:
pulse-access:x:127:
theworld::1002:
phil:x:1003:

```

---

### Post by michy99 on 2009-11-09
This looks really messed up. For one thing, there is no admin group listed in the group file. That means no one can use sudo. I hate to say it, but it might be time to think about backing up all your data and doing a reinstall.

---

### Post by BeingLostMayVary on 2009-11-09
Well I'm on phil atm. I'm pretty sure my admin file is now linuxpm. I'm not sure on that. If it isn't, how would I go about reinstalling? Or scrapping this and reinstalling from an image of 9.10 on a dvd? Are there options for it(to just wipe that is)?

---

