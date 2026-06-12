---
title: "why does 10.4 have so many permission issues?"
date: 2010-12-08
forum: General Help
---

### Post by eival on 2010-12-08
ive been using it for a few months after being on 8.04 since its release and it seems like everything i install and try to run gives me "permission denied" or just doesnt open at all by clicking their launch icons and i can only bypass it by using root terminal access.

in 8.04 there was a option to apply root/admin privileges to my normal user account to bypass all this, but in 10.4 i see no similar option, i tried adding my account to the Root "user group" but that doesnt fix anything.

did i screw something up on the isntall? otherwise ill prolly reinstall 8.04 cause i cant even use programs that are installed thru Synaptic except Firefox without issues.

---

### Post by tgm4883 on 2010-12-08
> **eival said:**
> ive been using it for a few months after being on 8.04 since its release and it seems like everything i install and try to run gives me "permission denied" or just doesnt open at all by clicking their launch icons and i can only bypass it by using root terminal access.

in 8.04 there was a option to apply root/admin privileges to my normal user account to bypass all this, but in 10.4 i see no similar option, i tried adding my account to the Root "user group" but that doesnt fix anything.

did i screw something up on the isntall? otherwise ill prolly reinstall 8.04 cause i cant even use programs that are installed thru Synaptic except Firefox without issues.

Odd, maybe a broken install. That definitly isn't usual. Maybe something you installed that changed permissions on stuff?  

Was it a fresh install? or did you upgrade/not format some partitions?

---

### Post by mlentink on 2010-12-08
Ubuntu 10.04 as such does not have any more permission 'issues' than 8.04. You problem most likely is caused by something you have changed yourself. The sudo system (to allow temporary administrator privileges to a normal user account) has not been changed, nor is there any reason to.

Perhaps you could inform us what exactly you did change in the form of permissions?

---

### Post by asmoore82 on 2010-12-08
There are no permission issues. (That I know of :P; running 10.04 since Beta)

There is a ***_**TON**_*** of bad advice out there that leads to countless permission issues. What's worse is that bad advice may not cause immediate problems, but leaves an underlying issue there waiting to pounce on you.

That having been said, if you attempted to circumvent sudo by running as the root account, your problem is the connection between the chair and the keyboard. If so, I say "attempted" because it obviously was not successful in the long run. It will never succeed(Ask Win 98/Me :P), you have been warned.

It is, somewhat OK to change your sudo configuration to not require the password on a certain "super admin" account. I say "somewhat" because this leads to the bad habit of using sudo early and often for every little problem without thought; and then you are back to the previous paragraph.

---

### Post by dcstar on 2010-12-08
> **asmoore82 said:**
> There are no permission issues. (That I know of :P; running 10.04 since Beta)

**There is a *[B]_**TON**_*** of bad advice out there[/B] that leads to countless permission issues. What's worse is that bad advice may not cause immediate problems, but leaves an underlying issue there waiting to pounce on you.
..........

Yep, and even worse are the people that blindly follow terminal commands for old releases and expect them to work the same in something different.

10.04 works fine when it is installed and used correctly, as tens (hundreds?) of thousands of Ubuntu users will attest to.

---

### Post by tgm4883 on 2010-12-09
> **dcstar said:**
> Yep, and even worse are the people that blindly follow terminal commands for old releases and expect them to work the same in something different.

10.04 works fine when it is installed and used correctly, as** tens (hundreds?) of thousands of Ubuntu users **will attest to.

Millions

---

### Post by oldos2er on 2010-12-09
Is this what you're referring to? [https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required](https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required)

---

### Post by viralmeme on 2010-12-09
> **eival said:**
> ive been using it for a few months after being on 8.04 since its release and it seems like everything i install and try to run gives me "permission denied"

Which apps are you trying to install and what method do you use for these installations.

---

### Post by eival on 2010-12-10
> **viralmeme said:**
> Which apps are you trying to install and what method do you use for these installations.

pretty much every app that wasnt preinstalled gives me issues.

Avidemux for example everytime i close it, i always get a popup:

can't open "/home/marcus/.avidemux/config.new": 13 (Permission denied)

WINE is another program i installed and when i try to run the config it never opens, if i use the terminal i get a message about how i dont have permission to create in the directory, which in result makes installing any .exe files impossible since i cant even set up WINE

i had similar issues with Virtual Box where i installed both open and closed source versions and neither would open when using the launch icons similar to WINE, so then i manually ran it as Root through terminal, which then made it only possible to ever run it as Root.

and all of those programs were installed via Ubuntu Software Center.


is there a system config file i could change to set everything back to normal an fix all this? otherwise i guess ill just have to reinstall it cause i cant remember all the terminal codes ive used

---

