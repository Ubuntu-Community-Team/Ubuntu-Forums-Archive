---
title: "ubuntu wont start up!!"
date: 2009-07-22
forum: General Help
---

### Post by The-ITu on 2009-07-22
hey ubuntu forum readers!

I have a prblem, and this time im not *as* much of a noob as before so I can help you help me better.
I think it has something to do Jaunty. any way.
my file system is ext4.
im runing ubuntu 9.04 (last updated 19/7)
the problem has got worse now. it wont even let me log on any more. after i type in my user name a pass word the log on screen gos away and nothing hapends.

I have a question tho, is there a way i could use my ubuntu 8.10 (it does not use ext4) CD to *down*grade back to 8.10 without harming my files?
a detales tutorial would be apreitiated.

apolagies for bad spelling,
I will bump if needed,
thanks to all who have and will help me.
  ________
_|-The-ITu-|_

---

### Post by Cheesemill on 2009-07-22
It is not possible to downgrade a Ubuntu installation, especially as 8.10 doesn't recognise ext4.
If you want 8.10 back on your machine you will need to reinstall from scratch.
First you would need to boot up with a 9.04 Live CD to recover the data from your existing partitions as you will have to reformat your drive to install 8.10.

If you can give more details about your problems with Jaunty we may be able to help you fix them.

---

### Post by The-ITu on 2009-07-22
> **Cheesemill said:**
> It is not possible to downgrade a Ubuntu installation, especially as 8.10 doesn't recognise ext4.
If you want 8.10 back on your machine you will need to reinstall from scratch.
First you would need to boot up with a 9.04 Live CD to recover the data from your existing partitions as you will have to reformat your drive to install 8.10.

If you can give more details about your problems with Jaunty we may be able to help you fix them.
well, now all i know is that downgreading is not an option. I don't have a 9.04 cd, and there is no way I gonna give up those file in there!
looks like (with the correct help) im gonna have a tacle this problem head on!!!
thanks for the help anyway.

---

### Post by Meson on 2009-07-22
It could have something to do with the files and/or permissions of your home directory. Have you tried booting into recovery mode? When the computer is booting the grub menu should list it for you.

Once there you should be able to do something like this and see the following:
```
~$ ls -al /home
total 36
drwxr-xr-x  9 root     root   4096 2009-07-08 20:31 .
drwxr-xr-x 20 root     root   4096 2009-07-15 18:43 ..
drwx------ 66 matt     matt   4096 2009-07-22 08:03 matt
drwxrwx--- 23 mike     matt   4096 2009-07-18 21:44 mike
```

Notice that all users have r/w/x on their home folders. Also notice that /home itself (listed as .) has at least r/x for everyone.

