---
title: "sudo command not working (Jaunty)"
date: 2009-07-21
forum: General Help
---

### Post by Silvo on 2009-07-21
Hey,

As the title says, my sudo command is not working. 

Any time I try to use it, it will prompt for my password (as it should). If I enter in the wrong password, it says "Sorry, try again", but if I enter the correct password, it fails silently. Nothing happens. I first noticed when the update manager didn't update the programs it said it would, so I thought something was wrong with that, but no, it is sudo that isn't working.

I think this happened soon after I "fixed" my keyring thing -- I got sick and tired of having to enter my password to connect to the wireless network, so i followed some advice from somewhere so that I woulnd't have to do that any more, and I suppose that this might have arisen around about the same time. It's hard to say for sure -- I think I have used sudo after that point, but I really couldn't say.

I have tried following the advice from here: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

I had to use the recovery boot option, and I saw that my /etc/sudoers file was slightly different from the example shown (different "Defaults"), so I replaced it with that one on the site, but this has not had any noticeable effect whatsoever.

And that is basically every scrap of information I can give you. So, any ideas?

---

### Post by earthpigg on 2009-07-21
run this command, and compare to my (functioning) output:

```
cat /etc/group | more
```

my username is 'ep', which i underlined to make things easier. my output:
```

ep@ep-9:/etc$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:_***ep***_
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:_***ep***_
fax:x:21:
voice:x:22:
cdrom:x:24:_***ep***_
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:_***ep***_
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
fuse:x:104:
ssl-cert:x:105:
lpadmin:x:106:***_ep_***
crontab:x:107:
mlocate:x:108:
ssh:x:109:
avahi-autoipd:x:110:
gdm:x:111:
netdev:x:112:
saned:x:113:
pulse:x:114:
pulse-access:x:115:
pulse-rt:x:116:
messagebus:x:117:
polkituser:x:118:
avahi:x:119:
haldaemon:x:120:
admin:x:121:ep
ep:x:1000:
sambashare:x:122:_***ep***_
winbindd_priv:x:123:
vboxusers:x:124:ep,root
test:x:1001:
guest:x:125:
ntp:x:126:

```

id pay special attention to that 'adm' group. my guess is that is 'admin'. a lot of those groups, i have no idea what they do. any differences between mine and yours that strike you as odd? i have done no custom configuring of that file.


if you need to modify this file (or any config file owned by root), and sudo does not work, you will need to do so from a live cd.

---

### Post by Silvo on 2009-07-21
Thank you for the quick reply!

Well, my file looks exactly the same as your. In fact, I went through it line by line, and they are all the same until the very end:

Mine:
winbindd_priv:x:123:
ntop:x:124:
vboxusers:x:125:silvo
uml-net:x:126:

Yours:
winbindd_priv:x:123:
vboxusers:x:124:ep,root
test:x:1001:
guest:x:125:
ntp:x:126:

I'm not even going to pretend to understand what they all mean, but maybe this is the problem? Seems unlikely though, because all the lines specifying a username are identical.

---

### Post by earthpigg on 2009-07-21
'test' and 'guest' are users i created just to play around. any time you make a new user, it makes a new group. i should have taken them off my output just to save you the hassle of noticing, and me the hassle of explaining.

the difference in vboxusers is insignificant.

ntp is created if you play around with system -> administration -> time and date and set it to auto-sync your system time with time servers on the internet. insignificant. 


well, that was my only hypothesis. best of luck, chief, and sorry i couldn't be of more help.

---

### Post by Silvo on 2009-07-21
OK, thanks for the explanation, and for taking the time to help.

So, anyone got any other ideas? Assuming I can't get this to work, will I have to make a new user, or will a complete reinstall be needed? Or can I enable the root account somehow, so that I use "su" like in other distros, and forgo the need for "sudo" completely? Obviously not ideal, but it might be a last resort.

---

### Post by prshah on 2009-07-21
> **Silvo said:**
> but if I enter the correct password, it fails silently. Nothing happens.