### Post by eival on 2010-12-10
> **mlentink said:**
> Ubuntu 10.04 as such does not have any more permission 'issues' than 8.04. You problem most likely is caused by something you have changed yourself. The sudo system (to allow temporary administrator privileges to a normal user account) has not been changed, nor is there any reason to.

yeah but i specifically remember having similar type issues in 8.04 but we were able to assign privileges to users via the System>Admin menu and now thats gone from the 10.4 menu, and no im not talking about those meaningless checkbox options in the "user groups" menu, there were checkboxes to assign root access for every possible scenario that would normally require you to use sudo without it, which is basically my issue now, except theres now no menu to assign those privileges.

---

### Post by tgm4883 on 2010-12-10
What is the output of

```
ls -l /home/marcus
ls -l /home/marcus/.avidemux
mount
```

Also, is your home directory on a network drive?

---

### Post by uRock on 2010-12-10
I advise against it, but if you want to get into the root account, then read this. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) It explains why it is a bad idea to have the account enabled, then it explains how to create and close the root account.

---

### Post by hawthornso23 on 2010-12-10
If it is prompting you for root permisison when it should not, then it is probably because something is owned by root that should not be. 

How can this happen? If you run as root, then any files generated in that process, including configuration files in your home directory, are going to end up being owned by root. This is the problem that gksudo is supposed to solve. 

It seems likely to me that the permission problems you are having now are caused by having run as root a lot in the past. 

You can try looking through your config files for ones owned by root. However it might be easier to just create a new user and copy all your files across.

---

### Post by uRock on 2010-12-10
Did you upgrade straight from 8.04 to 10.04? If you were using the root account in 8.04, then this could have messed things up and getting the root account back up and running might be sensible.

---

### Post by eival on 2010-12-17
> **tgm4883 said:**
> What is the output of

```
ls -l /home/marcus
ls -l /home/marcus/.avidemux
mount
```

Also, is your home directory on a network drive?

its installed on my hard drive and it was a fresh install, not an upgrade from 8.04.

here are my results to all 3 commands

```
marcus@marcus-desktop:~$ ls -l /home/marcus
total 80
drwxr-xr-x 10 marcus marcus 24576 2010-12-16 23:59 Desktop
drwxr-xr-x  2 marcus marcus  4096 2010-10-22 09:13 Documents
drwxr-xr-x  2 marcus marcus  4096 2010-11-25 01:09 Downloads
-rw-r--r--  1 marcus marcus   179 2010-10-22 09:02 examples.desktop
drwxr-xr-x  4 marcus marcus  4096 2010-10-23 03:04 GNUstep
-rw-r--r--  1 root   root       0 2010-11-29 21:51 java
drwxr-xr-x  8 root   root    4096 2010-11-29 01:06 jre1.6.0_22
drwxr-xr-x  3 marcus marcus  4096 2010-12-17 00:54 MOVIES
drwxr-xr-x  2 marcus marcus  4096 2010-10-22 09:13 Music
drwxr-xr-x  3 marcus marcus  4096 2010-12-01 19:59 Pictures
drwxr-xr-x  2 marcus marcus  4096 2010-10-22 09:13 Public
drwxr-xr-x  2 marcus marcus  4096 2010-12-05 02:24 sandbox
-rw-r--r--  1 root   root      24 2010-10-26 23:11 setup.xml
drwxr-xr-x  2 marcus marcus  4096 2010-10-22 09:13 Templates
drwxr-xr-x  2 marcus marcus  4096 2010-10-22 09:13 Videos
-rw-r--r--  1 root   root      28 2010-12-13 20:12 vlc-log.txt

```

