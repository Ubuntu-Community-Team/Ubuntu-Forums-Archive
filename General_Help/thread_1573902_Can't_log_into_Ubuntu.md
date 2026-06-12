---
title: "Can't log into Ubuntu"
date: 2010-09-13
forum: General Help
---

### Post by elperrillo on 2010-09-13
I am desperate I don't know what I am going to do anymore.

Somehow Ubuntu does not not let me log in, no matter if I am in normal mode or in terminal the only way I can log in is using recovery mode. I have done the XFIX I have checked the fsck, I ran dpkg and nothing seems to work, I tried changing the password for "administrator" and "root" while I was under "recovery mode" and it does not let me either. it gives me a "Segmentation fault" does not matter which user name I pick.

Can somebody help me? I am extremely desperate, this is one of my most important servers at work!! :frown:

---

### Post by elperrillo on 2010-09-13
Can anybody help me for the love of GOD!!!!

---

### Post by elperrillo on 2010-09-14
While it is true that these forums are free and that I should not expect a quick answer I must say that the quality has gone down considerably, When I started playing around with Ubuntu I use to get answers within minutes, now I have to beg for an answer and I do not even get one. Whats happening to Ubuntu, is it on the decline?

---

### Post by sikander3786 on 2010-09-14
I am really sorry that nobody answered your question. Might be someone capable didn't view your thread yet. There are lots of threads and only a handful of geeks around so you've to wait for some specific problems.

Which version of Ubuntu are you running? Also has it got a GUI or it is a server edition?

What happens when you login in the normal mode? Any error messages? Is it the blank screen causing problems?

---

### Post by elperrillo on 2010-09-14
Hi, thanks for answering me

I am running verion 8.04 still. I have been reluctant to upgrade it because I am running a proxy server which is extremely mission critical, and we work 24/hr a day. Right not the server is working but I cannot log in, to make any changes. 

When I try to log in, I type my username and password and hit enter, everything goes black for a couple of seconds and I am back to the login screen. If I do it using CTRL-ALT-F1 same thing happens, input usernamme and password and I am back to the prompt. (If I enter it incorrectly it will tell me that is incorrect, so it is acknowledging it as correct credentials)

I am able to log in using "recovery mode", however it does not let me change the password for any of the users, and if I create a new user it lets me create it but it does not ask me for a password, and If I try to change the password on it, it will just tell me "password changed" without even asking me for one.

---

### Post by Vigh on 2010-09-14
I had the exact same problem, did you recently install/uninstall/reinstall some alsa packages or change any configuration files? Best bet is to boot with ubuntu live-cd and back up all your data and then do a fresh install of ubuntu, then once you have everything setup again create a ghost-image of your drive with Clonezilla so if anything goes wrong again its a one-step system restore.

Tips- use only even numbered packages which are stable packages
-only follow setup-guides/config-guides for sound, video etc. from official ubuntu website or ubuntu forums

you could try dropping to root console with networking and running a sudo reinstall reconfigure gdm and ubuntu-desktop, but I am not exactly sure of the command on how to do this

---

### Post by elperrillo on 2010-09-14
Goog idea about creating a ghost image with clonezilla, however like I said this server is mission critical, I cannot take it down for too long. I do not even know how to backup SQUIDs configuration to establish a temporary server. What I did was remove FreeNX and Install Nomachine's NX. and I did go in there through the recovery console and removes all the NX packages, but that did not help.

---

### Post by Vigh on 2010-09-14
i think the command in root console with networking, once you go to recovery mode is

sudo apt-get install --reinstall gdm && ubuntu-desktop && reconfigure dpkg-gdm && dpkg-ubuntu-desktop

but I would check this with someone of a higher geekness than I

this may fix your login problems

---

### Post by elperrillo on 2010-09-14
Thanks for your help. 

I will try cloning the hard drive first in case anything goes wrong, then I will execute that command.

If anybody out there has any corrections to that command please let me know, thanks.

---

### Post by elperrillo on 2010-09-14
Vigh:

Finally after a lot of work I was able to close the server into a desktop computer, now I have a computer to play with in case something goes wrong. Unfortunatelly your command did not work, it did the first part but it stopped with an error stating:

"ubuntu-desktop" command not recognized.

Any Idea what it wrong with that command anybody? the command is:

sudo apt-get install --reinstall gdm && ubuntu-desktop && reconfigure dpkg-gdm && dpkg-ubuntu-desktop

---

### Post by Lateralis on 2010-09-14
The && tells the shell it is a new command.  It is therefore trying to run the command "ubuntu-desktop", which doesn't exist.  I think what Vigh was getting at was to reinstall and reconfigure the gdm and unbuntu-desktop packages. 

```

sudo aptitude reinstall gdm ubuntu-destop

```

will (hopefully) reinstall the GDM and ubuntu-desktop.  I'm not sure about the reconfigure, but from memory (and a quick man page scan)

```

dpkg-reconfigure gdm
dpkg-reconfigure ubuntu-desktop

```

will do the job. 

I can't vouch for whether this will fix your problem.  What this will do is reinstall and reconfigure the Gnome desktop environment - if the problem is with Gnome this might fix it.

---

### Post by elperrillo on 2010-09-15
Literalis:

Thanks for your help I executed you command and they worked. However I still have the same problem that did not solve ABSOLUTELY anything. 

Whenever I type the passowrd it does not let me in, I get kicked back to the login window again.

---

### Post by elperrillo on 2010-09-15
PROBLEM SOLVED!!!!

It was a samba issue, I went to and too a look at the logs at **/var/log/syslog** and spent quite some time there and finally saw an error that went something like...

**segfault error 4 in pam_smbpass**

So I went back to the login prompt and looked for all samba packages intalles using the command:

**dpkg -l *smb***

and then I decided to remote the libpam-smbpass package by executing

**sudo apt-get remove libpam-smbpass**

I rebooted and was able to log back on with no problems. Thanks to all of you that helped.

---

### Post by Sinone on 2011-01-17
Hi, I would like to suggest you a command!

try to type: sudo su -  [enter]
password: [password]

Hope it works!

---

