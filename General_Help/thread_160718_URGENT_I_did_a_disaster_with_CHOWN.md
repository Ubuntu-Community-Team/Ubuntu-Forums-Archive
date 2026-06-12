---
title: "**URGENT** I did a disaster with CHOWN"
date: 2006-04-15
forum: General Help
---

### Post by ashrack on 2006-04-15
this is what I typed:
```
sudo chown tom:tom / -R
```
dont know what I was thinking. Since I wanted to type:
```
sudo chown tom:tom /media/d/ -R
```
Because FF complained about some permission problems when saving WEB PAGES to a CIFS mounted share.

How can I repair the damage??? I've left the same *cursed* console opened as it is and havent opened any new progs since the disaster. 
Can this be fixed cos I would really hate to do a reinstall of my 5months old BREEZY..

ps. I was thinking of doing the following
```
sudo chown root:root / -R
```

and then on my home directory do:
```
sudo chown tom:tom /home/tom/ -R
```
What do U think?
Urgently awaiting your replies!!!

---

### Post by Ramses de Norre on 2006-04-15
Sounds like a suitable solution ;)

---

### Post by PriceChild on 2006-04-15
And don't forget to do it to /media/d/ as first intended :)

---

### Post by graigsmith on 2006-04-15
i think your pretty much going to have to reinstall.
there are files all throughout the system that need to be owned by special users.
for example, ntp.drift must be owned by the ntp user.

im sure there are more things that will need to be owned by special groups, but i dont know what they are.

---

### Post by engla on 2006-04-15
Your solution should probably work a long way.. changing owner isn't at all as fatal as changing mode (permissions) all over.

basically, on my system it seems almost all none-/home and none-/var files are owned by root.

---

### Post by ashrack on 2006-04-15
When I do this:
```
chown root:root / -R
```
I get the following:
```
chown: changing ownership of `/dev/vcsa2': Operation not permitted
```
about everything in system.

And when trying to go SU I get the following:
```
tom@pegasus:/media/d/linux/guides$ sudo -s
sudo: must be setuid root
tom@pegasus:/media/d/linux/guides$ su
Password:
setgid: Operation not permitted
tom@pegasus:/media/d/linux/guides$

```

If I were to go to INIT 1 would it help?

---

### Post by Ramses de Norre on 2006-04-15
Does it work when you do it with sudo?

---

### Post by ashrack on 2006-04-15
Yes I did, but this is what I got:
```
tom@pegasus:/media/d/linux/guides$ sudo chown root:root / -R
sudo: must be setuid root

```

DŽAKAJ ME NE MARAŠ

---

### Post by aysiu on 2006-04-15
Try booting into recovery mode. When you do that, you should automatically be logged in as root.

---

### Post by ashrack on 2006-04-15
[QUOTE=aysiu]Try booting into recovery mode. When you do that, you should automatically be logged in as root.[/QUOTE]
Did that, and when I was root I typed without any errors:
```
chown root:root / -R && chown tom:tom /home/tom -R
```
and when I rebooted the machine I still get this error:
```
tom@pegasus:/$ sudo chown -R root:root /
sudo: must be setuid root