If you get an error "Cannot resolve hostname" (or words to that effect) **when using sudo in a terminal** (Applications, Accessories, Terminal) see below for a solution.

you have to edit /etc/hosts and make sure that 127.0.0.1 is linked to your hostname. But to edit the /etc/hosts file, you need to use sudo; you can get around this catch 22 situation by either rebooting to recovery mode, 

== OR == 

Open a terminal (Applications-Accessories-Terminal) then give the command
```

hostname
```
Note the name shown and then give the command
```

gksudo
``` Note that though gksudo when combined with a command does not work, gksudo by itself should; or alternately, try gksu.

Give your password, then a window will open up, in the command box, type
```
gedit /etc/hosts
```

and choose "user" as "root", then OK/Enter. A new window will open up, look for the line beginning with
```
127.0.0.1
```

and change the word following that number to the same as in the hostname command above Note that case (UPPER/lower/Mixed) is important. Then save and quit.

Now your sudo should be working fine. (No need to reboot)

---

### Post by Silvo on 2009-07-21
Thank you for your reply. I am, however, not getting "Cannot resolve hostname" or anything similar. I am not getting any error message at all, in fact.

Out of curiosity I tried your suggestions anyway. I tried both gksudo and gksu, but neither worked. It would open a dialogue box, where I could type in a command and run it as root. I tried putting the command "gedit /etc/hosts" in that box, and I also tried just leaving it blank. It would then prompt for my password, which I entered, and then close, returning focus to the command line. So, yeah, same issue as before. 

Any other ideas?

---

### Post by prshah on 2009-07-21
> **Silvo said:**
> 
Any other ideas?

Try running a command with sudo from the terminal (Applications-Accessories-Terminal) so that we can see if there are any error messages.
Eg```
sudo pico /etc/hosts
``` Post back any error messages.

---

### Post by Silvo on 2009-07-21
> **prshah said:**
> Try running a command with sudo from the terminal (Applications-Accessories-Terminal) so that we can see if there are any error messages.

I have, there aren't any. Attached is a screenshot, if you don't believe me. Pico did not start in the above example.

Any command issued with "sudo" will prompt for a password, and when I enter it correctly, it just jumps back ready for the next command, it never *does* anything. Even something like "ls", doesn't do anything.

---

### Post by bacil on 2009-07-21
can you login as root using su - ?

if so just add yourself in to group admin thats automatiacly allowing you to use sudo

if not wewillhave to take deeper look :-)

---

### Post by Silvo on 2009-07-21
> **bacil said:**
> can you login as root using su - ?

Nope, it gives me this error: 

```
su: Authentication failure
```

> if so just add yourself in to group admin thats automatiacly allowing you to use sudo

Is that the same as going to System -> Administration -> Users and Groups, clicking "Properties", then going to the "User Privileges" tab and ticking "Administer the system"? Because, that box is ticked for me. It's also greyed out, and I can't change it.

---

### Post by bacil on 2009-07-21
not sure about gui :-) 

can you without sudo type adduser test to see if we can modify system ?  and then in gui add this user to admin group ?

another question: from what i see on your screenshot it looks like sudo is working, but no command executed. eg. you gain privileges but no command is executed.

here is my output when i try to sudo with test user who doesnt have sudoers rights.

```

test@one:~$ sudo ls
[sudo] password for test:
test is not in the sudoers file.  This incident will be reported.

```

thats different

---

### Post by Silvo on 2009-07-21
> **bacil said:**
> can you without sudo type adduser test to see if we can modify system ?

Like this?
```
silvo@pegasus:~$ adduser test
adduser: Only root may add a user or group to the system.
```

That doesn't seem to work...

> 
another question: from what i see on your screenshot it looks like sudo is working, but no command executed. eg. you gain privileges but no command is executed.

That might be a possibility... Would there be a way to test this?

---

### Post by bacil on 2009-07-21
can you try run 

```
sudo sleep 1000
```

and then from another terminal

