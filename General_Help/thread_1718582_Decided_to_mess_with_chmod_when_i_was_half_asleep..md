---
title: "Decided to mess with chmod when i was half asleep... Help?"
date: 2011-03-31
forum: General Help
---

### Post by Kitkin15 on 2011-03-31
I was halfway asleep in school, so i got bored and was learning about chmod. I ended up typing "sudo chmod 777 -R /etc"

Yes, i AM that stupid. Now i need to learn how to make my sudo folder back how it was (0445 i think) Im not able to type "sudo" anymore, so how do i fix this? I have Ubuntu installed on my EXT HDD if that makes any difference. I just got Ubuntu set up exactly how i want it (Took two weeks) so i really dont want to reinstall it and do all the work over again.

Can anyone help? I googled but the information i got wasnt very helpful.\


Thanks

  -Kitkin15

---

### Post by HermanAB on 2011-03-31
Re-install. Sorry.

Enjoy your nice, clean, fresh system.

---

### Post by brakos on 2011-03-31
Yep, I did /usr/bin once.... that was interesting.

---

### Post by Kitkin15 on 2011-03-31
"sudo: /etc/sudoers is mode 0755, should be 0440
sudo: no valid sudoers sources found, quitting"

Thats the exact error. I saw that someone did fix it, but the way they did it was by typing in "su" Then entering the password and then re-chmoding it. But when i type in "su" And type in my password it tells me its incorrect (I only have one password on my system, and thats the one i used)

