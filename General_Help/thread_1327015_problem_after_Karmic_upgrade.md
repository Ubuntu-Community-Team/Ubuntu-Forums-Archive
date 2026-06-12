---
title: "problem after Karmic upgrade"
date: 2009-11-15
forum: General Help
---

### Post by The-ITu on 2009-11-15
hi,
I have been ubun ubuntu 8.10 for quite a while now.
When jaunty came out, i gave it a try and after a week, it completely failed on me for no aparent reason. So i reformated my computer and re-insalled ubuntu. all my files where unrecoverable. 

not to long ago, my friend convinced me that Karmic was perfect for our laptops (we both have the same one) and that he had been using it for a while and that it was amazing. After a long time of arguing I finaly gave in and performed a double-upgreade.

now, ubuntu crashes every time the startup sound gets made. This might have been due to an installation problem, as the installation window closed its self radomly near the end of the instalation process. (the one **before** the cleanup process).

I was just wondering if there is a way this can be delt with, becuse I will be verry angry indeed if al my work was lost again, becuse i heavaly depended i ubuntu.

Thanks, The-IT

---

### Post by grandtoubab on 2009-11-15
Ensure all is up to date

in a terminal

check your list
```
sudo apt-get update
```

upgrade your packages
```
sudo apt-get upgrade
```

verify you do not miss new packages
```
sudo apt-get dist-upgrade
```

---

### Post by mick55 on 2009-11-15
hi The-IT

You can't directly upgrade from Ubuntu 8.10 to Ubuntu 9.10.

To upgrade from Ubuntu 8.10 to Ubuntu 9.10, 
you first have to upgrade to 9.04,
then upgrade 9.04 to 9.10.

I read the part about your problems with 9.04
so that doesn't appear to be an option for you.

My advice is to boot to the Live Cd and copy
all your documents and files to an
external USB drive or Network drive,
and then reformat and do a clean install.

I notice most Linux distros recommend a clean
install over an upgrade which is why I will
install the next LTS and play it safe
for the next 3 years.

Good Luck
mick

---

### Post by The-ITu on 2009-11-15
> **mick55 said:**
> hi The-IT

You can't directly upgrade from Ubuntu 8.10 to Ubuntu 9.10.

To upgrade from Ubuntu 8.10 to Ubuntu 9.10, 
you first have to upgrade to 9.04,
then upgrade 9.04 to 9.10.

I read the part about your problems with 9.04
so that doesn't appear to be an option for you.

My advice is to boot to the Live Cd and copy
all your documents and files to an
external USB drive or Network drive,
and then reformat and do a clean install.

I notice most Linux distros recommend a clean
install over an upgrade which is why I will
install the next LTS and play it safe
for the next 3 years.

Good Luck
mick
read the original post more carefuly next time.
i did upgreade to 9.04 and from there i upgreaded to karmic.

as for your post grandtoubab, 
I will try that from safe mode, becuse ubuntu does not start up properly.

---

### Post by grandtoubab on 2009-11-15
if it do not boot it could be also X problem

[I]restart your computer 
choose the ligne with recovery mode 
select boot with root 
when root prompt type the following 
 
X -configure 
cp /root/xorg.conf.new /etc/X11/xorg.conf 
reboot 			[/I]

---

### Post by J-Buntu on 2009-11-15
If all else fails, you might want to try burning the iso to disk at a slower speed if you try again from scratch. I burned mine to dvd at x2 speed.

It's just a thought. I know it doesn't help your current problem.

---

### Post by grandtoubab on 2009-11-15
> **The-ITu said:**
> 
as for your post grandtoubab, 
I will try that from safe mode, becuse ubuntu does not start up properly.

in this case recovery mode with root and internet connection, if root no need of sudo

---

### Post by mick55 on 2009-11-15
sigh..
> read the original post more carefuly next timeYeah, lets do that
> I have been ubun ubuntu 8.10 for quite a while nowDespite the mispelling  it seems to indicate you are using Ubuntu 8.10.

> When jaunty came out, i gave it a try and after a week, it completely failed on me for no aparent reason. So i reformated my computer and re-insalled ubuntuDespite the mispelling  it seems to indicate that you reinstalled 
Ubuntu 8.10 since Ubuntu 9.04 didn't work.You don't indicate which version
you reinstalled.