```
 ps -ef | grep sleep 
```

and get me the result of grep ?

---

### Post by prshah on 2009-07-21
Can you post the contents of your /etc/sudoers file? You need to be root to access the file, so maybe you will need to restart in "recovery mode" and copy the file elsewhere and make a permissions change to make it readable. Eg```

cp /etc/sudoers /root/
chmod a+r /root/sudoers
``` then reboot and post the /root/sudoers file.

---

### Post by bacil on 2009-07-21
> **prshah said:**
> Can you post the contents of your /etc/sudoers file? You need to be root to access the file, so maybe you will need to restart in "recovery mode" and copy the file elsewhere and make a permissions change to make it readable. Eg```

cp /etc/sudoers /root/
chmod a+r /root/sudoers
``` then reboot and post the /root/sudoers file.

I dont think this will help us. see screen shot sudo works and user is in sudoers or in group that is it seems like execution is not performed.

---

### Post by Silvo on 2009-07-21
> **bacil said:**
> can you try run 

```
sudo sleep 1000
```

and then from another terminal

```
 ps -ef | grep sleep 
```

and get me the result of grep ?

Here it is:

```
silvo     4734  4717  0 19:55 pts/1    00:00:00 grep sleep
```

Also, I ran the "ps..." command after I had run "sudo sleep 1000" but before I entered my password, and it had another entry with "root". I don't know if that helps. But this one above was run after the password was entered.

---

### Post by Silvo on 2009-07-21
> **bacil said:**
> I dont think this will help us. see screen shot sudo works and user is in sudoers or in group that is it seems like execution is not performed.

I can show you my sudoers file, it's the one from here: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

I replaced my previous one with that one earlier, but there was no change. The only differece of the original comapred to that one was where this one had 
```
Defaults !lecture,tty_tickets,!fqdn 
```

the old one had something like

```
 Defaults env_something 
```

I dont quite remember what it was, but I think it had env in it somewhere. I have the file backed up, but i need root permissions to get at it, so I'll have to reboot into recovery mode. Do you need me to get this old file? Bare in mind that the new file should be identical to the one on that site, unless in the mean time something has screwed with it again.

---

### Post by bacil on 2009-07-21
You saying that sudo sleep 1000 returned immediately ?

it shouldnt ... it should have give you plenty of time to start another terminal before it returned

can you run it again and get return code ? so it will go like this
```

[+18% 00:01:24]-bacil@one:/etc$ sudo sleep 1
[+18% 00:01:24]-bacil@one:/etc$ echo $?

```
and i need output of that echo $? 

eventualy you can run it through the pipe

```
sudo sleep 1000 | echo $?
```

---

### Post by Silvo on 2009-07-21
Oh, you're saying that sleep 1000 should give me a long pause? Hmm, it didn't.

I just ran "sleep 1000" instead of "sudo sleep 1000" and I understand what you mean now... I thought 1000 was in milliseconds! :D 

```
silvo@pegasus:~$ sudo sleep 1
[sudo] password for silvo: 
silvo@pegasus:~$ echo $?
1
silvo@pegasus:~$ sudo sleep 1000 | echo $?
0
[sudo] password for silvo: 
silvo@pegasus:~$ 
```

Nowhere in all of that did it sleep for any noticeable amount of time.

---

### Post by bacil on 2009-07-21
Ok it returns 1, so there is something wrong somewhere.

can you check if you got all these files ?