Are you sure ill have to reinstall? Damn i feel really stupid now :( Took forever to get everything set up lol

---

### Post by Kitkin15 on 2011-03-31
[http://crunchbanglinux.org/forums/topic/2402/need-fast-help-i-messed-up-sudoers-now-sudo-does-not-work/](http://crunchbanglinux.org/forums/topic/2402/need-fast-help-i-messed-up-sudoers-now-sudo-does-not-work/)

Im going to try this but i really doubt it will work....... My EXT HDD is partitioned and i cant see the files. But i guess its better then not trying at all....

---

### Post by Sina_RJ on 2011-03-31
use rootsh maybe that'll be helpful
in that way you won't need any sudoer ;)
it's just a try!
i don't have any idea how it'll work


EDIT: i mean get access to root somehow :)

---

### Post by nothingspecial on 2011-03-31
> **Kitkin15 said:**
> 

Are you sure ill have to reinstall? 

Yep, you've toasted it.

In theory it's possible but it'd be easier to reinstall.

---

### Post by matt_symes on 2011-03-31
Hi

Why did  you do that ? That is really not very clever.

/etc/sudoers needs to be (From a LiveCD/USB) after mounting

```
sudo chmod 440 <mount_point>/etc/sudoers
```

Kind regards

---

### Post by Sina_RJ on 2011-03-31
> **matt_symes said:**
> 
```
sudo chmod 440 <mount_point>/etc/sudoers
```


He says sudoers doesn't work at all!!
all the things happen after sudo and password is just an err

---

### Post by matt_symes on 2011-03-31
Hi

> **Sina_RJ said:**
> He says sudoers doesn't work at all!!
all the things happen after sudo and password is just an err

That is why i said LiveCD/USB. Of course it can also be done  from the root console but after that chmod i would suggest the OP keep well away from any root console.

Kind regards

---

### Post by Kitkin15 on 2011-03-31
Yes i thought of doing 
sudo chmod 440 <mount_point>/etc/sudoersBut its being a pain. Ive been at it for about 30 minutes now...... And its not working.

Do you guys know how i can erase the partition i put on my EXT HDD that had Ubuntu on it? I want to use that space. What programs can do that?

---

### Post by matt_symes on 2011-03-31
Hi

> **Kitkin15 said:**
> Yes i thought of doing 
sudo chmod 440 <mount_point>/etc/sudoersBut its being a pain. Ive been at it for about 30 minutes now...... And its not working.

Do you guys know how i can erase the partition i put on my EXT HDD that had Ubuntu on it? I want to use that space. What programs can do that?

Do you want me to teach you how to fix your sudoers file from a LiveCD/USB and attempt to fix your /etc folder or do you want to reinstall Ubuntu on your Ubuntu partition and start again  ? What do you want to do with the partition ?

For both you will need a LiveCD/USB. I would go for the latter.

**EDIT: On second thoughts you have been a bit of a burk (no offence intended). I don't want to spend ages on this thread. Follow the advice of others in this thread. Backup and resinstall.**

Kind regards

---

### Post by Kitkin15 on 2011-03-31
> **matt_symes said:**
> Hi



Do you want me to teach you how to fix your sudoers file from a LiveCD/USB and attempt to fix your /etc folder or do you want to reinstall Ubuntu on your Ubuntu partition and start again  ? What do you want to do with the partition ?

For both you will need a LiveCD/USB. I would go for the latter.

**EDIT: On second thoughts you have been a bit of a burk (no offence intended). I don't want to spend ages on this thread. Follow the advice of others in this thread. Backup and resinstall.**

Kind regards

I would like if you could help me fix it, i put to much work into it to lose it.

So i typed in this command:
sudo chmod 440 "/media/238e38a6-e377-4e09-92f6-4ac48054207f/etc/sudoers"

"238e38a6-e377-4e09-92f6-4ac48054207f" Is the name of my Ubuntu partition on my EXT HDD (This was all in live CD)
It worked, sort of.... Now im getting:
"sudo: can't open /etc/sudoers.d/README: Permission denied"

So what should my next code be?
I so far have these codes lined up and i think they might work, but not sure.

"sudo chmod 777 "/media/238e38a6-e377-4e09-92f6-4ac48054207f/etc/sudoers.d"
sudo chmod 777 -R "/media/238e38a6-e377-4e09-92f6-4ac48054207f/etc/sudoers.d"
sudo chmod 440 "/media/238e38a6-e377-4e09-92f6-4ac48054207f/etc/sudoers.d/README"
sudo chmod 440 "/media/238e38a6-e377-4e09-92f6-4ac48054207f/etc/sudoers"
To do all of those one after the other. If you know one thats better please do let me know.

Sorry that ive been a "bunk" I was busy trying to fix it, ive been trying for at least 2 and a half hours. I would really like it if you could help me here. I will stay on and follow all your instructions if youll help me.

---

### Post by coffeecat on 2011-03-31
I'm going to go with the majority here. You need to re-install. To give you a glimpse  of the herculean size of the task you would have re-assigning all the correct permissions in /etc, just look at this fragment of the output of 'ls -l /etc' from my system:

```
lrwxrwxrwx  1 root    root        22 2011-03-17 20:52 printcap -> /var/run/cups/printcap
-rw-r--r--  1 root    root       497 2011-02-25 17:38 profile
-rw-r--r--  1 root    root      2859 2011-02-18 14:36 protocols
-rwxr-xr-x  1 root    root       306 2010-12-06 20:43 rc.local
-rw-r--r--  1 root    root      1586 2011-02-20 02:26 request-key.conf
-rw-r--r--  1 root    root       123 2011-03-31 19:09 resolv.conf
-rwxr-xr-x  1 root    root       268 2010-11-13 14:45 rmt
-rw-r--r--  1 root    root       887 2010-11-08 11:32 rpc
-rw-r--r--  1 root    root      1195 2010-11-19 17:51 rsyslog.conf
-rw-r--r--  1 root    root      3828 2011-02-21 00:18 securetty
-rw-r--r--  1 root    root      9320 2011-02-15 19:56 sensors3.conf
-rw-r--r--  1 root    root     19666 2011-02-18 14:36 services
-rw-r-----  1 root    shadow    1036 2011-02-26 08:50 shadow
-rw-------  1 root    root      1036 2011-02-26 08:50 shadow-
-rw-r--r--  1 root    root       165 2010-12-06 20:43 shells
-r--r-----  1 root    root       574 2011-03-25 21:37 sudoers
-r--r-----  1 root    root       574 2010-12-16 00:02 sudoers.dpkg-dist
-rw-r--r--  1 root    root      2083 2010-12-21 09:56 sysctl.conf
-rw-r--r--  1 root    root        14 2011-03-16 23:11 timezone
-rw-r--r--  1 root    root       645 2010-03-07 05:58 ts.conf
-rw-r--r--  1 root    root      1260 2008-05-30 07:22 ucf.conf
-rw-r--r--  1 root    root       310 2010-10-15 02:02 updatedb.conf
-rw-r--r--  1 root    root       592 2011-02-01 14:23 usb_modeswitch.conf
lrwxrwxrwx  1 root    root        23 2011-03-21 13:40 vtrgb -> /etc/alternatives/vtrgb

```And that's just a few files, not all the folders and their contents. Look at the medley of differing permissions.

> **Kitkin15 said:**
>  ive been trying for at least 2 and a half hours. 

It will take you about 40 minutes to re-install **and** update if you have broadband.

---

### Post by Kitkin15 on 2011-03-31
> **coffeecat said:**
> I'm going to go with the majority here. You need to re-install. To give you a glimpse  of the herculean size of the task you would have re-assigning all the correct permissions in /etc, just look at this fragment of the output of 'ls -l /etc' from my system:

```
lrwxrwxrwx  1 root    root        22 2011-03-17 20:52 printcap -> /var/run/cups/printcap
-rw-r--r--  1 root    root       497 2011-02-25 17:38 profile
-rw-r--r--  1 root    root      2859 2011-02-18 14:36 protocols
-rwxr-xr-x  1 root    root       306 2010-12-06 20:43 rc.local
-rw-r--r--  1 root    root      1586 2011-02-20 02:26 request-key.conf
-rw-r--r--  1 root    root       123 2011-03-31 19:09 resolv.conf
-rwxr-xr-x  1 root    root       268 2010-11-13 14:45 rmt
-rw-r--r--  1 root    root       887 2010-11-08 11:32 rpc
-rw-r--r--  1 root    root      1195 2010-11-19 17:51 rsyslog.conf
-rw-r--r--  1 root    root      3828 2011-02-21 00:18 securetty
-rw-r--r--  1 root    root      9320 2011-02-15 19:56 sensors3.conf
-rw-r--r--  1 root    root     19666 2011-02-18 14:36 services
-rw-r-----  1 root    shadow    1036 2011-02-26 08:50 shadow
-rw-------  1 root    root      1036 2011-02-26 08:50 shadow-
-rw-r--r--  1 root    root       165 2010-12-06 20:43 shells
-r--r-----  1 root    root       574 2011-03-25 21:37 sudoers
-r--r-----  1 root    root       574 2010-12-16 00:02 sudoers.dpkg-dist
-rw-r--r--  1 root    root      2083 2010-12-21 09:56 sysctl.conf
-rw-r--r--  1 root    root        14 2011-03-16 23:11 timezone
-rw-r--r--  1 root    root       645 2010-03-07 05:58 ts.conf
-rw-r--r--  1 root    root      1260 2008-05-30 07:22 ucf.conf
-rw-r--r--  1 root    root       310 2010-10-15 02:02 updatedb.conf
-rw-r--r--  1 root    root       592 2011-02-01 14:23 usb_modeswitch.conf
lrwxrwxrwx  1 root    root        23 2011-03-21 13:40 vtrgb -> /etc/alternatives/vtrgb

```And that's just a few files, not all the folders and their contents. Look at the medley of differing permissions.



It will take you about 40 minutes to re-install **and** update if you have broadband.
Can you tell me how to overwrite my partition then? I need to get rid of my current partition in order to get room for the new one.

---

### Post by matt_symes on 2011-03-31
**Backup and Reinstall**

It will take too long otherwise and even then there are no guarantees.

Next time try not to get bored.

---

### Post by coffeecat on 2011-03-31
> **Kitkin15 said:**
> Can you tell me how to overwrite my partition then? I need to get rid of my current partition in order to get room for the new one.

Use the manual/advanced option at the partitioning stage of the installer. Simply designate your old root partition as '/' for the new install, choose your filesystem and mark the reformat tickbox. If there are any other partitions you want automounted in the new system, you can designate them at the same stage. Don't bother with the swap partition - the installer will detect that automatically.

---

### Post by matt_symes on 2011-03-31
Hi

> Can you tell me how to overwrite my partition then? I need to get rid of my current partition in order to get room for the new one.

It's not your current partition you need to get rid of, it's  the operating system in that partition.

You can use your existing partition and just install into it.

Backup first, backup first, backup first any files you want to keep.

A partition is just an area on the hard drive. You can install, reinstall or overwrite that partition with whatever you want.

What do you want to install there ?

If Ubuntu then when reinstalling you will need to select the manual partition option.

Kind regards

---

### Post by Kitkin15 on 2011-03-31
Yes before i did anything i backed up all my files that i needed, so i have that done. Thats always #1 to me.

When i went to install it it only gave me the options to install side by side (Which i dont want) Or the advanced which is to do it all myself, but then that fills the whole EXT HDD with Ubuntu, which is definitely not what i want.

---

### Post by coffeecat on 2011-03-31
> **Kitkin15 said:**
> Or the advanced which is to do it all myself, but then that fills the whole EXT HDD with Ubuntu, which is definitely not what i want.

No it doesn't. Look again. The manual/advanced option will show you all the partitions on the drive. Simply highlight the one you want to install to and choose "edit" or "change" or something or other, and then you can do what I've already explained. Then repeat for any partitions you want mounted to special mount points (if any).

---

### Post by Kitkin15 on 2011-03-31
> **coffeecat said:**
> No it doesn't. Look again. The manual/advanced option will show you all the partitions on the drive. Simply highlight the one you want to install to and choose "edit" or "change" or something or other, and then you can do what I've already explained. Then repeat for any partitions you want mounted to special mount points (if any).

Ok ill try it again in one minute.

Thanks so much for the help guys, ill let you know how it goes :)

