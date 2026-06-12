---
title: "gnokii problem"
date: 2010-06-01
forum: General Help
---

### Post by chris.olive on 2010-06-01
Dear All
I have been trying to get my Samsung mobile [Samsung B3310] connected to my laptop by trying out any and all phone sync programs, with no success.
One of which was gnokii, now I cannot remove all of it, I have tried synaptic, terminal and Ubuntu software centre.
I have removed it, replaced it, removed it and done apt-get remove several times with no effect!
The error I get is this 
"dpkg:unrecoverable fatal error, aborting:
syntax error: unknown group 'gnokii' in stateoverride file
E: sub process /usr/bin/dpkg returned an error code [2] 
A package tried to install. trying to recover:"
Any ideas will be gratefully received.

---

### Post by keraman on 2010-06-03
Hey,

that's a known bug. I have the same problem. Hopefully it is corrected in the next Release of Ubuntu. I think until now the only way to get rid of that bug is do a fresh install of the OS. If there's another way round, I am open to alternative ways :wink:

keraman

EDIT:
I googled a bit and found a solution at [http://osdir.com/ml/debian-user-german-debian/2009-12/msg00305.html:](http://osdir.com/ml/debian-user-german-debian/2009-12/msg00305.html:) 
gnokii does not create a group. So the Installation wants to change some settings in group gnokii but there isnt any group "gnokii". Just create a group "gnokii" and for me the workaround fixed it  :D

---

### Post by chris.olive on 2010-06-03
Thanks keraman, that did not work, I too had a look round the web with no luck, however I intend getting a new laptop within the next month so will do a fresh install on that and forget about gnokki

---

### Post by Vege 4wd on 2010-06-15
Hey, I have the same problem but there is no way I want to do a fresh install.
Gnokii seems to have broken blue tooth. I tried to install kbluetooth and got error with gnokii. 

anyway I am fairly new to Linux and do not know how to create the groups. Actually I dont really know what you mean.

I would appreciate it if you could shed some light.

---

### Post by msambenny on 2010-06-19
guys just do this
$ cd /var/lib/dpkg
$ sudo cp statoverride-old statoverride
$ sudo groupdel gnokii

Then delete all gnokii files in the system.

$ sudo dpkg --configure -a

Now synaptic should work......reply to this thread if it still doesn't work

---

### Post by crienoloog on 2010-06-22
> **msambenny said:**
> guys just do this
$ cd /var/lib/dpkg
$ sudo cp statoverride-old statoverride
$ sudo groupdel gnokii

Then delete all gnokii files in the system.

$ sudo dpkg --configure -a

Now synaptic should work......reply to this thread if it still doesn't work

Sorry give following error:
groupdel: group 'gnokii' does not exist

---

### Post by msambenny on 2010-06-22
if u don't have that group u may ignore that line....tell me your problem then i can be more precise

---

### Post by crienoloog on 2010-06-22
I had a problem updating my system - it gave me something like a gnokii error, but now that I did all your lines apparently this error has gone away... It looks like the last line
    $ sudo dpkg --configure -a
cleaned up the foul directory...
So problem solved, however don't know how... but I can update my system again...

Thanks for your help.

---

### Post by Peppuzzo on 2010-06-27
Guys,

this is affecting me now as well. However the suggested code did not solve the problem. What to do now?
When I try to update, i get this error message

```
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'gnokii' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
```

---

### Post by msambenny on 2010-06-27
Can you tell me your full system specifications including the OS version, what works for one might not work for the other so lets dig in to the problem and find out :p

---

### Post by Peppuzzo on 2010-06-27
Code did not work for me either. This is the terminal readout:

```
peppuzzo@PeppinoPC:/var/lib/dpkg$ cd /var/lib/dpkg
peppuzzo@PeppinoPC:/var/lib/dpkg$ sudo cp statoverride-old statoverride
[sudo] password for peppuzzo: 
peppuzzo@PeppinoPC:/var/lib/dpkg$ sudo groupdel gnokii
groupdel: group 'gnokii' does not exist
peppuzzo@PeppinoPC:/var/lib/dpkg$ sudo dpkg --configure -a
peppuzzo@PeppinoPC:/var/lib/dpkg$ 

```

My system is:

```
You are using Ubuntu 10.04 LTS
                - the Lucid Lynx - released in April 2010 and supported until April 2013.
```
    
Let me know if you need more info.

Thanks for the help.

---

### Post by Peppuzzo on 2010-06-27
I think I solved it. I had a look at the statoverride vile in /var/lib/dpkg

There was a line referring to gnokii:
```

root gnokii 4750 /usr/sbin/mgnokiidev
```

I removed the line, and synaptic is running ok now. I hope I did not screw up the system though.....

---

### Post by Vege 4wd on 2010-06-27
Had the same problem and that worked for me. Only thing is it then came up with a empty line error. Just had to put the cursor under the last line and hold down delete.

---

### Post by nightshade209 on 2010-07-05
> **Peppuzzo said:**
> I think I solved it. I had a look at the statoverride vile in /var/lib/dpkg

There was a line referring to gnokii:
```

root gnokii 4750 /usr/sbin/mgnokiidev
```

I removed the line, and synaptic is running ok now. I hope I did not screw up the system though.....

I had the same problem and this solved it for me. Thanks!

---

### Post by lord_alan on 2010-07-10
I just created the gnokii group and it removed the error for me.

```
$ sudo groupadd gnokii
```

Al

---

### Post by smardi on 2010-07-19
> **msambenny said:**
> guys just do this
$ cd /var/lib/dpkg
$ sudo cp statoverride-old statoverride
$ sudo groupdel gnokii

Then delete all gnokii files in the system.

$ sudo dpkg --configure -a

Now synaptic should work......reply to this thread if it still doesn't work


I was facing the same problem, this solution worked, now there is no issue. Thanks

---

### Post by xtian88 on 2010-07-25
> **Peppuzzo said:**
> I think I solved it. I had a look at the statoverride vile in /var/lib/dpkg

There was a line referring to gnokii:
```

root gnokii 4750 /usr/sbin/mgnokiidev
```

I removed the line, and synaptic is running ok now. I hope I did not screw up the system though.....

Thanks for this. This worked. I almost thought I'll have to reinstall. Phew!

---

### Post by Fender89 on 2010-08-09
> **Peppuzzo said:**
> I think I solved it. I had a look at the statoverride vile in /var/lib/dpkg

There was a line referring to gnokii:
```

root gnokii 4750 /usr/sbin/mgnokiidev
```

I removed the line, and synaptic is running ok now. I hope I did not screw up the system though.....

I had the exact same problem and this solved it for me. Thank you so much!

---