```

sudo: /usr/bin/sudo                                                                                   
sudo: /usr/bin/sudoedit                                                                               
sudo: /usr/lib/sudo/sudo_noexec.so                                                                    
sudo: /usr/sbin/visudo                                                                                
sudo: /usr/share/doc/sudo/BUGS                                                                        
sudo: /usr/share/doc/sudo/HISTORY                                                                     
sudo: /usr/share/doc/sudo/NEWS.Debian.gz                                                              
sudo: /usr/share/doc/sudo/OPTIONS                                                                     
sudo: /usr/share/doc/sudo/PORTING.gz                                                                  
sudo: /usr/share/doc/sudo/README                                                                      
sudo: /usr/share/doc/sudo/README.Debian                                                               
sudo: /usr/share/doc/sudo/TROUBLESHOOTING.gz                                                          
sudo: /usr/share/doc/sudo/UPGRADE.gz                                                                  
sudo: /usr/share/doc/sudo/changelog.Debian.gz                                                         
sudo: /usr/share/doc/sudo/changelog.gz                                                                
sudo: /usr/share/doc/sudo/copyright                                                                   
sudo: /usr/share/doc/sudo/examples/sudoers                                                            
sudo: /usr/share/lintian/overrides/sudo                                                               
sudo: /usr/share/man/man5/sudoers.5.gz                                                                
sudo: /usr/share/man/man8/sudo.8.gz                                                                   
sudo: /usr/share/man/man8/sudo_root.8.gz                                                              
sudo: /usr/share/man/man8/sudoedit.8.gz                                                               
sudo: /usr/share/man/man8/visudo.8.gz      

```

and also you said you can replace sudoers ? how whithout admin privileges ?

---

### Post by sisco311 on 2009-07-21
How did you *"fixed" the keyring thing*?

What's the output of:
```
cat /etc/pam.d/gdm
cat /etc/pam.d/sudo
```

---

### Post by Silvo on 2009-07-21
> **bacil said:**
> Ok it returns 1, so there is something wrong somewhere.

can you check if you got all these files ?

```

sudo: /usr/bin/sudo                                                                                   
sudo: /usr/bin/sudoedit                                                                               
sudo: /usr/lib/sudo/sudo_noexec.so                                                                    
sudo: /usr/sbin/visudo                                                                                
sudo: /usr/share/doc/sudo/BUGS                                                                        
sudo: /usr/share/doc/sudo/HISTORY                                                                     
sudo: /usr/share/doc/sudo/NEWS.Debian.gz                                                              
sudo: /usr/share/doc/sudo/OPTIONS                                                                     
sudo: /usr/share/doc/sudo/PORTING.gz                                                                  
sudo: /usr/share/doc/sudo/README                                                                      
sudo: /usr/share/doc/sudo/README.Debian                                                               
sudo: /usr/share/doc/sudo/TROUBLESHOOTING.gz                                                          
sudo: /usr/share/doc/sudo/UPGRADE.gz                                                                  
sudo: /usr/share/doc/sudo/changelog.Debian.gz                                                         
sudo: /usr/share/doc/sudo/changelog.gz                                                                
sudo: /usr/share/doc/sudo/copyright                                                                   
sudo: /usr/share/doc/sudo/examples/sudoers                                                            
sudo: /usr/share/lintian/overrides/sudo                                                               
sudo: /usr/share/man/man5/sudoers.5.gz                                                                
sudo: /usr/share/man/man8/sudo.8.gz                                                                   
sudo: /usr/share/man/man8/sudo_root.8.gz                                                              
sudo: /usr/share/man/man8/sudoedit.8.gz                                                               
sudo: /usr/share/man/man8/visudo.8.gz      

```

and also you said you can replace sudoers ? how whithout admin privileges ?

Yep, I've got all of those.

i changed the sudoers file by rebooting into recovery mode -- that gave me a root command line where I could swap the files over.

---

### Post by prshah on 2009-07-21
> **Silvo said:**
> 
```
Defaults !lecture,tty_tickets,[color=red]!fqdn[/color] 
```


OK, !fqdn is probably important. From the man:> 

Beware that turning on fqdn requires sudo to make DNS lookups which may make sudo unusable if DNS stops working (for example if the machine is not plugged into the network).  Also note that you must use the host&#8217;s official name as DNS knows it. 

The default for fqdn is "on", and by not putting the "!fqdn" (translates to "NOT fqdn") you are probably facing this issue.

Boot into recovery mode, edit your /etc/sudoers file with ```
visudo
```, add the "!fqdn" tag, save, reboot and check if sudo works.