If your permissions are fine you can try doing something (still from recovery mode) like:
```
mv /home/username /home/username.bak
mkdir /home/username
chown username:username /home/username
chmod u=rwx,go= /home/username
```
(Note that because you are in recovery mode here, you don't need to use sudo for these commands)

Once you've done this, type "exit" and you should be able to resume a normal boot. Your home directory will be rebuilt and your files will be safely backed up.

---

### Post by The-ITu on 2009-07-23
[quote=Meson] Have you tried booting into recovery mode?[/quote] yes I have.
[quote=Meson]It could have something to do with the files and/or permissions of your home directory[/quote] I don't think so.
I think it is becuse the X Server has some sort of problem.
 
last question:
you said that after I make those changes all my files will be backed up.
where would they be backed up?

---

### Post by The-ITu on 2009-07-23
> **Meson said:**
> If your permissions are fine you can try doing something (still from recovery mode) like:
```
mv /home/username /home/username.bak
mkdir /home/username
chown username:username /home/username
chmod u=rwx,go= /home/username
```
(Note that because you are in recovery mode here, you don't need to use sudo for these commands)
 
Once you've done this, type "exit" and you should be able to resume a normal boot. Your home directory will be rebuilt and your files will be safely backed up.
Thanks for trying, however, It did njot work :(
I tryed to log on after doing so and it just gave me an error (what I found interesting about this error is that it was in the KDE GUI. I have KDE installed but I never use it becuse it does not seam like it wants to pick up the keybord). the error want **something** like this: [quote=error]cannot goto directory with './'[/quote] or something like that. and The same thing hapend as before; it did not log me on.
 
i doubt the problem is with permissions.
thanks for trying tho :)

---

### Post by Meson on 2009-07-23
Well, it could have something to do with the permissions on .Xauthority (but I guess not if you tried starting with a fresh home directory)

You could try from recovery mode:
```
dpkg-reconfigure xserver-xorg
```

Also, if you could post some actual error messages it would help. (There should be an Xorg.0.log)

---

### Post by The-ITu on 2009-07-23
> **Meson said:**
> Well, it could have something to do with the permissions on .Xauthority (but I guess not if you tried starting with a fresh home directory)
 
You could try from recovery mode:
```
dpkg-reconfigure xserver-xorg
```
 
Also, if you could post some actual error messages it would help. (There should be an Xorg.0.log)
thanks il try that line now.
If the error comes again, il write it down.
I can't get into the log file if I can't even boot.
unless you tell me where its located. then i could veiw it on safe mode.
still... thanks for all the help.

---

### Post by The-ITu on 2009-07-24
still no luck :(
i wrote down this new error; this is exactly what it said:
[quote=error]connot enter home directory. using /.[/quote]
reconfiguring the xserver didn't really help eather.

---

### Post by UncleMike on 2009-07-24
UncleMike here, new to your forum.
I installed 9.04 over 7.10 and all it did was try to run but it ab-ended with each attempt to load. now trying to reinstall 7.10 and not getting anywhere. any ideas?
running on a Dell lattitude, 7.10 ran just fine but did not have the ease of using a data card for my net connect, without a bunch of behind the seine fiddling.:confused:

[IMG]http://www.harges.net/emoticons/oldman.gif[/IMG]UncleMike

---

### Post by Meson on 2009-07-24
> **The-ITu said:**
> still no luck :(
i wrote down this new error; this is exactly what it said:

reconfiguring the xserver didn't really help eather.

Hmm, does anyone know if this means X11 thinks that / is his home directory? The-ITu, can you verify that your home directory is /home/username in the file /etc/passwd?
```
grep $USER /etc/passwd
```

---

### Post by Meson on 2009-07-24
> **UncleMike said:**
> UncleMike here, new to your forum.
I installed 9.04 over 7.10 and all it did was try to run but it ab-ended with each attempt to load. now trying to reinstall 7.10 and not getting anywhere. any ideas?
running on a Dell lattitude, 7.10 ran just fine but did not have the ease of using a data card for my net connect, without a bunch of behind the seine fiddling.:confused:

[IMG]http://www.harges.net/emoticons/oldman.gif[/IMG]UncleMike

This isn't related to the original post.

---

### Post by UncleMike on 2009-07-24
sorry where can I find an install thread, have done a cursory search and seemed to be overwhelmed with install problems.

[img]http://www.harges.net/emoticons/oldman.gif[/img]UncleMike

---

### Post by Meson on 2009-07-24
To be honest I had trouble even making out what your problem is from what you wrote above. Just start your own thread =)  Try to be clear and specific.

---

### Post by The-ITu on 2009-07-24
> **Meson said:**
> Hmm, does anyone know if this means X11 thinks that / is his home directory? The-ITu, can you verify that your home directory is /home/username in the file /etc/passwd?
```
grep $USER /etc/passwd
```
my home directory should be under /home/username, thats where it was back when ubuntu actualy used to work...
but I don't exactly know what you mean by my home directory being in the file /etc/password.
il run the command and tell you what it returnes.

---

### Post by The-ITu on 2009-07-24
ok I tryed that and here is how that went:
```
root@ubuntu:~# grep $USER /etc/password
grep: /etc/password: No such file or directory.
root@ubuntu:~# grep $TheIT /etc/password
_
```
and the it did absolutly nothing.
I waited for about 5 mins, still nothing.
do I have to wait longer? what was that **supposed** to do?

---

### Post by DeMus on 2009-07-24
> **The-ITu said:**
> hey ubuntu forum readers!

I have a prblem, and this time im not *as* much of a noob as before so I can help you help me better.
I think it has something to do Jaunty. any way.
my file system is ext4.
im runing ubuntu 9.04 (last updated 19/7)
the problem has got worse now. it wont even let me log on any more. after i type in my user name a pass word the log on screen gos away and nothing hapends.

I have a question tho, is there a way i could use my ubuntu 8.10 (it does not use ext4) CD to *down*grade back to 8.10 without harming my files?
a detales tutorial would be apreitiated.

apolagies for bad spelling,
I will bump if needed,
thanks to all who have and will help me.
  ________
_|-The-ITu-|_

Could it be that the drive /home is filled up? In other words, is it possible the system has no free space to write to?

---

### Post by The-ITu on 2009-07-25
> **DeMus said:**
> Could it be that the drive /home is filled up? In other words, is it possible the system has no free space to write to?
no I don't think so becuse last time I checked i had 17 gigs left on my ubuntu partition.
 
on another note, Meason, could you please tell my what I did you my home folder, becuse i went into safe mode to put my python file on a memory stick so I could wor on some projects but there was nothing there when i types in 'ls'.
how can I get it back?

---

### Post by Meson on 2009-07-25
You typed the command wrong before, the file it's passwd (just 'wd', not 'word') So:
```
grep $USER /etc/passwd
```

DeMus had a good suggestion too. Try posting the output of ```
df -h
``` You may have done something like let your trash bin fill up. (An honest mistake, I've seen people do it before.) When your disk runs out of space, there are usually problems logging in to X.

As far as your home directory goes, I just suggested you move it. To move it back:
```
sudo mv /home/username /home/username.bak2
sudo mv /home/username.bak /home/username
```

---

### Post by The-ITu on 2009-07-26
> **Meson said:**
> Try posting the output of      Code:
     df -h 

ok here:
```
        276    8.2g    18g      %33    /
tmps          987m      0    987m   %0      /lib/int/rw
varrun        987m  12k    987m   %1      /var/run
varlock       987m     0    987m   %0      /var/lock
udevtmpfs     987m  14BK  987m   %1      /dev
/dev/sda1      987m     0    987m   %0      /dev/shm
lrm             107g  52g    55g      %49    /host
ile              987m 2.4m   95m     %1     /lib/modules/2.6.28-11-generic/volat
```[quote=Meson]
             **Re: ubuntu wont start up!!**
         You typed the command wrong before, the file it's passwd (just 'wd', not 'word') So:
     Code:
     grep $USER /etc/passwd 

that did nothing.
just like last time when i spelt it worng.

---

### Post by Meson on 2009-07-26
I'm not sure what that /dev/shm mount point you have is, but it's full.

As far as "grep $USER /etc/passwd" not returning anything, that is bad.

---

### Post by The-ITu on 2009-07-27
its not that it did not return anything, its that it did **nothing**.
it did not ask me to put in another command like after the previos one had finished.
mabe i did not wait long enough.

what do you suggest? or else, is there any one more experienced (not that im saying your not its just that im desprite now :( ) I could talk to?

thanks for ***all*** your help any way :)

---

### Post by Meson on 2009-07-28
```
~$ grep $USER /etc/passwd
matt:x:1000:1000:,,,:**/home/matt**:/bin/bash
~$
```

The text in bold is my home directory, if it isn't set properly it will mean bad things for me. The fact that the command isn't displaying ANYTHING is troublesome. Is your user account set up on an LDAP or something? To elaborate: is this a stand-alone system or is it hooked up to some server for things like user accounts and shared files?

---

