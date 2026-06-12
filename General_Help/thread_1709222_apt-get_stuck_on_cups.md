---
title: "apt-get stuck on cups"
date: 2011-03-17
forum: General Help
---

### Post by plunksnakotis on 2011-03-17
Hello everyone one more time ! :) When I tried to remove cups printing service I have faced with such problem. I typed :

```
apt-get remove cups
```
It just stuck at removing it and nothing happened for a long time so I canceled it ... If I type apt-get remove cups one more time such error pops up : 
```

root@kamp:~# apt-get remove cups
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@kamp:~# dpkg --configure -a
dpkg: error processing cups (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 cups

```

I have tried :

```

root@kamp:~# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```
Nothing changed .......

```

root@kamp:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,914kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 152313 files and directories currently installed.)
Preparing to replace cups 1.4.4-6ubuntu2 (using .../cups_1.4.4-6ubuntu2_i386.deb) ...


```And this hangs for unlimited time !! Whats wrong ? I don't know how to solve this, anyone can help me ? If I cancel this procedure apt-get hangs ........  FOR EXAMPLE :

```

root@kamp:~# apt-get install gedit
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```So ........ I have to manually kill it .... like : 
```

root@kamp:~# ps -ax | grep apt
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
15704 pts/2    T      0:00 apt-get autoremove
16197 pts/2    S+     0:00 grep --color=auto apt-get
15729 ?        Ss     0:00 /usr/bin/dpkg --status-fd 24 --unpack --auto-deconfigure /var/cache/apt/archives/cups_1.4.4-6ubuntu2_i386.deb

``````

kill -9 15704

```after that I tried many different things ,but I can't understand why it is so ..... Please help anyone  !:) Thank you in advance !

---

### Post by 5149.5 on 2011-03-17
CUPS is common unix printing system and is used by everything. I would try a reinstall to see if it clears up the problems.

---

### Post by garvinrick4 on 2011-03-18
Sometimes it is better to use "purge" rather than 'remove".
[http://joysofprogramming.com/dpkg-purge-versus-remove/](http://joysofprogramming.com/dpkg-purge-versus-remove/)

---

### Post by plunksnakotis on 2011-03-18
OK. So what you can suggest to fix this problem ? Because it's not possible to install with apt-get cups and it's not possible to remove it completly and it's not even possible to USE apt-get to install anything !!! When installing ANYTHING it just hangs after apt-get detects cups process being removed partially !? Someone has some suggestions ?

Look what happens if I try to install it one more time :

```

root@kamp:/home/nhoj# apt-get install cups
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  foomatic-db-compressed-ppds foomatic-db hplip xpdf-korean xpdf-japanese
  xpdf-chinese-traditional xpdf-chinese-simplified cups-pdf
Recommended packages:
  cups-driver-gutenprint ghostscript-cups
The following packages will be upgraded:
  cups
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,914kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package cups.
(Reading database ... 152313 files and directories currently installed.)
Preparing to replace cups 1.4.4-6ubuntu2 (using .../cups_1.4.4-6ubuntu2.3_i386.deb) ...
stop: Job has already been stopped: cups
Unpacking replacement cups ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up cups (1.4.4-6ubuntu2.3) ...
**Installing new version of config file /etc/init/cups.conf ...**

```Bolded line stays forever, after this nothing happens and  process hangs..

When I terminate it leaves loads of hanged up processes like :
```

root@kamp:/home/nhoj# ps -ax | grep cups
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
  589 pts/2    S+     0:00 grep --color=auto cups
32260 ?        Ss     0:00 /usr/bin/dpkg --status-fd 24 --configure cups
32263 ?        S      0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/cups.postinst configure 1.4.4-6ubuntu2
32272 ?        S      0:00 /bin/sh /var/lib/dpkg/info/cups.postinst configure 1.4.4-6ubuntu2
32306 ?        S      0:00 start cups
root@kamp:/home/nhoj# ps -ax | grep apt
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
  546 pts/2    S+     0:00 grep --color=auto apt
31996 pts/2    T      0:01 apt-get install cups


```APT-GET -F INSTALL also fails .......

These questions/answers  doesn't help also : [http://askubuntu.com/questions/16726/cant-print-cups-package-corrupted-and-hangs-on-re-install](http://askubuntu.com/questions/16726/cant-print-cups-package-corrupted-and-hangs-on-re-install)

I killed all these bogus processes and tried : 

```

root@kamp:/home/nhoj# dpkg -r --force-remove-reinstreq cups
(Reading database ... 152312 files and directories currently installed.)
Removing cups ...


```
Still it hangs .... no luck ..... HELP ME :)))

