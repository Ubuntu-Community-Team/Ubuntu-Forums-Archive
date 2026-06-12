---
title: "Permissions Error in Firefox1.5.0.1"
date: 2006-02-13
forum: General Help
---

### Post by Red Knuckles on 2006-02-13
After using Automatix to replace Firefox1.0.7 with Firefox1.5.0.1 I get the following error message:
Read and write permissions are needed for the following file: /home/username/.mozilla/firefox/qqdqllmb.default/forecastfox/profiles.xml

How do I correct this?:confused:

---

### Post by sbassett on 2006-02-13
[QUOTE=Red Knuckles]After using Automatix to replace Firefox1.0.7 with Firefox1.5.0.1 I get the following error message:
Read and write permissions are needed for the following file: /home/username/.mozilla/firefox/qqdqllmb.default/forecastfox/profiles.xml

How do I correct this?:confused:[/QUOTE]

Your best bet would be the terminal. Applications->Terminal.

When the terminal opens, simply type the following:

chown -R username.usergroup .mozilla/*

chmod -R 770 .mozilla/*

What this does is change the ownership of everything within .mozilla to username and usergroup (which would be your user). 99.9% of the time, the main group of the user is named the same as the user itself. So joe would be the member of the joe group.

The second line gives full access to everything in the .mozilla directory to user  joe and group joe (from example listed above) and prevents anyone else (other) from seeing, writing, or executing the contents.

Rerun firefox and you should be set.

---

### Post by Red Knuckles on 2006-02-13
[QUOTE=sbassett]Your best bet would be the terminal. Applications->Terminal.

When the terminal opens, simply type the following:

chown -R username.usergroup .mozilla/*

chmod -R 770 .mozilla/*

What this does is change the ownership of everything within .mozilla to username and usergroup (which would be your user). 99.9% of the time, the main group of the user is named the same as the user itself. So joe would be the member of the joe group.

The second line gives full access to everything in the .mozilla directory to user  joe and group joe (from example listed above) and prevents anyone else (other) from seeing, writing, or executing the contents.

Rerun firefox and you should be set.[/QUOTE]

Here's what I got:

zzz@ubuntu:~$  chown -R zzz.zzz .mozilla/*
chown: changing ownership of `.mozilla/firefox/qqdqllmb.default/forecastfox/profiles.bak': Operation not permitted
chown: changing ownership of `.mozilla/firefox/qqdqllmb.default/forecastfox/profiles.xml': Operation not permitted

I'm only including the last 2 lines but every line says 'operation not permitted'.

When I ran as sudo:

zzz@ubuntu:~$ sudo chown -R zzz.zzz .mozilla/*
Sorry, user zzz is not allowed to execute '/bin/chown -R zzz.zzz .mozilla/firefox' as root on localhost.localdomain.

I seem to have a permissions problem [after running automatix, this isn't the only error that has come up]. Can anyone help me???:confused:

---

### Post by sbassett on 2006-02-13
[QUOTE=Red Knuckles]Here's what I got:

ben@ubuntu:~$  chown -R ben.ben .mozilla/*
chown: changing ownership of `.mozilla/firefox/qqdqllmb.default/forecastfox/profiles.bak': Operation not permitted
chown: changing ownership of `.mozilla/firefox/qqdqllmb.default/forecastfox/profiles.xml': Operation not permitted

I'm only including the last 2 lines but every line says 'operation not permitted'.

When I ran as sudo:

ben@ubuntu:~$ sudo chown -R ben.ben .mozilla/*
Sorry, user ben is not allowed to execute '/bin/chown -R ben.ben .mozilla/firefox' as root on localhost.localdomain.

I seem to have a permissions problem [after running automatix, this isn't the only error that has come up]. Can anyone help me???:confused:[/QUOTE]

Is this the same user you created during setup? Is this your setup?

---

### Post by towsonu2003 on 2006-02-13
[QUOTE=Red Knuckles]```

zzz@ubuntu:~$ sudo chown -R zzz.zzz .mozilla/*
Sorry, user zzz is not allowed to execute '/bin/chown -R zzz.zzz .mozilla/firefox' as root on localhost.localdomain.

```
[/QUOTE]
is user "zzz" in /etc/sudoers? It should be if zzz was the first account you created after a fresh ubuntu install. I would contact the developer of automatix via its sub-forum though so that he fixes this.

I think the origin of this is running the firefox update with sudo, which changes the ownership of /home/zzz/.mozilla/firefox/somefile during update[/code]

---

### Post by Red Knuckles on 2006-02-13
[QUOTE=Red Knuckles]Here's what I got:

zzz@ubuntu:~$  chown -R zzz.zzz .mozilla/*
chown: changing ownership of `.mozilla/firefox/qqdqllmb.default/forecastfox/profiles.bak': Operation not permitted
chown: changing ownership of `.mozilla/firefox/qqdqllmb.default/forecastfox/profiles.xml': Operation not permitted

I'm only including the last 2 lines but every line says 'operation not permitted'.

When I ran as sudo:

zzz@ubuntu:~$ sudo chown -R zzz.zzz .mozilla/*
Sorry, user zzz is not allowed to execute '/bin/chown -R zzz.zzz .mozilla/firefox' as root on localhost.localdomain.

I seem to have a permissions problem [after running automatix, this isn't the only error that has come up]. Can anyone help me???:confused:[/QUOTE]

I may have spoken to soon. I ran both commands as suggested as regular user and even though it said 'Operation not permitted' after each line the error message has gone away. Did I do this correctly? I'm not sure what I just did!:)

---

### Post by towsonu2003 on 2006-02-13
[QUOTE=Red Knuckles]I may have spoken to soon. I ran both commands as suggested as regular user and even though it said 'Operation not permitted' after each line the error message has gone away. Did I do this correctly? I'm not sure what I just did!:)[/QUOTE]
what's the output of ```
firefox
``` any errors? you could check the ownerships of those files by ```
ls -l mozilla/firefox/qqdqllmb.default/forecastfox/ 
``` all ownerships must be youruser:youruser There shouldn't be any root ownership in there.
also check if forecastfox extension is working properly. 
And finally, let the developer of automatix know... s/he may need to change the way it updates firefox.

---

### Post by Red Knuckles on 2006-02-13
[QUOTE=towsonu2003]what's the output of ```
firefox
``` any errors? you could check the ownerships of those files by ```
ls -l mozilla/firefox/qqdqllmb.default/forecastfox/ 
``` all ownerships must be youruser:youruser There shouldn't be any root ownership in there.
also check if forecastfox extension is working properly. 
And finally, let the developer of automatix know... s/he may need to change the way it updates firefox.[/QUOTE]

When I run 'firefox' it simply opens firefox. When I run:

zzz@ubuntu:~$ ls -l mozilla/firefox/qqdqllmb.default/forecastfox/

I get:

ls: mozilla/firefox/qqdqllmb.default/forecastfox/: No such file or directory

Due to another problem [with firestarter] I tried to change 'sudo visudo' and now I can't do anything as root. I get an error message like:

zzz@ubuntu:~$ sudo apt-get update
Sorry, user zzz is not allowed to execute '/usr/bin/apt-get update' as root on localhost.localdomain.

So now I _**REALLY**_ need help.

---

### Post by arnieboy on 2006-02-13
do two things:
first of all go to system --> administration--> users and groups and make sure your user name is included in group "**admin**". after that is done, please paste the results of the following command:
```
sudo cat /etc/sudoers
```

---

### Post by Red Knuckles on 2006-02-13
[QUOTE=arnieboy]do two things:
first of all go to system --> administration--> users and groups and make sure your user name is included in group "**admin**". after that is done, please paste the results of the following command:
```
sudo cat /etc/sudoers
```[/QUOTE]

Uh, I logged out of Ubuntu to try 'Rescue Mode' with Install CD and now I can't get back in. I can get to login screen and then next screen with 'Window Manager' but then it stops. Sure could use some help! This computer is dual boot w/Mandriva on the other partition but I would prefer to use Ubuntu as my main system.

---

### Post by towsonu2003 on 2006-02-13
[QUOTE=Red Knuckles]
zzz@ubuntu:~$ ls -l mozilla/firefox/qqdqllmb.default/forecastfox/
[/quote]
yep, my stupidity, sorry. [/code]ls -l /home/yourusername/.mozilla/firefox/qqdqllmb.default/forecastfox/[/code]
[QUOTE=Red Knuckles]
Due to another problem [with firestarter] I tried to change 'sudo visudo' and now I can't do anything as root. I get an error message like:
[/QUOTE]
You don't need to open firestarter everytime you login, it will run in the background w/out problems. use it only when you need to change settings / configuration / open close ports etc.
As far as I know, as long as your sudoers file looks like this (below), you shouldn't have problems:
> 
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
**yourusername**  ALL=(ALL) ALL

but automatix may need otherwise?

But you probably cannot see it as you cannot use sudo now, so you will not be able to edit this with sudo visudo...

PS. I was going to post something about how to get back to your sudoers file using the Livecd, but I don't really know how sudo visudo works (this is the command you're supposed to use when you need to edit /etc/sudoers), so I didn't wanna cause more troubles.

---

### Post by towsonu2003 on 2006-02-13
[QUOTE=Red Knuckles]Uh, I logged out of Ubuntu to try 'Rescue Mode' with Install CD and now I can't get back in. I can get to login screen and then next screen with 'Window Manager' but then it stops. Sure could use some help! This computer is dual boot w/Mandriva on the other partition but I would prefer to use Ubuntu as my main system.[/QUOTE]
what did you do in the rescue mode? step by step, with details? also, just in case, do you have a live cd?

---

### Post by Red Knuckles on 2006-02-13
[QUOTE=towsonu2003]what did you do in the rescue mode? step by step, with details? also, just in case, do you have a live cd?[/QUOTE]

In rescue mode, log in and select Ubuntu-kernel-Rescue Mode I added these lines to /etc/sudoers .tmp:

root     All = [All] All
username.username     All = [All] All

The file was empty when I got there and that is all I've done in Rescue Mode. I still can't log in to Ubuntu so what I did was wrong or not enough. [I tried to use the man page for sudoer].

---

### Post by sbassett on 2006-02-13
Red -

I am going through the motions now, and will post back with exact instructions. In the meantime, how do you have your harddisk partitioned? Just / with swap? This is the default. Or do you have multiple partitions?

"df" should list all your partitions.

Be back in a few.

---

### Post by towsonu2003 on 2006-02-13
[QUOTE=Red Knuckles]
The file was empty when I got there and that is all I've done in Rescue Mode. I still can't log in to Ubuntu so what I did was wrong or not enough. [I tried to use the man page for sudoer].[/QUOTE]
I'm not sure if this will work, but let's try it... no guarantees.... I never tried doing this! read all first to decide whether you wanna do this. this assumes you  know which partition is your / (root folder; C: in Windows terms) in ubuntu.
1. Take notes about the /etc/sudoers file I posted previously
2. Boot from the install cd, at boot promt, type rescue and hit enter. 
3. when it gives you the sh# prompt (or similar, where you can type commands), hit ctrl+alt+f2, press enter
4. mount / partition
```

mkdir ubunturoot
mount /dev/rootpartition /ubunturoot -t ext3
ls /ubunturoot

```
ls /ubunturoot will give you a list of what you have in the root partition, just to check wether you are in the right place
5. chroot into ubuntu /
```

chroot bash /ubunturoot

```
6. edit sudoers like this
```

visudo

```
If everything went fine, this will open up /etc/sudoers in nano (command line editor, easy to use, look at the bottom of screen for important stuff to do)
7. change your sudoers file to your needs = make it look like mine, but use your own username
yourusername ALL=(ALL) ALL  - not yourusername.yourusername at the end....
8. hit ctrl+O (letter) to write changes
9. hit ctrl+X to close nano
10. it will tell you that sudoers file was updated (hopefully)
11. type: exit to get out
12. reboot (command to reboot is reboot, take the livecd out before it boots from it again)

Note: 
If you do not know where your ubuntu / is, list partitions with ```
fdisk -l
```
mkdir for each one, mount each one, and list the contents of each one (with ls). ubuntu / will have a "media" folder in it (and hopefully Mandriva does not have one. 

I am really hoping that this will work...

---

### Post by sbassett on 2006-02-13
[QUOTE=Red Knuckles]In rescue mode, log in and select Ubuntu-kernel-Rescue Mode I added these lines to /etc/sudoers .tmp:

root     All = [All] All
username.username     All = [All] All

The file was empty when I got there and that is all I've done in Rescue Mode. I still can't log in to Ubuntu so what I did was wrong or not enough. [I tried to use the man page for sudoer].[/QUOTE]

OK RED,

This should put you back in the saddle again. We will remove the firestarter no password issue and change this back to the original state.

Boot into rescue. If Ubuntu is the main OS, then you will select part1. Go through the defaults until you get to the sh: prompt. I found this pretty useless. So press Ctrl+Alt+F2, this will bring you to a second terminal, asking you to press Enter to start. Go ahead and press enter. Now type :
```
nano /target/etc/sudoers
```
This will open the sudoers file in nano, simply move around with the arrows and erase and retype like you were in a regular text editor.

replace the firestarter line with the following:
```
%admin  ALL=(ALL) ALL
```
After this has been finished, press Ctrl+O to "write out" (aka save) accept the  default, then Ctrl+X to exit the file. You may now type exit, then CTRL+ALT+F1 and exit out of this terminal, this will reboot the computer.

Please make sure the line above is exact. Please let me know if you have any issues.

---

### Post by Red Knuckles on 2006-02-13
Quote:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
yourusername ALL=(ALL) ALL


I tried to make my /etc/sudoers.tmp file look EXACTLY like yours except of course for username. 

It gave me syntax error Line 18:

# User privilege specification

And line 21:

# Members of the admin group may gain root privileges

I couldn't figure out the errors so I'm back in Mandriva.

---

### Post by towsonu2003 on 2006-02-13
[QUOTE=Red Knuckles]I tried to make my /etc/sudoers.tmp[/QUOTE]
You should be changing /etc/sudoers , not /etc/sudoers.tmp. the .tmp file is created by the program visudo while you are changing sudoers using visudo.

Refer back to [http://ubuntuforums.org/showpost.php?p=730156&postcount=16](http://ubuntuforums.org/showpost.php?p=730156&postcount=16) first (much easier),
if it doesn't work, refer to [http://ubuntuforums.org/showpost.php?p=730156&postcount=15](http://ubuntuforums.org/showpost.php?p=730156&postcount=15) (more complicate and not sure if it will work)

Edited AGAIN: links were in wrong sequence...

---

### Post by sbassett on 2006-02-13
[QUOTE=Red Knuckles]Quote:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
yourusername ALL=(ALL) ALL


I tried to make my /etc/sudoers.tmp file look EXACTLY like yours except of course for username. 

It gave me syntax error Line 18:

# User privilege specification

And line 21:

# Members of the admin group may gain root privileges

I couldn't figure out the errors so I'm back in Mandriva.[/QUOTE]
I hope you reconsider at some point, I am still puzzled as to the /etc/sudoers.tmp. When you open the second terminal everything on the main system will be prefixed by /target (i.e. /target/etc/sudoers). I created a test modification and she worked like a peach.

---

### Post by Red Knuckles on 2006-02-13
[QUOTE=sbassett]Red -

I am going through the motions now, and will post back with exact instructions. In the meantime, how do you have your harddisk partitioned? Just / with swap? This is the default. Or do you have multiple partitions?

"df" should list all your partitions.

Be back in a few.[/QUOTE]

As far as partitions when I turn on computer bios goes to a menu:

Ubuntu-latest kerenal
Ubuntu-latest kerenal Recovery Mode
Ubuntu-next latest kernel
Ubuntu-next latest kerenal Recovery Mode
Mem Test
Mandriva
Mandriva Failsafe

Ubuntu is on /dev/hda3
Mandriva is on /dev/hda2
I think swap is on /dev/hda4

When I run 'df' in Mandriva I get:

[zzz@c-vv-vvv-vvv-vv ~]$ df
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              73G  2.4G   67G   4% /

---

### Post by sbassett on 2006-02-13
I would guess that ubuntu is on part2. Not sure what is residing on hda1.

---

### Post by towsonu2003 on 2006-02-13
[QUOTE=Red Knuckles]
When I run 'df' in Mandriva I get:

[zzz@c-vv-vvv-vvv-vv ~]$ df
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              73G  2.4G   67G   4% /[/QUOTE]
If mandriva gives this, hda2 is not your ubuntu root. what does fdisk -l say?

---

### Post by sbassett on 2006-02-13
[QUOTE=towsonu2003]If mandriva gives this, hda2 is not your ubuntu root. what does fdisk -l say?[/QUOTE]
Good catch, my bad. I would say part3. Again, sorry.

---

### Post by Red Knuckles on 2006-02-14
I went back over this thread yesterday and tried every suggestion to resolve my log in issue but was unable to do so. I then did a fresh install of Ubuntu and upon first boot I did the Ubuntu update. I then installed 'Automatix' and ran it selecting the updates and packages I wanted. Then I rebooted [entering password for Firestarter] and all went well/normal UNTIL I installed Spellbound dev in Firefox 1.5.0.1. I THEN got the error message:

Read and write permissions are needed for the following file:
/home/ben/.mozilla/firefox/imhm7ib.default/forecastfox/profiles.xml

So far I haven't found any problems caused by Automatix.

Will see if I can NOW learn how to get rid of that error message. Any advice/tips will be greatly appreciated.:cool:

---

### Post by Red Knuckles on 2006-02-14
[QUOTE=Red Knuckles]I went back over this thread yesterday and tried every suggestion to resolve my log in issue but was unable to do so. I then did a fresh install of Ubuntu and upon first boot I did the Ubuntu update. I then installed 'Automatix' and ran it selecting the updates and packages I wanted. Then I rebooted [entering password for Firestarter] and all went well/normal UNTIL I installed Spellbound dev in Firefox 1.5.0.1. I THEN got the error message:

Read and write permissions are needed for the following file:
/home/ben/.mozilla/firefox/imhm7ib.default/forecastfox/profiles.xml

So far I haven't found any problems caused by Automatix.

Will see if I can NOW learn how to get rid of that error message. Any advice/tips will be greatly appreciated.:cool:[/QUOTE]


Ok, I got rid of that error message by running the following 2 commands as sudo. When I ran them as regular user I got long lists of files ending in 'operation not permitted'. So I then ran them as sudo. It appeared to work and I closed/reopened Firefox with no error message!

The commands:

chown -R username.usergroup .mozilla/*

chmod -R 770 .mozilla/*

These commands came from the 2nd post in this thread by sbassett. I have learned a lot in the last 2 days.:-D

---

### Post by Zeroangel on 2006-02-14
Congratulations. You can also use gksudo nautilus to do those kinds of operations (change permissions, owner, edit files) as root.

---

### Post by Red Knuckles on 2006-02-14
[QUOTE=Zeroangel]Congratulations. You can also use gksudo nautilus to do those kinds of operations (change permissions, owner, edit files) as root.[/QUOTE]
Thanks for the Tip!

---

### Post by towsonu2003 on 2006-02-14
[QUOTE=Red Knuckles]
Read and write permissions are needed for the following file:
/home/ben/.mozilla/firefox/imhm7ib.default/forecastfox/profiles.xml

So far I haven't found any problems caused by Automatix.
[/QUOTE]
I'm glad you fixed it, although you had to reinstall. 

Now I am *truly speculating* as I have *no idea* what automatix uses to update firefox to 1.5.0.1. I assume from your problem that it launches firefox with root privileges to update it (a very popular approach to the update issue). During the update, firefox writes / changes some files in your /home/user/.mozilla/firefox/*.default profile (in your case, I think firefox tweaks forecastfox extension, rendering it "root owned"). As it changes these files, the new files become owned by root (who launched firefox to update as to the request of automatix). Thus, they cannot be accessed (for writing) by the normal user (you, who launch firefox after the update). 

This problem was also present in the FirefoxNewVersion wiki page, as we didn't predict this would happen (we: end users like you). I updated that section after seeing your post and your privilege and ownership problems.

---