---

### Post by Silvo on 2009-07-21
> **sisco311 said:**
> How did you *"fixed" the keyring thing*?


I dont think I'm going to be able to find the site that had the instructions again, but it involved deleting the files in the folder ~/.gnome2/keyrings

> 
What's the output of:
```
cat /etc/pam.d/gdm
cat /etc/pam.d/sudo
```

```

silvo@pegasus:~$ cat /etc/pam.d/gdm
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password


silvo@pegasus:~$ cat /etc/pam.d/sudo
#%PAM-1.0

@include common-auth
@include common-account

session required pam_permit.so
session required pam_limits.so
silvo@pegasus:~$ 

```

---

### Post by bacil on 2009-07-21
This is wierd.

it looks like your sudo is not executing any commands 

can you run ```
 cat /var/log/auth.log | grep sudo
```

---

### Post by Silvo on 2009-07-21
> **prshah said:**
> OK, !fqdn is probably important. From the man:

The default for fqdn is "on", and by not putting the "!fqdn" (translates to "NOT fqdn") you are probably facing this issue.

Boot into recovery mode, edit your /etc/sudoers file with ```
visudo
```, add the "!fqdn" tag, save, reboot and check if sudo works.

Sorry, I probably didn't explain myself very well: my *new* file has the !fqdn part in it, the *old* file didn't. Neither work. I rebooted into recovery mode anyway just to check, and yes, the !fqdn part is definitely there.

---

### Post by Silvo on 2009-07-21
> **bacil said:**
> This is wierd.

it looks like your sudo is not executing any commands 

can you run ```
 cat /var/log/auth.log | grep sudo
```

Here it is. It's quite long.