i see that Java is under Root which could explain [[COLOR="DeepSkyBlue"]my issue with Java[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1633207") , any tips on fixing that as well?




```
marcus@marcus-desktop:~$ ls -l /home/marcus/.avidemux
total 8
-rw-r--r-- 1 root root 2917 2010-10-30 23:45 config
drwxr-xr-x 2 root root 4096 2010-10-30 23:45 custom

```



```
marcus@marcus-desktop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marcus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marcus)

```

i should also add that it seems my very own user folder "home/marcus" is under root as well cause GIMP and Firefox have saved some files in that directory by mistake in the past and when i tried to open i get no response but if i tried to move them to my desktop or trash i get a similar "permission denied" message. so maybe fixing my user home directory would fix all my other issues, since thats the default location and would explain why all recent apps ive tried isntalling arent accessible. is there an easy way to fix that?

---

### Post by jocko on 2010-12-17
> **eival said:**
> its installed on my hard drive and it was a fresh install, not an upgrade from 8.04.

here are my results to all 3 commands

```
marcus@marcus-desktop:~$ ls -l /home/marcus
total 80
drwxr-xr-x 10 marcus marcus 24576 2010-12-16 23:59 Desktop
drwxr-xr-x  2 marcus marcus  4096 2010-10-22 09:13 Documents
drwxr-xr-x  2 marcus marcus  4096 2010-11-25 01:09 Downloads
-rw-r--r--  1 marcus marcus   179 2010-10-22 09:02 examples.desktop
drwxr-xr-x  4 marcus marcus  4096 2010-10-23 03:04 GNUstep
-rw-r--r--  1 root   root       0 2010-11-29 21:51 java
drwxr-xr-x  8 root   root    4096 2010-11-29 01:06 jre1.6.0_22
drwxr-xr-x  3 marcus marcus  4096 2010-12-17 00:54 MOVIES
drwxr-xr-x  2 marcus marcus  4096 2010-10-22 09:13 Music
drwxr-xr-x  3 marcus marcus  4096 2010-12-01 19:59 Pictures
drwxr-xr-x  2 marcus marcus  4096 2010-10-22 09:13 Public
drwxr-xr-x  2 marcus marcus  4096 2010-12-05 02:24 sandbox
-rw-r--r--  1 root   root      24 2010-10-26 23:11 setup.xml
drwxr-xr-x  2 marcus marcus  4096 2010-10-22 09:13 Templates
drwxr-xr-x  2 marcus marcus  4096 2010-10-22 09:13 Videos
-rw-r--r--  1 root   root      28 2010-12-13 20:12 vlc-log.txt

```i see that Java is under Root which could explain [[COLOR=DeepSkyBlue]my issue with Java[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1633207") , any tips on fixing that as well?




```
marcus@marcus-desktop:~$ ls -l /home/marcus/.avidemux
total 8
-rw-r--r-- 1 root root 2917 2010-10-30 23:45 config
drwxr-xr-x 2 root root 4096 2010-10-30 23:45 custom

``````
marcus@marcus-desktop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marcus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marcus)

```i should also add that it seems my very own user folder "home/marcus" is under root as well cause GIMP and Firefox have saved some files in that directory by mistake in the past and when i tried to open i get no response but if i tried to move them to my desktop or trash i get a similar "permission denied" message. so maybe fixing my user home directory would fix all my other issues, since thats the default location and would explain why all recent apps ive tried isntalling arent accessible. is there an easy way to fix that?
This should clear everything up for you:
```
sudo chown -R marcus:marcus /home/marcus
```

I'm not sure what caused your problem, but one thing I can think of that could change the permissions on files in your home folder is running graphical applications with sudo (use gksudo instead).

---

### Post by amsterdamharu on 2010-12-17
Probably you don't own all the files in your home dir. To fix this you can change ownership with this command:

cd ~;sudo chown -R marcus:marcus ../marcus

Haha, you beat me to it.

---

### Post by eival on 2010-12-17
> **jocko said:**
> This should clear everything up for you:
```
sudo chown -R marcus:marcus /home/marcus
```

I'm not sure what caused your problem, but one thing I can think of that could change the permissions on files in your home folder is running graphical applications with sudo (use gksudo instead).

okay when i entered that i got this message

```
chown: cannot access `/home/marcus/.gvfs': Permission denied

```

i noticed that amsterdamharu code is slightly different, should i try that instead?

i wanna make sure before i go doing both an mess things up more:p

---

### Post by amsterdamharu on 2010-12-17
Could you tell us the output of?

```
ls -d -l /home/marcus/.gvfs
```If you run the command as sudo then root should change the owner of all the files in /home/marcus to marcus unless you didn't copy and paste the commands right.

---

### Post by dcstar on 2010-12-18
> **eival said:**
> 
..........
i wanna make sure before i go doing both an mess things up more:p

How about telling people what "sudo" commands you have run on your system previously to break things in this manner?

---

### Post by eival on 2010-12-18
> **amsterdamharu said:**
> Could you tell us the output of?

```
ls -d -l /home/marcus/.gvfs
```If you run the command as sudo then root should change the owner of all the files in /home/marcus to marcus unless you didn't copy and paste the commands right.

```
dr-x------ 2 marcus marcus 0 2010-12-17 22:15 [COLOR="DeepSkyBlue"]/home/marcus/.gvfs[/COLOR]

```

so you're telling me to add sudo to that above command, and it will fix everything?

i edited the text color just like the terminal has it, if it means anything

---

### Post by uRock on 2010-12-18
> **dcstar said:**
> How about telling people what "sudo" commands you have run on your system previously to break things in this manner?
The best way to get all of the previous commands is with the **history** command.

---

### Post by CharlesA on 2010-12-18
You can't use sudo to access .gvfs.

The permissions are set correctly.

---

### Post by amsterdamharu on 2010-12-18
The directory .gvfs is read only and execute for the owner unless you temper with it the system would never set permissions like that. If you execute the ***mand as I told you it would not give an error (I think) because even if root has no access to the file/directory it can still access the file/directory that's why it's root.

```
[COLOR=Red]sudo[/COLOR] chown -R marcus:marcus /home/marcus
sudo find /home/marcus/ -type d -exec chmod +x '{}' \;
chmod 770 /home/marcus/.gvfs
```I added the second one because besides having owner ship problems you seem to have changed execute and read permissions as well and a directory always needs execute permission.

The third line gives .gvfs read and write access.

Try to copy and paste ***mands from this page into the terminal. Any error please copy and paste the whole lot from the terminal and post it here so we can see what's going on there and what ***mands are actually issued.

---

### Post by amsterdamharu on 2010-12-18
> You can't use sudo to access .gvfs.

I think you can:

```
myuser@my***puter:~/$ chmod 500 test
myuser@my***puter:~/$ ls -ld test
dr-x------ 2 myuser myuser 4096 2010-12-19 12:23 test
myuser@my***puter:~/$ sudo chown -R myuser:myuser test
myuser@my***puter:~/$ ls -ld test
dr-x------ 2 myuser myuser 4096 2010-12-19 12:23 test
myuser@my***puter:~/$ ls -l test
total 4
-rw-r--r-- 1 myuser myuser 4 2010-12-19 12:23 aaaaa
myuser@my***puter:~/$ sudo whoami
root
```

---

### Post by eival on 2010-12-19
> **amsterdamharu said:**
> The directory .gvfs is read only and execute for the owner unless you temper with it the system would never set permissions like that. If you execute the ***mand as I told you it would not give an error (I think) because even if root has no access to the file/directory it can still access the file/directory that's why it's root.

```
[COLOR=Red]sudo[/COLOR] chown -R marcus:marcus /home/marcus
sudo find /home/marcus/ -type d -exec chmod +x '{}' \;
chmod 770 /home/marcus/.gvfs
```I added the second one because besides having owner ship problems you seem to have changed execute and read permissions as well and a directory always needs execute permission.

The third line gives .gvfs read and write access.

Try to copy and paste ***mands from this page into the terminal. Any error please copy and paste the whole lot from the terminal and post it here so we can see what's going on there and what ***mands are actually issued.

it just keeps saying permission denied


also if i type sudo su to become root, i notice it says root@marcus, rather than root@root, could it be an issue with my user groups settings? i think i checked my name under a few different groups in hopes of bypassing this issue before (adm / admin / root / sudo / ect...)

---

### Post by jocko on 2010-12-19
> **amsterdamharu said:**
> I think you can:

```
myuser@my***puter:~/$ chmod 500 test
myuser@my***puter:~/$ ls -ld test
dr-x------ 2 myuser myuser 4096 2010-12-19 12:23 test
myuser@my***puter:~/$ sudo chown -R myuser:myuser test
myuser@my***puter:~/$ ls -ld test
dr-x------ 2 myuser myuser 4096 2010-12-19 12:23 test
myuser@my***puter:~/$ ls -l test
total 4
-rw-r--r-- 1 myuser myuser 4 2010-12-19 12:23 aaaaa
myuser@my***puter:~/$ sudo whoami
root
```
Nope. You can't do anything to .gvfs while gnome is running. But there is no need to change that.

Eival: You should really just make sure that you change ownership on the files and folders in your home directory that are currently owned by root, the rest are fine.
Check the output of:
```
ls -la ~/
```For every file or folder (except the link "..") that is not owned by your user (marcus) and group (marcus), run:
```
sudo chown -R marcus:marcus [COLOR=Blue]filemame[/COLOR]

```And you should also make sure that in the future you **never, ever run a command with sudo when it's not necessary**, and *if* you ever need to run a graphical application as root you should **use gksudo instead of sudo** to avoid changing permissions in your home directory...

---

### Post by amsterdamharu on 2010-12-19
@jocko
Ok, so that directory locked by gnome and it's not a owner/permission problem. I thought you meant to say sudo won't work because root don't have any access to the directory. Good thing about root is that you can repair whatever (even when execute is taken off directories) because root can do whatever.

@marcus/eival
Don't worry, your problems should be solved but if you want to be 100% sure than exit gdm:
press control + alt + F1 and type the following commands
```
sudo service gdm stop
sudo chown -R marcus:marcus /home/marcus
sudo find /home/marcus/ -type d -exec chmod +x '{}' \;
sudo service gdm start
```

---

### Post by eival on 2010-12-19
> **amsterdamharu said:**
> 
@marcus/eival
Don't worry, your problems should be solved but if you want to be 100% sure than exit gdm:
press control + alt + F1 and type the following commands
```
sudo service gdm stop
sudo chown -R marcus:marcus /home/marcus
sudo find /home/marcus/ -type d -exec chmod +x '{}' \;
sudo service gdm start
```

awesome, i ran those codes an dont see any errors:popcorn:

---