---

### Post by Kitkin15 on 2011-03-31
Ok you were right, it went perfectly :) Now all i have to do is install all my programs again lol.

Thanks so much for the help guys, i really do appreciate it.

  -Kitkin15

---

### Post by mtc11 on 2011-04-26
hie

I am facing the same problem of not being able to boot Ubuntu. I am however able to boot from LIVE CD on USB but cannot change the permissions of /etc/sudoers file. when trying to do any sudo it says 
sudo: /etc/sudoers is mode 0755, should be 0440
sudo: no valid sudoers sources found, quitting.


I believe there should be a solution of being able to change the permissions of the file without reinstalling the OS.

---

### Post by Dave_L on 2011-04-26
You can easily change the permissions of a file by booting from a Live CD or Live USB drive.

The original poster's problem was restoring the correct permissions of all the files in /etc, which is much more complicated.

---

### Post by tgm4883 on 2011-04-26
> **mtc11 said:**
> hie

I am facing the same problem of not being able to boot Ubuntu. I am however able to boot from LIVE CD on USB but cannot change the permissions of /etc/sudoers file. when trying to do any sudo it says 
sudo: /etc/sudoers is mode 0755, should be 0440
sudo: no valid sudoers sources found, quitting.


I believe there should be a solution of being able to change the permissions of the file without reinstalling the OS.

You can change the file permissions without reinstalling the OS, but the sheer amount of work involved doesn't make it a method most people want to take.

However, if you really want to do it.

1) Boot into recovery console
2) Boot up a working machine
3) Compare the permissions of EVERY file on the working machine to that of the broken machine. Fix where necessary.

Or just reinstall the OS.

---