```
or
```
tom@pegasus:/$ sudo synaptic
sudo: must be setuid root
```

ps. Ive checked the system with "ls -l" and what I checked said that it was ROOT

---

### Post by aysiu on 2006-04-15
I Googled your error and came up with these two threads. They may help.

[http://ubuntuforums.org/printthread.php?t=16958](http://ubuntuforums.org/printthread.php?t=16958)
[http://ubuntuforums.org/archive/index.php/t-5494.html](http://ubuntuforums.org/archive/index.php/t-5494.html)

---

### Post by Ramses de Norre on 2006-04-15
```
chmod 4111 /usr/local/bin/sudo
```

---

### Post by localzuk on 2006-04-15
You are going to have to do a re-install. There are files all over the system that have special ownerships to various users. To fix them all would take many days - even if you know them all.

The simplest solution is to re-install I'm afraid.

---

### Post by ashrack on 2006-04-15
[QUOTE=Ramses de Norre]```
chmod 4111 /usr/local/bin/sudo
```[/QUOTE]
4M that does not exist. But I did "locate sudo" and then found the following in recovery mode:
```
chmod 4111/usr/bin/sudo[
```
but now when I do:
```
tom@pegasus:/$ ls -l /usr/bin/sudo
---s--x--x  1 root root 98916 2006-01-09 11:41 /usr/bin/sudo

```
What is this new "S" permission, I've never seen it B4??

But anyway it works OK now.

---

### Post by Ramses de Norre on 2006-04-15
The S is the symbol for SUID
> SUID or setuid: change user ID on execution. If setuid bit is set, when the file will be executed by a user, the process will have the same rights as the owner of the file being executed.
In this case owner is root.

---

### Post by arch stanton on 2006-04-15
If it makes you feel any better, I did the same thing last year in slackware... since I figured was gonna have  reinstall anyway , I installed Ubuntu to give it a try and have been been with Ubuntu ever since.

I also formatted all three of my hard drives trying to install red hat 4-5 years ago, so take comfort in knowing there are bigger dumbasses out there;}

---

### Post by Toxicity999 on 2006-04-15
This seems like a right of passage in Linux transition... we have that moment of... I'm sick of sudo........... I KNOW! or we do it accidently like that. Which is what I have done before.

---

### Post by ashrack on 2006-04-16
> **arch stanton]If it makes you feel any better, I did the same thing last year in slackware... since I figured was gonna have  reinstall anyway , I installed Ubuntu to give it a try and have been been with Ubuntu ever since.

I also formatted all three of my hard drives trying to install red hat 4-5 years ago, so take comfort in knowing there are bigger dumbasses out there said:**
> 
Im a person that hates reinstalls, like who doesnt;) I do almost everything to avoid a reinstall. Since it is my believe that a good OS doesnt need a reinstall every half a year if U treat it right. And so is this situation, am to stuborn to reinstall it at least till DAPPER is out. Every fool can reinstall an OS but fixing a fubared OS, now that is a challenge.

[QUOTE=Toxicity999]This seems like a right of passage in Linux transition... we have that moment of... I'm sick of sudo........... I KNOW! or we do it accidently like that. Which is what I have done before.
I personally love SUDO. Its much easier than having to go to SU to change some root settings. This was a big issue on MDK9 4M.

@ALL
apperantly the system works now. But havent done any real testing yet.But I already found a problem which I found a quick hack 4 it.

```
tom@pegasus:/var/spool/cron/atjobs$ at +5min
warning: commands will be executed using /bin/sh
Cannot open lockfile /var/spool/cron/atjobs/.SEQ: Permission denied

```
this are the permissions for the .SEQ file:
```
-rw-------  1 root root    6 2006-04-16 09:50 .SEQ
```
if I do 
```
sudo chmod ugo=rw .SEQ
```
than "at" works. But is this the correct procedure?

ps. dont know if this is relevant but "sudo at +5min" naturally works..

---

### Post by ubernoob on 2006-04-16
> And so is this situation, am to stuborn [-(  to reinstall it at least till DAPPER is out. Every fool can reinstall an OS but fixing a fubared OS, now that is a challenge.

Well... every fool can change back the permission too. But only the ones with too much spare time does it. I suggest you install dapper. It's seems like it is more stable than the user it will have (you). ;)

Or you can try another popular command "(Edit: removed in case a noob enters ;))" and try recovering after that :-\" 

To boot into single user mode in grub:

   1.      If you have a GRUB password configured, type p and enter the password.
   2.      Select ubuntu with the version of the kernel that you wish to boot and type e for edit. You will be presented with a list of items in the configuration file for the title you just selected.
   3.      Select the line that starts with kernel and type e to edit the line.
   4.      Go to the end of the line and type single as a separate word (press the [Spacebar] and then type single). Press [Enter] to exit edit mode.
   5.      Back at the GRUB screen, type b to boot into single user mode.

---

### Post by towsonu2003 on 2006-04-16
Your stubbornness is an inspiration. no, really :)

Here is my (stupid) idea. apt-get linux-headers and build-essential as well *** gcc-3.4 and maybe gcc-3.3. Install [vmware player]("http://www.vmware.com/products/player/") (untar, use install.sh) and its [ubuntu image]("http://www.vmware.com/vmtn/appliances/directory/ubuntu.html") (untar, do vmplayer where it is untarred). Than run ubuntu under ubuntu (called emulation, one OS within another) and check permissions and ownerships between emulated ubuntu and real ubuntu. It may be easier than finding small glitches and fixing them along the way. 

This should work nicely if you can install vmware.

And one thing (I saw this happening before with newbies trying out commands, even after notifications and stuff):
[quote=ubernoob]Or you can try another popular command [size=5]"sudo rm -rf /"[/size] and try recovering after that[/quote] [SIZE="6"]this command wipes off your hard disk!! [color=red]Do NOT try it[/color][/SIZE] ubernoob might want to remove that from his/her post too?

Overkill?

---

### Post by ubernoob on 2006-04-16
I guess you are right...There... it's gone.8-[

---

### Post by ashrack on 2006-04-16
[QUOTE=ubernoob]
To boot into single user mode in grub:

   1.      If you have a GRUB password configured, type p and enter the password.
   2.      Select ubuntu with the version of the kernel that you wish to boot and type e for edit. You will be presented with a list of items in the configuration file for the title you just selected.
   3.      Select the line that starts with kernel and type e to edit the line.
   4.      Go to the end of the line and type single as a separate word (press the [Spacebar] and then type single). Press [Enter] to exit edit mode.
   5.      Back at the GRUB screen, type b to boot into single user mode.[/QUOTE]
Or U just choose RECOVERY MODE!

---

### Post by ubernoob on 2006-04-16
i forgot ubuntu came with that. Way to long ago since i rebooted ;)

---

### Post by ashrack on 2006-04-16
> **ubernoob]i forgot ubuntu came with that. Way to long ago since i rebooted  said:**
> 
I learned a lot about GRUB when I was learning how to compile custom kernels and adding support for SWSUP2. Even on my DESKTOP computer I cant live without hibernation. Since its so good when U turn off computer when U go to bed and just start it up in the morning and U continue doing your work where U left it
[QUOTE=towsonu2003]Your stubbornness is an inspiration. no, really :)

Here is my (stupid) idea. apt-get linux-headers and build-essential as well *** gcc-3.4 and maybe gcc-3.3. Install [vmware player]("http://www.vmware.com/products/player/") (untar, use install.sh) and its [ubuntu image]("http://www.vmware.com/vmtn/appliances/directory/ubuntu.html") (untar, do vmplayer where it is untarred). Than run ubuntu under ubuntu (called emulation, one OS within another) and check permissions and ownerships between emulated ubuntu and real ubuntu. It may be easier than finding small glitches and fixing them along the way. 

This should work nicely if you can install vmware.

Gonna give it a try. It sunday and tomorrow is a national holiday so I have lots of time.
> And one thing (I saw this happening before with newbies trying out commands, even after notifications and stuff):
 [SIZE="6"]this command wipes off your hard disk!! [color=red]Do NOT try it[/color][/SIZE] ubernoob might want to remove that from his/her post too?

Overkill?
Such commands should never be inputed in the forums. Cos lots of PPL just do copy&paste without knowing anything what the command does.

---

### Post by ashrack on 2006-04-17
Ive succesfully installed VMWARE and launched virtual UBUNTU in it.
And then changed the .SEQ permissions and all of the previous folders to match the VIRTUAL UBUNTU. But I still get the following error:
> tom@pegasus:/var/spool/cron/atjobs$ at +5min
warning: commands will be executed using /bin/sh
Cannot open lockfile /var/spool/cron/atjobs/.SEQ: Permission denied

ps. so as a workarround I did, 
```
chmod o=rw .SEQ
```

---

### Post by towsonu2003 on 2006-04-17
Here is the permissions on my install:

```
sudo ls -l /var/spool/cron/atjobs/.SEQ
Password:
-rw-------  1 daemon daemon 0 2005-08-04 10:47 /var/spool/cron/atjobs/.SEQ

```
from the directory structure, it seems related to cron. making it writable to everyone (o=wr) may be a high security risk, though I'm not sure. if cron reads that file to start the job it refers to, than one can access your computer, change the contents of that file, and launch something with cron's permissions (usually root in Ubuntu). 

I have to say I'm not sure what I'm talking about here ;)

---

### Post by ashrack on 2006-04-18
I've set mine to be like that, but it still gives me permission denied

---

### Post by varunus on 2006-04-18
The issue is, files also sometimes need to have their UID set to those of a different user.  All of the printing stuff, for example, is owned by cups, and has setuid cups.  This way, any user in the cups group can print.

I'd honestly say just reinstall.  Otherwise, every time you try to use your computer to do something new, you'll find new, fresh permissions problems waiting.  And if you're on a schedule and need to get something done right then...well, its better to have a clean OS.

Why not upgrade to the Dapper Beta that just came out?

---

### Post by ashrack on 2006-04-18
[QUOTE=varunus]
Why not upgrade to the Dapper Beta that just came out?[/QUOTE]
When? I thought the latest was DAPPER ALPHA - FLIGHT 6??

[http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)

---

