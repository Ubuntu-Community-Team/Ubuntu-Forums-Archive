---
title: "AVG for Linux uninstall problem"
date: 2009-10-22
forum: General Help
---

### Post by MikRose on 2009-10-22
I tried to expand my Software List for Ubuntu 9.04 Jaunty Jack by using:
 ([http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/#comment-382](http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/#comment-382)), see below.

((("To Do List After installing Ubuntu 9.04 aka Jaunty*Jackalope

1 – Expand the Software Repository List
First of all, lets make Ubuntu “see” more packages. Go to the terminal and edit your sources.list with:

sudo gedit /etc/apt/sources.list

Here is the content of my sources.list which I think is quite complete to have all the necessary applications you could ever need. So delete the whole content of your sources list and replace it with the content of <author's>.  (Note, I saved a copy of my etc/apt/sources.list first)
Save it. Go to the Terminal and type:

sudo apt-get update && sudo apt-get upgrade

Now all your programs will run on the last version.")))

After doing this, I installed avg85flx version 85.287.  I was never able to see it in my Applications or Add/Remove Applications, but it was listed in my Synaptic Manager.  When I couldn't open it, I decided to uninstall it using Synaptic.  When I try, I get a message that says: 
E: avg85flx: subprocess pre-removal script returned error exit status 100
It won't let me Uninstall or reinstall from the same source (it tells me there is an error in the package).

There is NO Broken Package listed in Synaptic.

In Synaptic, if I highlight  "avg85flx version 8.5.287" and go to Properties > Dependencies, it tells me:    	
Conflicts avg71 and Conflicts avg75 (I can't find files using search)
I have used sudo apt-get remove –purge avg71 (or 75), but it tells me they aren’t installed.

I have used this command also for  "avg85flx version 85.287", as well as "sudo apt-get uninstall xxx", with no success.

I have tried to reinstall my saved copy of "etc/apt/sources.list" and replace the author's, no luck.

I have asked on Linux Questions with no result, although there is a similar thread for removing avg75 I think it is, but it won't work.

I went to System>Administration>Computer Janitor and AVG was listed, but when I try to clean it from the system, the message says:
E: sub-process /usr/bin/dpkg returned an error code (1).

Not sure where to turn now.

---

### Post by OpenGuard on 2009-10-22
```
dpkg -l | grep avg

```

Can you show us the output ?

---

### Post by phillw on 2009-10-23
I did this a while ago ... I'm pretty sure it should all still work (AVG is still on about version 8 !!)

> Removing AVG

Firstly, lets find out which version you have ...

~$ dpkg-query -l '*avg*'

You'll get something along the lines of....

un avg71fld     <none>         (no description available)
ii avg75fld     7.5.45_a0973     Free edition of antivirus solution with GUI.
un avggui     <none>         (no description available)
un avglinux     <none>         (no description available)
un wmavgload     <none>         (no description available)

or

un  avg71          <none>         (no description available)
un  avg75          <none>         (no description available)
ii  avg85flx       8.5.287        AVG Anti-Virus for Linux
un  avglinux       <none>         (no description available)
un  wmavgload      <none>         (no description available)

the bit we're after is the one beginning ii

now edit the file /etc/init.d/avgd and replace exit $? with exit 0 at the and of the file.

e.g. 

~$ sudo gedit /etc/init.d/avgd

finally ...

~$ sudo apt-get --purge autoremove avg75fld

OR

~$ sudo apt-get --purge autoremove avg85flx

(Or whatever is reported after ii above)

For version 7.5  you should get something like this

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  avg75fld*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 118297 files and directories currently installed.)
Removing avg75fld ...
 * Stopping avgdkill: 246: Illegal number: -
( not running)
 * [fail]
Uninstalling 'avgd' service initscripts...
Unregistering 'avgd' service ...
 Removing any system startup links for /etc/init.d/avgd ...
   /etc/rc0.d/K20avgd
   /etc/rc1.d/K20avgd
   /etc/rc2.d/S20avgd
   /etc/rc3.d/S20avgd
   /etc/rc4.d/S20avgd
   /etc/rc5.d/S20avgd
   /etc/rc6.d/K20avgd
Purging configuration files for avg75fld ...
dpkg - warning: while removing avg75fld, directory `/opt/grisoft/avggui/config' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt/grisoft/avggui/prog' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt/grisoft/avggui' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt/grisoft/avg7/data' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt/grisoft/avg7/var/update/backup' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt/grisoft/avg7/var/update/download' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt/grisoft/avg7/var/update/log' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt/grisoft/avg7/var/update' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt/grisoft/avg7/var' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt/grisoft/avg7' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt/grisoft' not empty so not removed.
dpkg - warning: while removing avg75fld, directory `/opt' not empty so not removed.


for version 8, it should look something like this..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  avg85flx*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 101MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 191786 files and directories currently installed.)
Removing avg85flx ...
 * Stopping avgd               |                                         [ ok ]
Uninstalling 'avgd' service initscripts...
Unregistering 'avgd' service ...
 Removing any system startup links for /etc/init.d/avgd ...
   /etc/rc0.d/K20avgd
   /etc/rc1.d/K20avgd
   /etc/rc2.d/S20avgd
   /etc/rc3.d/S20avgd
   /etc/rc4.d/S20avgd
   /etc/rc5.d/S20avgd
   /etc/rc6.d/K20avgd
Purging configuration files for avg85flx ...
Processing triggers for man-db ...


Now, the original article this is based on seemed to point to you still having some remnants of avg left in /opt with version 7.5 -- so, let's have a quick look

~$ cd /opt
~$ ls

if you see either an entry for either grisoft or avg - you need to remove them manually

~$ sudo rm -r grisoft

OR

~$ sudo rm -r avg

PLEASE BE CAREFUL  sudo rm -r  is EXTREMELY powerful - and you get no 2nd chance. If you are a little unsure - leave the files where they are until you are SURE you are happy with what you are typing.PLEASE note the caution on using the rm -r under sudo control. It is REALLY fatal if you do it in the wrong place.

Regards,

Phill.

---

### Post by fishears on 2011-02-19
Thank you phill!!!

---

