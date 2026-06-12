---
title: "Broken 'flasplugin-nonfree'"
date: 2010-05-01
forum: General Help
---

### Post by John Z on 2010-05-01
'flashplugin-nonfree' is labeled as broken, and has been since I upgraded to 10.04.

Flash still seems to work fine, but when I try and run an update I get this message:

> E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.
I cannot remove or reinstall the file, and I have tried the methods suggested in similar threads on this forum.

---

### Post by clhsharky on 2010-05-01
HI

```
 sudo apt-get autoclean
 sudo apt-get autoremove 
 sudo apt-get remove --purge flashplugin-nonfree
```

That will remove flash plugin

reinstall with

```
 sudo apt-get install flashplugig-installer
```

Sharky

---

### Post by John Z on 2010-05-01
Tried your method of removing it. I got this error:

> dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by brawd on 2010-05-01
Hi there, I hope you don't mind me joining with my little error.

I tried the above commands and got as far as removing the flash plug in, then I got this,

Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help is appreciated.

regards,

brawd.

---

### Post by clhsharky on 2010-05-01
HI 

Have you tried to fix broken packages in synapic package manager?
Its under custom filters.

Sharky

> sudo apt-get -f install flashplugin-nonfree

will try to fix broken package

---

### Post by brawd on 2010-05-01
Just tried the fix broken package using synaptic but got the same message:-

E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

---

### Post by brawd on 2010-05-01
Synaptic only offers me a couple of options and all of them return the same error as above

---

### Post by clhsharky on 2010-05-01
HI

> Quote:
sudo apt-get -f install flashplugin-nonfree
will try to fix broken package

What did that return?

Sharky

---

### Post by brawd on 2010-05-01
I just noticed the bug report splash at the top of the screen. The info it collected is

package flashplugin-nonfree 10.0.1.218 really9.0.262.0ubuntu1 failed to install/upgrade: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

But being as it's as bad as it is it won't let me reinstall.
Arrgghh!!

regards,

brawd.

---

### Post by clhsharky on 2010-05-01
HI

Well I have gone in and remove the file to start over with flash install.
Its not hard . Up to you.

Sharky

---

### Post by John Z on 2010-05-01
Identical results for me. It won't let me reinstall or remove it.

---

### Post by clhsharky on 2010-05-01
HI

To manuly delete.

```
gksudo nautilus
```
Give password .

Navagate to 'file system/usr/lib/flashplugin-installer'.

Right click, move to trash.

Its gone, close windows.

Follow previous instructions to install.
> sudo apt-get autoclean
sudo apt-get -f install flashplugin-nonfree

Sharky

I like to use nautilus so I can see what I remove and can also able to put it back if need to, that just me though.

---

### Post by rnerwein on 2010-05-01
hi
i am running lucid lynx 2.6.32-21-generic  
and did an upgrade/update 30.04.2010.#32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

my firefox version is: Mozilla Firefox 3.6.3, Copyright (c) 1998 - 2010 mozilla.org.
i did:  ( but remember i am running a 64 bit system )
cd ~/tmp
stop firefox 
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)
tar xvf libflashplayer-10.0.45.2.linux-x86_64.so.tar
cksum ibflashplayer.so   ---> 4141789390 9570824
sudo cp ibflashplayer.so  /usr/lib/mozilla/plugins/libflashplayer.so
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so

restart firefox
--> works as a charme  :-)
ciao

---

### Post by brawd on 2010-05-01
Well..

Sorry to say but I took the wimp's option.
I downloaded the install iso first and wrote the CD.
I used Hiren Killdisk to wipe the HDD and installed 10.04.

On the positive side my HDD probably needed a good washout because now it's running faster. Lord alone knows why that is.

Thanks for your help though, and as ever in these situations, I learned a little more.

regards,

brawd.

---

### Post by John Z on 2010-05-01
I don't think I'll give up quite yet. I tried your latest suggestion sharky.

I moved the file to the trash, it disappeared but isn't in my trash. I also got an error message in the terminal.

I the did the autoclean/reinstall cmds and I got this error:

> You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
After following its suggestion and running '-f install' I get this error:

> dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by John Z on 2010-05-01
Also, Merwein, I don't think that will fix my problem. I have flash installed, and it seems to work perfectly. 

My problem is with a broken package that is preventing me from doing any updates.

---

### Post by John Z on 2010-05-01
I fixed the issue. For those curious I ended up using:

```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree
```Thanks for all the help.

---

### Post by 7G Operator on 2010-05-03
Cheers John that did the trick, i was wandering around in the dpkg sorta area (as thats where the error message pertains to) but i didnt know exactly which file to edit. Cheers =). - Dan

---

### Post by denizs on 2010-05-06
Thanks for all the info. I was having the same problems and it s fixed thanks to previous notes by all:
 In summary I did;
       sudo  rm /var/lib/dpkg/info/flashplugin-nonfree.prerm        
sudo dpkg --remove --force-remove-reinstreq flushplugin-nonfree
        sudo dpkg  --purge --force-remove-reinstreq flushplugin-nonfree
        sudo apt-get autoclean
       sudo apt-get autoremove
        sudo apt-get remove --purge flashplugin-nonfree
       sudo  apt-get -f install flashplugin-nonfree

---

### Post by cotsweb on 2010-05-06
> **John Z said:**
> I fixed the issue. For those curious I ended up using:

```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree
```Thanks for all the help.

Thanks John, that sorted it out for me, I then did

```

sudo apt-get -f install flashplugin-nonfree 

```

to get the pluging installed properly, all looks fine now.

Mark

---

### Post by alcyst on 2010-05-06
Tried lots of things here, i.e.;

XXXXXXX:~$ sudo apt-get -f install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
XXXXXX:~$ ^C
XXXXXX:~$ sudo apt-get -f install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

still no working flash

---