```

Jul 16 11:35:29 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jul 16 11:35:29 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jul 16 11:35:30 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Jul 16 11:41:09 pegasus sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=silvo
Jul 16 11:41:24 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 60817445 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpBS6ega
Jul 16 14:07:30 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 16 14:10:04 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/gdebi-gtk --non-interactive /home/silvo/Downloads/opera-static_9.64.2480.gcc295.qt3_i386.deb
Jul 16 14:46:37 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 16 17:56:42 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 16 17:59:05 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/gedit /etc/apt/sources.list
Jul 16 17:59:19 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Jul 16 18:00:31 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Jul 16 18:00:51 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 16 18:01:57 pegasus sudo:    silvo : TTY=pts/1 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get update
Jul 16 18:05:24 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Jul 16 18:09:10 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-key add -
Jul 16 18:09:10 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/wget -O - http://deb.opera.com/archive.key
Jul 16 18:09:23 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Jul 16 18:09:43 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get update
Jul 16 18:10:42 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Jul 16 18:14:49 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Jul 16 18:15:24 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-key add -
Jul 16 18:15:44 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get update
Jul 16 18:16:07 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 17 09:34:30 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jul 17 09:34:30 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jul 17 09:34:30 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Jul 17 09:41:34 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 58720293 -o Synaptic::closeZvt=true --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpncHQrp
Jul 17 16:19:03 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 17 16:26:21 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Jul 17 16:28:32 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7EBC211F
Jul 17 16:28:50 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Jul 17 16:28:56 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Jul 17 16:29:29 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 17 16:29:39 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get update
Jul 17 16:29:49 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 18 17:54:23 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/gedit /boot/grub/menu.lst
Jul 18 21:30:11 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 18 21:37:24 pegasus sudo:    silvo : TTY=unknown ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 18 21:45:24 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/sbin/hdparm -d /dev/sda7
Jul 18 21:45:29 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/sbin/hdparm -d /dev/sda7
Jul 18 21:54:16 pegasus sudo:    silvo : TTY=pts/1 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get install preload
Jul 18 21:54:57 pegasus sudo:    silvo : TTY=pts/1 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/gtkorphan
Jul 18 21:56:28 pegasus sudo:    silvo : TTY=pts/1 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/gtkorphan
Jul 18 21:57:43 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get --help
Jul 18 21:58:05 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get check
Jul 18 21:58:13 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get clean
Jul 18 21:58:32 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get clean
Jul 18 21:58:36 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get upgrade
Jul 18 22:01:10 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get upgrade
Jul 18 22:01:13 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get clean
Jul 18 22:01:16 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get check
Jul 18 22:01:30 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 18 22:02:21 pegasus sudo:    silvo : TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/sbin/synaptic
Jul 19 10:26:33 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jul 19 10:26:33 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jul 19 10:26:33 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Jul 20 10:37:56 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jul 20 10:37:56 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jul 20 10:37:56 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Jul 21 11:16:16 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jul 21 11:16:16 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jul 21 11:16:16 pegasus sudo:     root : TTY=unknown ; PWD=/ ; USER=silvo ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Jul 21 11:42:31 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:17:25 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:20:16 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:20:26 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:20:41 pegasus sudo: pam_unix(sudo:auth): authentication failure; logname=silvo uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=silvo
Jul 21 15:20:45 pegasus sudo:    silvo : 1 incorrect password attempt ; TTY=pts/0 ; PWD=/home/silvo ; USER=root ; COMMAND=/usr/bin/apt-get update
Jul 21 15:20:50 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:20:54 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:20:57 pegasus sudo: pam_unix(sudo:auth): authentication failure; logname=silvo uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=silvo
Jul 21 15:21:05 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:21:13 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:24:57 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:25:00 pegasus sudo: pam_unix(sudo:auth): authentication failure; logname=silvo uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=silvo
Jul 21 15:26:53 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:30:25 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:49:03 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:49:24 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 15:56:56 pegasus sudo: pam_unix(sudo:auth): authentication failure; logname=silvo uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=silvo
Jul 21 15:58:38 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 16:01:22 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 17:22:53 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 17:23:09 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 17:24:08 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 17:25:30 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 18:50:01 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 18:55:23 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 18:56:04 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 19:32:44 pegasus sudo: pam_unix(sudo:auth): authentication failure; logname=silvo uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=silvo
Jul 21 19:32:50 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 19:33:10 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 19:34:45 pegasus sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=silvo ; COMMAND=/usr/bin/pactl suspend-sink 1
Jul 21 19:34:45 pegasus sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=silvo ; COMMAND=/usr/bin/pactl suspend-source 1
Jul 21 19:36:59 pegasus sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=silvo ; COMMAND=/usr/bin/pactl suspend-source 0
Jul 21 19:36:59 pegasus sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=silvo ; COMMAND=/usr/bin/pactl suspend-sink 0
Jul 21 19:54:36 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 19:54:59 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 20:04:28 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 20:04:51 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf
Jul 21 20:53:02 pegasus sudo: pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf

```

---

### Post by Silvo on 2009-07-21
Hmm, every time I run a sudo command (I just tried "sudo gedit"), it adds that error to the log:

pam_smbpass(sudo:auth): Error loading service file /etc/samba/smb.conf

But, that's to do with samba isn't it? Samba being the network/file-sharing thing? Surely that can't be what's screwing with sudo?

---

### Post by slakkie on 2009-07-21
What output does sudo -l give you?

---

### Post by Silvo on 2009-07-21
> **slakkie said:**
> What output does sudo -l give you?

Nothing:

```
silvo@pegasus:~$ sudo -l
[sudo] password for silvo: 
silvo@pegasus:~$ 
```

---

### Post by bacil on 2009-07-21
it does not show any of sleep commands. so they were not issued. wierd since it works from scripts.

can you run ```
which sudo
```

just in case you got two different ones ?

---

### Post by Silvo on 2009-07-21
Only the one:

```
silvo@pegasus:~$ which sudo
/usr/bin/sudo
silvo@pegasus:~$ 

```

Correction from earlier: the samba error doesn't appear in the logs *every* time I run a sudo command... It only happens some of the time, which is odd.

---