Look I was only trying to help, but the way you worded
your post was not clear.That being said, I still think a
clean install would work best for you.

I wish you luck
mick

---

### Post by The-ITu on 2009-11-16
> **mick55 said:**
> Despite the mispelling  it seems to indicate that you reinstalled 
Ubuntu 8.10 since Ubuntu 9.04 didn't work.You don't indicate which version
you reinstalled.

Look I was only trying to help, but the way you worded
your post was not clear.That being said, I still think a
clean install would work best for you.

I wish you luck
mick
ok im sorry for any confusion.

---

### Post by The-ITu on 2009-11-16
> **grandtoubab said:**
> Ensure all is up to date
check your list
```
sudo apt-get update
```upgrade your packages
```
sudo apt-get upgrade
```verify you do not miss new packages
```
sudo apt-get dist-upgrade
```
nope. did not work. conection error (yes, i did usen comand line with networking)

[quote=grandtoubab]X -configure 
cp /root/xorg.conf.new /etc/X11/xorg.conf 
reboot[/quote]
that did not work either. gave this error:
```
error: can not stat "/root/xorg.conf.new". no such file or directory.
```

thank you both for trying tho. Any help at all is greatly apretiated.

---

### Post by grandtoubab on 2009-11-16
> **The-ITu said:**
> nope. did not work. conection error (yes, i did usen comand line with networking)


that did not work either. gave this error:
```
error: can not stat "/root/xorg.conf.new". no such file or directory.
```thank you both for trying tho. Any help at all is greatly apretiated.

And what is the answer to the command you must have type before as root user
```
X -configure
```

---

### Post by The-ITu on 2009-11-16
I remember it gave me a long list of what *could* have been parameters. I typed it in corectly tho. It did not give any errors. I will try again just in case.

---

### Post by The-ITu on 2009-11-17
ok, i did that again, this time no errors.
did not help. so now we know its nothing to do with the xserver. right?

---

### Post by P4man on 2009-11-17
does ```
uname -a
``` return the correct kernel version (ie 2.6.31-xx) ?

---

### Post by The-ITu on 2009-11-17
how do i know wich one is the correct one?

---

### Post by P4man on 2009-11-17
If its 2.6.31-xx then its correct. If its 2.6.28-xx then you're still booting the jaunty kernel (caused by a bug in the updater)

---

### Post by The-ITu on 2009-11-17
ok, i have got work that is due tommorow. 
can some one please post code on how to copy a directory onto a USB flash card (the directory containes spaces).

---

### Post by gordonh on 2009-11-17
> **The-ITu said:**
> ok, i have got work that is due tommorow. 
can some one please post code on how to copy a directory onto a USB flash card (the directory containes spaces).

You have to "Escape" the spaces ie escape\ the\ spaces in the cp command

Good luck

---

### Post by The-ITu on 2009-11-18
sorry, what i meant was that the directory *name* contains spaces. eg, /home/username/Documents/folder** **name/stuff

---

### Post by mick55 on 2009-11-18
You can drag and drop just like you can in Windows.

This is assuming you have a GUI.
You didn't say.

---

### Post by The-ITu on 2009-11-18
i can't boot up, remember?

---

### Post by mick55 on 2009-11-18
You can use a Live Cd.

I won't bother you again with my suggestions, since
they seem to irritate you.

Good Bye

---

### Post by The-ITu on 2009-11-18
No wait. don't be that way. Any help is apretiated and its partialy my fault as well.
I don't have a live CD coz i sister snaped it, and i might not be able to obtain one for a while.

---

### Post by mick55 on 2009-11-18
No problem.

Any Linux Live Cd will work.Even a small Distro like
Puppy Linux will give you a desktop and the ability to mount drives
and copy files and access the internet.

Of course if you don't have access to another PC to download and
burn the CD, then obviously this option won't work.

Are you familiar with Distrowatch?
They have many Distros and rescue Cd's.Perhaps one of
them could assist you in your endeavour.
[html]http://distrowatch.com/[/html]I hope you can resolve the problem, good luck.

---

### Post by The-ITu on 2009-11-19
thank you. 
I will get to doing that soon.

---

