---
title: "Need help with &quot;disabled&quot; user account Ubuntu 10.04"
date: 2010-12-31
forum: General Help
---

### Post by ulriksvensson on 2010-12-31
Hi all,

I have a rather urgent problem. When I log on after boot the screen goes black for a few seconds and then it prompts me for the password again. Can't log on. My Ubuntu has worked perfectly until yesterday, and here's a brief outline of what I did that might have caused the problem:

I needed to install the Intel Fortran-90 compiler and the installation script requiers a root-user. As there is no such in Ubuntu I did

sudo passwd root

and gave a new password. After having finished the installation I rebooted and couldn't log on. I tried to log on as root and this worked. I tried to change the properties of my normal user, but nothing helped. So I thought that it is the root-user that's messing things up so I did this to remove it:

su ulrik
sudo passwd -l root

and rebooted. This is where I am now, unable to log in at all. It's strange that I could (in a terminal) switch user to my normal user (ulrik) but not log on with it...

All I can do now is to boot from the LiveCD and change config-files. I have no idea which files to look in though. Can anyone please help me, I don't want to re-install.

System: 
Ubuntu 10.04 x86_64

I'll be happy to post contents of files etc, but I don't know whats important right now...

---

### Post by ulriksvensson on 2010-12-31
Update: If I log into recovery-mode I get to the grub-menu. There I can choose "Resume Normal Boot" and then I get prompted for log in and password. This works and I can even run startx. But still I can't log in via the log-in screen. Strange?

---

### Post by imcecil on 2010-12-31
could you enter recovery mode get root access the tail /var/log/auth.log and /var/log/syslog while trying to login.
should give some insight into the problem hopefully 

something like

tail -f /var/log/{syslog,auth.log} &
startx

---

### Post by imcecil on 2010-12-31
could you enter recovery mode get root access the tail /var/log/auth.log and /var/log/syslog while trying to login.
should give some insight into the problem hopefully 

something like

tail -f /var/log/{syslog,auth.log} &
startx

---

### Post by imcecil on 2010-12-31
could you enter recovery mode get root access the tail /var/log/auth.log and /var/log/syslog while trying to login.
should give some insight into the problem hopefully 

something like

tail -f /var/log/{syslog,auth.log} &
startx

---

### Post by imcecil on 2010-12-31
could you enter recovery mode get root access the tail /var/log/auth.log and /var/log/syslog while trying to login.

should give some insight into the problem hopefully 



something like



tail -f /var/log/{syslog,auth.log} &

startx

---

### Post by imcecil on 2010-12-31
could you enter recovery mode get root access the tail /var/log/auth.log and /var/log/syslog while trying to login.

should give some insight into the problem hopefully 



something like



tail -f /var/log/{syslog,auth.log} &

startx

---

### Post by ulriksvensson on 2010-12-31
Deleted

---

### Post by imcecil on 2010-12-31
Thats not really got any useful info yet can you tail the auth log in one console and try loging in through another switch consoles with crtl+alt+ some f key (f1,f2,f3...)

also remove and info from the output that you would consider personal.

---

### Post by ulriksvensson on 2010-12-31
Forgive my ignorance. I don't really understand, to be able to do this I have to be logged in already? If I su ulrik I get this which really says nothing:

```
Dec 31 17:16:18 ulrik-laptop su[2583]: Successful su for ulrik by ulrik
Dec 31 17:16:18 ulrik-laptop su[2583]: + /dev/pts/2 ulrik:ulrik
Dec 31 17:16:18 ulrik-laptop su[2583]: pam_unix(su:session): session opened for user ulrik by ulrik(uid=1000)

```

---

### Post by imcecil on 2010-12-31
yes you can login to one console and then look at the auth.log output which should display the messages from pam which authorizes the login

then switch to a different console using ctrl+alt+f2 and try to login. pam should post some output to auth.log then switch back to the original console probably ctrl+alt+f1 and see what happened

---

### Post by ulriksvensson on 2010-12-31
The problem is that there's no root-user. The only way to swich to root access is via sudo su. This is default in ubuntu. I can only log in as "ulrik".

---

### Post by imcecil on 2010-12-31
sorry missed that bit, seems you might have locked the root account from logging in
passwd -l will insert ! at the beginning of the users password in /etc/shadow so no password input will match disabling su - 
try sudo passwd -u root

if you still have issues with su - then sudo -i has a similar effect

---

### Post by ulriksvensson on 2010-12-31
Ok, I reset the root-password with help of your reply. The log shows this:

```
Dec 31 17:37:23 ulrik-laptop su[1613]: Successful su for ulrik by root
Dec 31 17:37:23 ulrik-laptop su[1613]: + /dev/pts/0 root:ulrik
Dec 31 17:37:23 ulrik-laptop su[1613]: pam_unix(su:session): session opened for user ulrik by root(uid=0)

```

---

### Post by imcecil on 2010-12-31
just to check where things are now
if you boot up and try to login to the graphical console if fails?
root has a password set and su - works?
are you still running in recovery mode?

---

### Post by ulriksvensson on 2010-12-31
1. Yes with "ulrik" it fails. With root it works.
2. Yes
3. Yes

---

### Post by imcecil on 2010-12-31
boot into the normal mode.
try see if the login as ulrik works through the graphical
if not switch to a terminal (crtl+alt+f..) and try as ulrik again.
if this fails then login as root (in the console it's generally not advised to run graphical apps as root) and try to create new user with the adduser command then login to both the console and graphical with this user.

the screen going black on the login suggest that the login succeeds but then the x server closes if it works with other users then it's probably something in your profile you might need to go back to the logs to find what or as a last resort backup your profile and start with a fresh one.

also you switch back to the graphical terminal with ctrl+alt+f and I think it's on 8 or 9 but can't remember.

---

### Post by ulriksvensson on 2010-12-31
I booted into normal mode. Can't log in via graphical. I hit ctrl-alt-f.. and logged in as ulrik. It worked but when I ran startx I got the following:

Invalid MIT-MAGIC-COOKIE-1 keyring giving up

Tried to google this but couldn't find anything of use. Ideas?

---

### Post by imcecil on 2010-12-31
not come across the mit magic cookie before but apparently it's to do with access control to the xserver.
could you try starting the server with restart gdm or start gdm and then try logging in if it still fails then have a look in auth.log syslog and possibly even xorg.log if you everything looks normal.

---

### Post by ulriksvensson on 2010-12-31
I can log in as ulrik (already logged in) by starting gdm. Checked the xorg log-files but the only wrnings there seems to be common bugs. Might have to reinstall after all...

---

### Post by imcecil on 2010-12-31
was that by running the 'sudo start gdm' as a command, I think thats how the system starts the xserver on boot if you can login through that then everything should be working as it's a service you should be able to log out of the terminals and still have the running graphial console.
If your still trying to run startx directly as a user and this is giving you a login screen then that will probably be whats causing the magical cookie issue.

---

### Post by ulriksvensson on 2010-12-31
Yes, only it's just sudo gdm.

Another thing, after trying to startx (normal boot) I looked into /var/log/Xorg.0.log and it says the xserver is already running. I'm adviced to remove /etc/.X0-lock and try again. Still no luck.

---

### Post by ulriksvensson on 2011-01-01
An update:

I had a look in the script /etc/gdm/Xsession and realized that it is reading the file ~/.profile. So I had a look in this file and found out that the program I had built and installed had added a few lines that mad gdm think that an x-session is already running. I removed those lines and was able to log in. However Networkmanager and battery status is gone from panel and I can't connect to wireless.

---