### Post by bacil on 2009-07-21
ok and ```
ls -la /usr/bin/sudo
``` ?

---

### Post by Silvo on 2009-07-21
```
silvo@pegasus:~$ ls -la /usr/bin/sudo
-rwsr-xr-x 1 root root 115136 2009-02-17 14:22 /usr/bin/sudo
silvo@pegasus:~$ 
```

---

### Post by bacil on 2009-07-21
You got me there now. 

i would try from recovery console apt-get remove sudo and install sudo

---

### Post by Silvo on 2009-07-21
alright, I'll give that a go now.

Looking at my logs, it appears that the last sudo commands that I have run successfully were:

- to install the application "preload"
- to install and run "gtkorphan" (a GUI for "deborphan")

Have either of these been known to have effects like this?

---

### Post by sisco311 on 2009-07-21
i think i found the solution: [http://forum.ubuntu-it.org/index.php/ topic,296582.20.html]("http://forum.ubuntu-it.org/index.php/topic,296582.20.html") <- Italian Ubuntu forums.  

your smb.conf is missing or is messed up.

in the recovery mode:
```
cp /usr/share/samba/smb.conf /etc/samba/smb.conf
```

---

### Post by bacil on 2009-07-21
nope both are scheduled runs to clean up system, my system is running them aswel

---

### Post by Silvo on 2009-07-21
> **sisco311 said:**
> i think i found the solution: [http://forum.ubuntu-it.org/index.php/ topic,296582.20.html]("http://forum.ubuntu-it.org/index.php/topic,296582.20.html") <- Italian Ubuntu forums.  

your smb.conf is missing or is messed up.

in the recovery mode:
```
cp /usr/share/samba/smb.conf /etc/samba/smb.conf
```

That did it!!! :D

Thank you, everyone, for all your help! It turned out that the cryptic samba error in the log was the culprit after all. I wonder why that happened all ofa sudden? I probably removed samba with gtkorphan... Is that bad? Do I need samba? I originally installed it so I could have a shared folder with my virtualbox windows installation, but I couldn't work out how to use it. Is there a way I can get rid of it safely?

Thanks again for your help everyone!

---

### Post by sisco311 on 2009-07-21
Sounds like a pam BUG in Jaunty.

---

### Post by Silvo on 2009-07-21
What is pam? Wikipedia might know...

---

### Post by bacil on 2009-07-21
nice one. would not have thought that smb.conf will prevent sudo from running

---

### Post by Silvo on 2009-07-21
Yeah, that doesn't make sense to me either. Why would sudo care at all about samba? 

And I tried to learn about PAMs on Wikiepdia, but I must say that it still doesn't make very much sense... Is samba somehow involved in authenticating users for super-user privileges? That would explain why sudo would keep trying to run samba, and why it might not authenticate you if samba is screwing up... But you'd think that it would give you a more helpful error message beyond some cryptic remark hidden in a log file somewhere.

---

### Post by bacil on 2009-07-21
Yeah,

i guess there is some linking when samba needs to authenticate incoming connection. I don't have samba on this laptop, but running it on my othe one will try to remove it and see if sudo keep working.

what i would sugest to you is create password for root so you can su to it if needed 

```
 sudo passwd 
```

make it secure password and use it with su - when need tobecoma root with all privileges.

can you send me your old smb.conf ? for rference i fill run diff on it adn will see what caused this ?

---

### Post by Silvo on 2009-07-21
Thanks for that tip! I've wondered how to get a root user account before, because there are times when I'm doing a fair bit of tinkering and I've thought that it would be handy to not have to keep adding "sudo" to everything (especially when I keep forgetting about it...). I thought that Ubuntu wouldn't let you do it, but as it turns out, you can! :)

I'd love you give you old my smb.conf file, but I didn't have one! I didn't even have a /etc/samba folder. I guess that was automatically removed when I ran gtkorphan. I remember ticking the box that said somethign like "remove all configuration files" thinking "what could possibly go wrong?". Well, now I know!

---