---

### Post by garvinrick4 on 2011-03-18
so what does:
```
sudo dpkg --configure cups
```do.

Relax a bit and think about what you are doing before
cleaning and autoremoving and removing packages.

You got your system in this shape no one else. By giving the clean command
you erased the package to be reinstalled in your system already. Why?

Take one step at a time and use google as much as possible and these forums
until you get your system straight.

Edit: That was autoclean not clean so you might get lucky and have the package
        still with you and not have to fetch a new one.

---

### Post by plunksnakotis on 2011-03-18
> 
so what does:
     Code:
     sudo dpkg --configure cups 
do.

Relax a bit and think about what you are doing before
cleaning and autoremoving and removing packages.

You got your system in this shape no one else. By giving the clean command
you erased the package to be reinstalled in your system already. Why?

Take one step at a time and use google as much as possible and these forums
until you get your system straight.

Edit: That was autoclean not clean so you might get lucky and have the package
        still with you and not have to fetch a new one.     
Ok, sorry for being a little anxious about this :) Actually I'm quite relaxed. Nevermind. Autoclean and remove actually does not remove anything ,because when it tries to remove cups - it suddenly hangs. And I think that was "Update manager" that suggested to install cups and other updates and it hanged up. Just then I tried to solve the problem by removing cups. But ofcourse with Linux it's like this and I'm not blaming anyone. Actually it's interesting trying to solve this. BTW command clean was useless, because it did nothing .... :)

```

root@kamp:/home/nhoj# sudo dpkg --configure cups
Setting up cups (1.4.4-6ubuntu2.3) ...

```hangs up also .... :)

Maybe I should manually delete cups ? Or ... some other suggestions you have ? Thank you for helping me !

P.S. For >1year I'm using ubuntu and my system always aren't straight, always problems and always hassle, but I want to learn ! :) Maybe I should invest some time into languages so I can solve problems in deeper level ?

---

### Post by garvinrick4 on 2011-03-18
Have you tried to purge:
```
sudo apt-get purge cups
```It removes all the config files also.
#sudo apt-get clean does do something it cleans out all the packages on your
machine that are installed so you have to fetch new ones from repositories
when needed. 


You need to purge out all of cups and then reinstall new package. 
You can see it here most likely: Go to Synaptics to status and to residual config. as in screenshot:
* Very glad to hear you are interested in learning, so am I and that makes Linux enjoyable to me.*

---

### Post by plunksnakotis on 2011-03-18
Look : 
```

root@kamp:/home/nhoj# sudo apt-get purge cups
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cups*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 8,376kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 152312 files and directories currently installed.)
Removing cups ...


```Also hangs up !! :) What a heck ? Actually I don't need cups at all, I don't even have a printer so ... But this is really annoying ,because I have to compile everything from source and that usually gives problems when installing software... Other Ideas how to solve this ? I can't find on google anything related to similar problem ...

So you say Synaptic and I say it's ****** up, I can't even start it because it throws an error statig : 
```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```Ok, ok ... I will run one more time dpkg --configure -a and what I get ? WOW WOW !!!!! THANK YOU FOR POINTING ME TO CORRECT DIRECTION.... Solution was GUI :) I ran dpkg --configure -a and somehow this time it sucessfully configured everything Then I ran Synaptic and completly removed cups and hlip(yea?) broken installs. After this apt-get started to shine like a new :) What now I have different Q. What does dpkg --configure **-a** mean ? I couldn't find in man page function -a , only -A and to my little dumb head this completly different story ??

[[IMG]http://img860.imageshack.us/img860/4876/screenshot1b.png[/IMG]]("http://img860.imageshack.us/i/screenshot1b.png/")

[IMG]http://img860.imageshack.us/i/screenshot1b.png[/IMG]

---

### Post by plunksnakotis on 2011-03-18
> **5149.5 said:**
> CUPS is common unix printing system and is used by everything. I would try a reinstall to see if it clears up the problems.

What do you mean is used by everything ? :)

---

### Post by garvinrick4 on 2011-03-18
```
sudo dpkg --configure -a
```
Is to fix broken packages also below.
```
sudo apt-get -f install
```

*Glad you are up and running.
#The difference between purge and remove is purge will clean out config-files also.
Most of time better to purge than remove.
#Also read up on aptitude instead of apt-get and dpkg command.
#See ya later Enjoy your Ubuntu

---

