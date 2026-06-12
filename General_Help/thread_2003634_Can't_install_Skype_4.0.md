---
title: "Can't install Skype 4.0"
date: 2012-06-14
forum: General Help
---

### Post by bhishan on 2012-06-14
Skype 4.0 just got released recently. I uninstalled the older version and tried to install the new one. I downloaded it from the Skype website. Although I use Ubuntu 12.04 64 bit, I downloaded the one labeled for Ubuntu 10.04 64 bit because that was the only one available. This is the error I got one the terminal, on trying to install it. Help needed.

```
$ sudo dpkg -i skype4.deb
(Reading database ... 175218 files and directories currently installed.)
Unpacking skype (from skype4.deb) ...
dpkg: error processing skype4.deb (--install):
 trying to overwrite '/etc/dbus-1/system.d/skype.conf', which is also in package skype-bin:i386 2.2.0.35-0precise3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 skype4.deb

```

---

### Post by kanikilu on 2012-06-14
Did you "remove" or "purge" the old version? If remove, maybe it left some extraneous conf files around? I'm not sure if you can purge it at this point, so if not, you can either try deleting (or renaming/moving) that file manually, or just reinstall the old version, and then purge it.

```
sudo mv /etc/dbus-1/system.d/skype.conf /etc/dbus-1/system.d/skype.conf.old
```

or

```
sudo apt-get install skype; sudo apt-get purge skype
```

?

---

### Post by anmar on 2012-06-14
Same problem. Removing or renaming the offending file doesn't fix it sinc the debian packaging system is detecting that in the description of the package.

BTW, I can see skype-bin package installed but when I try to purge ut using

$ sudo dpkg --purge skype-bin 

It says that it can't find the package. Funny thing if I do

$ dpkg -l | grep skype

I see the skyp-bin package. 

Not sure what the heck is going on.

---

### Post by anmar on 2012-06-14
I just installed skype 4.0 on my laptop that had no previous versions of skype and it worked like a charm. No issues whatsoever.

---

### Post by IsraeliHawk on 2012-06-14
purging skype and "autoremove" did the trick for me.. 

installed and played with it - works nice.:guitar:

---

### Post by utherpendragonfly on 2012-06-14
I'm using Xubuntu 12.04. I just purged skype in the terminal. But the icon was still in the menu, so I checked with synaptic and skype:bin was still there. So I uninstalled that and now there's no sign of skype.
I double-clicked the skype-ubuntu 4.0.0.7-1amd-64.deb file I downloaded and it says it requires the installation of *168 packages!* Is this normal?

---

### Post by bhishan on 2012-06-14
In the terminal I entered ```
$ dpkg -l | grep skype
```
It showed two packages:
skype-bin:i386
python-skype

I purged them both using ```
$ sudo dpkg --purge skype-bin:i386
$ sudo dpkg --purge python-skype
```

And I tried installing it again, worked like a charm :)

---

### Post by anmar on 2012-06-14
Hmm.. Thanks hanikilu. Sounds like my desktop machine is acting funky :confused:. I will see if rebuilding the packages list will fix things.

---

### Post by sulliwane on 2012-06-15
Thanks bhishan,

#sudo dpkg --purge skype-bin:i386

made it !

:p

---

### Post by anmar on 2012-06-15
> **anmar said:**
> Hmm.. Thanks hanikilu. Sounds like my desktop machine is acting funky :confused:. I will see if rebuilding the packages list will fix things.

Ok. fixed it bu purging the package. Not sure what happened but all is well.
:guitar:

---

### Post by Call_M on 2012-06-26
Jup it worked. I should remember these commands.

Thank you!

---

### Post by tumutanzi.com on 2012-07-14
> **bhishan said:**
> In the terminal I entered ```
$ dpkg -l | grep skype
```
It showed two packages:
skype-bin:i386
python-skype

I purged them both using ```
$ sudo dpkg --purge skype-bin:i386
$ sudo dpkg --purge python-skype
```

And I tried installing it again, worked like a charm :)

On my computer, it gets the result as follows, so just use the right name:

ii  skype                                  2.2.0.35-0precise3                      VOIP and instant messaging client
pi  skype-bin                              2.2.0.35-0precise3                      VOIP and instant messaging client - binary files

---

### Post by rusell on 2012-07-19
> **bhishan said:**
> In the terminal I entered ```
$ dpkg -l | grep skype
```It showed two packages:
skype-bin:i386
python-skype

I purged them both using ```
$ sudo dpkg --purge skype-bin:i386
$ sudo dpkg --purge python-skype
```And I tried installing it again, worked like a charm :)

Thx Buddy! This also helped me! Seems like Skype has file conflicts with older versions, so it complains like this... Thx once again! ;) ):P

---

### Post by tazz4vr on 2012-08-03
Tried installing Skype from their website. My puter is Wubi with 12.04 and I tried installing the Ubuntu 10.04 64 bit, now receiving the following error message....  How do I report this bug?

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package skype needs to be reinstalled, but I can't find an archive for it.'

---

### Post by rockprincess on 2012-10-09
Hi guys,

I really need your help. It seems I've tried almost EVERYTHING....I have installed Skype a dozen times on my previous linux machines and never had such problems.
First I downloaded the .deb file from the official website, then it needed too many dependencies, and I thought "hey, there must be a repository for this...."
I then followed this advice, and added the repository.
[http://www.ubuntugeek.com/how-to-install-skype-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/how-to-install-skype-in-ubuntu-12-04precise.html)

Somehow it wouldn't install because "skype-bin" a virtual dependency couldn't be resolved.

I then read here in the forum to try

```
dpkg -l | grep skype
```

and then
```
sudo dpkg --purge skype-bin:i386
```

and then tried again installing it over
sudo apt-get install skype

But still it keeps saying that skype-bin can't be resolved.
I'm clueless. I don't know what else to do, to get it working :(

Please help!

---

