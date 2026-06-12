---
title: "Howto - uninstall the webmin from the repository and install the official one"
date: 2006-01-22
forum: General Help
---

### Post by calt129 on 2006-01-22
Hi,

*I've posted this howto to howto section, but apparently the moderators thought it's not worth a howto, so that's why I'm posting this here, in case it can help someone.*

If you install the recent webmin package (v1.230-1) from the Ubuntu repository, you might end up with a broken webmin installation :mad: Furthermore, if you uninstall & reinstall it, you might really screw up things to a point where neither installation nor uninstallation is possible. I'm gonna show you how you can uninstall it if you've already installed the broken package (step 1) and install the package from webmin.com.
[LIST=1]
[*]**Run this step only if you have the package from the repository!**
During the uninstallation webmin would complain about 2 missing files: */etc/webmin/webmin.acl* & */etc/webmin/update.conf*. First create them with:
```
sudo touch /etc/webmin/{webmin.acl,update.conf}
```

Now you may proceed with the uninstallation:
```
sudo apt-get remove webmin-core webmin
```
*Note: If you do this via synaptic or aptitude, they might want to uninstall apache & other depended packages in case they are needed **only** for webmin and wouldn't be used otherwise. So **do not use synaptic or aptitude!** We'll need these packages later.*
[*]Now download the latest webmin package (at the time of this posting v1.250) from the [nearest webmin.com mirror]("http://www.webmin.com/index4.html").
[*]Unpack it with, cd to the directory (correct filename if needed):
```
tar xzvf webmin-1.250.tar.gz
cd webmin-1.250

```
and start the installation (change the target location if needed):
```

sudo ./setup.sh /usr/local/webmin/

```
Answer the few questions such as config-dir, etc.
*Note: Do not simply run setup.sh if you want to define the target yourself because setup.sh does **not** ask you for the target dir.*
[*]Most probably webmin can't create the startup script under /etc/init.d, check it with:
```
ls -al /etc/init.d/webmin
```
If this is the case, it is because webmin tries to create the script under */etc/rc.d/init.d*. So we'll create the directory temporarily, let webmin create the startup script, move the script to the correct location and delete the dir back.

First create the temporary directory:
```
sudo mkdir -p /etc/rc.d/init.d
```
And go to to the webmin dir and run the script with:
```
cd /usr/local/webmin/init/
sudo sh -c 'WEBMIN_CONFIG=/etc/webmin WEBMIN_VAR=/var/log/webmin /usr/local/webmin/init/atboot.pl webmin'

```
*Note: please replace the webmin, config & log directories with yours.*
Now move the script to its correct location with:
```
sudo mv /etc/rc.d/init.d/webmin /etc/init.d/
```
and delete the directory:
```
sudo sh -c 'rmdir /etc/rc.d/init.d; rmdir /etc/rc.d'
```
*Note: **Do not use** simply *rm -fr /etc/rc.d/* just in case you might have the directory already and there are files under it, rmdir should avoid this.*
[*]This script does **NOT** automatically start webmin at bootup, you should do this with, for example, with the following:
```
sudo ln -s /etc/init.d/webmin /etc/rc3.d/S13webmin
```
or similar. **_However, do not mess with startup scripts on the commandline if you do not know how init-scripts work and I would definitely recommend that you use webmin to mess with these scripts._**
[/LIST]

Now, finally you may open [http://localhost:10000/](http://localhost:10000/) (or whatever port you've set during the installation and start using webmin.

*EDIT - Post installation notes:*
The official webmin package is not optimized for ubuntu, that is, some paths in module configurations might be wrong. For example, Apache module might expect *apachectl* under /bin/apachectl whereas your system has it under */usr/local/bin/apachectl*, so you might tweak a few configs under apache. A big help here is the command-duo *updatedb* & *locate*. In order to find missing files just do an update first and search for the file with:
```
sudo updatedb
locate apachectl

```
Also note, in order to open webmin from another machine, you need to edit webmin.conf first, because only 127.0.0.1 is allowed until specified otherwise.

From there on, you're beyond this howto...

Please inform me, if this does or does not work for you! I'll update it this howto accordingly.

Cheers :D

---

### Post by jcl on 2006-02-06
Thanks! Got webmin working, that's a plus.

Now for the minus... now that I've uninstalled webmin from apt-get and installed it manually, the system doesn't think it's installed. This wouldn't be a problem, except now I want to install 'squid-cgi' from apt-get and it's wanting to pull in 'webmin' and 'webmin-squid' before it will install it. This will kill my webmin installation that's working.

How do I hack the apt-get database so that it thinks webmin is installed (when in fact it is) so it won't try to pull it back in when it's a dependency and I can get 'squid-cgi' installed?

Thanks

---

### Post by jcl on 2006-02-06
On second thought, maybe it wouldn't be such a good idea to hack the apt database to fool it into thinking webmin is installed because then it will always want to push down updates if/when they become available?

Ideally I would like to figure out how to force apt-get to install 'squid-cgi' only without pulling in any other packages...

Thanks

---

### Post by calt129 on 2006-02-07
[QUOTE=jcl]Thanks! Got webmin working, that's a plus.[/QUOTE]

:) Glad to hear it.

[QUOTE=jcl]
How do I hack the apt-get database so that it thinks webmin is installed (when in fact it is) so it won't try to pull it back in when it's a dependency and I can get 'squid-cgi' installed?[/QUOTE]

You can let apt-get/aptitude ignore the dependencies. In aptitude, simply press *-* (minus key) to deselect the depended package (webmin, etc.) when aptitude shows you the list of to-be-installed packages.

---

### Post by jcl on 2006-02-07
> In aptitude, simply press - (minus key) to deselect the depended package (webmin, etc.) when aptitude shows you the list of to-be-installed packages.

When I deselect the webmin packages in aptitude, it marks 'squid-cgi' as broken and won't install it (it prompts me to fix the broken packages and it pulls 'webmin' and 'webmin-squid' back in)

Thanks

---

### Post by Ranger on 2006-02-09
Hello, Thanks for the howto.
I am having trouble with the section

> 
And go to to the webmin dir and run the script with:

```
cd /usr/local/webmin/init/
sudo sh -c 'WEBMIN_CONFIG=/etc/webmin WEBMIN_VAR=/var/log/webmin /usr/local/webmin/init/atboot.pl webmin'

```
*Note: please replace the webmin, config & log directories with yours.*


it returns

```

em2@tka-em2:/$  cd /usr/local/webmin/init
em2@tka-em2:/usr/local/webmin/init$ sudo sh -c 'WEBMIN_CONFIG=/etc/webmin WEBMIN_VAR=/var/webmin /usr/local/webmin/init/atboot.pl webmin'
Password:

-----
Script was not run with full path (failed to find /usr/local/webmin/init/atboot.pl under /usr/local/webmin/)
-----
em2@tka-em2:/usr/local/webmin/init$

```

any suggestions?
Thanks

---

### Post by calt129 on 2006-02-10
[QUOTE=Ranger]Hello, Thanks for the howto.
I am having trouble with the section
...
Script was not run with full path (failed to find /usr/local/webmin/init/atboot.pl under /usr/local/webmin/)
[/QUOTE]

The problem is the script which creates the startup-script doesn't exist under that directory but the installation should have copied it there (I'm assuming you have installed webmin under */usr/local*) Try this:
```
sudo find / -name atboot.pl
```

It should return at least one result, preferably somewhere under /usr/local. If not, you have not successfully installed webmin yet. Review the steps, especially step 3 (the one with *sudo ./setup.sh /usr/local/webmin/*).

---

### Post by calt129 on 2006-02-10
[QUOTE=jcl]When I deselect the webmin packages in aptitude, it marks 'squid-cgi' as broken and won't install it (it prompts me to fix the broken packages and it pulls 'webmin' and 'webmin-squid' back in)[/QUOTE]

You can temporarily disable the dependency checking, under *Menu (key F10)-> Options-> Dependency Handling*. But I'm a bit concerned about this :-k

As I understand, squid-cgi is used to administer Squid via a web-interface. Then why don't you simply install the squid plugin from webmin.com?

---

### Post by Ranger on 2006-02-10
The script does seem to be in the right place:
```

em2@tka-em2:~$ sudo find / -name atboot.pl
/usr/local/webmin/init/atboot.pl
find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
em2@tka-em2:~$ cd /usr/local/webmin/init/
em2@tka-em2:/usr/local/webmin/init$ sudo sh -c 'WEBMIN_CONFIG=/etc/webmin WEBMIN_VAR=/var/webmin /usr/local/webmin/init/atboot.pl webmin'

-----
Script was not run with full path (failed to find /usr/local/webmin/init/atboot.pl under /usr/local/webmin/)
-----
em2@tka-em2:/usr/local/webmin/init$

```
but it still does not like it. When it says```
failed to find /usr/local/webmin/init/atboot.pl under /usr/local/webmin/
```
it looks to me like it is looking for the path */usr/local/webmin/init/atboot.pl * in the directory * /usr/local/webmin/ *. As a beginner though, I could be totaly confused:???: 
Webmin does run, but will not run apache2 or Mysql, both of which are installed.
Here is a brief history of my attempt to install it so far.
After running *sudo touch /etc/webmin/{webmin.acl,update.conf}*
I tried to remove my original installation with *sudo apt-get remove webmin-core webmin* but it was not succesful, perhaps because it was version 1.180 and was not installed with synaptic or apt-get. I installed the new one anyway and it recognized the existing installation and said to remove the old /usr/local/webmin directory when I was finished. As I had installed it to the same directory it broke when I removed it so I put it back. I then renamed the /usr/local/webmin, /var/webmin, and /etc/webmin folders changing webmin to webmin-old and proceeded with the install process.
Being a recent convert from windows I am more comfortable in a gui than command line and I used nautilus to extract the package to a temporary folder in my home folder to install from. After that I followed the directions as written, changing the targets as necessary.
Hopefully I have not messed it up to the point of needing to reinstall ubuntu :)  
Thanks

---

### Post by calt129 on 2006-02-11
> **Ranger]
it looks to me like it is looking for the path */usr/local/webmin/init/atboot.pl * in the directory * /usr/local/webmin/ *. As a beginner though, I could be totaly confused:???:
[/QUOTE]

[QUOTE=Ranger]
Webmin does run, but will not run apache2 or Mysql, both of which are installed.
[/QUOTE]
Oh, well said. In the Howto, I've forgotten to mention that, the default webmin distribution does not automatically recognize all the configuration and binary paths in the system. That is, apache might be installed as /bin/httpd or /usr/local/bin/apache or so, and sometimes you need to tweak the module settings in webmin, and change a few paths said:**
> 
Here is a brief history of my attempt to install it so far.
After running *sudo touch /etc/webmin/{webmin.acl,update.conf}*
I tried to remove my original installation with *sudo apt-get remove webmin-core webmin* but it was not succesful, perhaps because it was version 1.180 and was not installed with synaptic or apt-get. I installed the new one anyway and it recognized the existing installation and said to remove the old /usr/local/webmin directory when I was finished. As I had installed it to the same directory it broke when I removed it so I put it back. I then renamed the /usr/local/webmin, /var/webmin, and /etc/webmin folders changing webmin to webmin-old and proceeded with the install process.
Being a recent convert from windows I am more comfortable in a gui than command line and I used nautilus to extract the package to a temporary folder in my home folder to install from. After that I followed the directions as written, changing the targets as necessary.
Hopefully I have not messed it up to the point of needing to reinstall ubuntu :)  
Thanks

Well, you lost me somewhere in the middle :confused:  but I don't think you need to reinstall Ubuntu :-) And remind you there's no wrong liking GUI more than command line, so you're not abnormal :D Now, if I interpret the error msg correctly, at the time of installation atboot.pl has been copied with a hard-coded path */usr/local/webmin* in it, and its location has been changed afterwards. Unfortunately that installation scripts have lots of cross-dependencies that I wouldn't delve more into debugging atboot.pl.

Why don't you first remove all traces of webmin first with ```
/etc/webmin/uninstall.sh
``` (and if necessary renaming like you did is always wise), and even re-install and immediately remove webmin from repository via aptitude and follow the guide again. Just between us, I had to reinstall/deinstall the repository-webmin a few times until I got it all in place and understood what's going on.

I'll edit the howto to add that issue with server configs..

---

### Post by jcl on 2006-02-11
> As I understand, squid-cgi is used to administer Squid via a web-interface. Then why don't you simply install the squid plugin from webmin.com?

The more software I have managed by apt-get the better... I didn't want more 'rogue' software out there to have to worry about depenencies on.

No worries though, I posted another thread about this and basically I downloaded the .deb package, used commands to pull the package apart, edited the control file, pulled out the webmin dependencies, rebuilt the package and installed it. Worked like a charm.

Thanks

---

### Post by calt129 on 2006-02-11
[QUOTE=jcl]The more software I have managed by apt-get the better... I didn't want more 'rogue' software out there to have to worry about depenencies on.
[/QUOTE]

A webmin plugin is simply a bunch of files which are copied under the webmin directory and thus is **not** a software in the apt-get sense which might copy its files all over the filesystem. So they wouldn't mess with the intricate deb dependency tree. You can compare them much to Firefox extensions. The dependency was only there because you wanted to install a deb-package although you don't have have the depended package, not because webmin-squid is a rogue package. Now you can't update webmin or webmin-squid without going through much trouble. It's your call but **I** would definitely have installed the webmin plugin, it's much *cleaner*...

---

### Post by Ranger on 2006-02-11
Thanks for the update.
I uninstalled with */etc/webmin/uninstall.sh* and removed the var/webmin folder manually as it had not removed that one. I then reinstalled from the package that I downloaded (skipping the synaptic install and uninstall). Unfortunatly this did not resolve the atboot.pl issue. However, webmin seemed to be running so I decided to ignore that and deal with Apache2. 
To get this working I adjusted the configuration and binary paths in the module settings (*updatedb & locate* were quite handy :). 
I also had to change the permissions for */etc/apache2/apache2.conf* and comment out a reference to httpd.conf (which is just a backwards compatability placeholder in apache2) in apache2.conf (I also renamed httpd.conf to disabled-httpd.conf) 
One other item that caused me some trouble is that apachectl is now apache2ctl.

At this point it seems to be working for what I need it for, so I will probably leave it as is and get some work done :)
One minor typo, in your edited howto you have 
```
sudo updateb
locate apachectl
```
instead of updatedb, but fortunatly it is spelt right in the line above it.
Thanks for your help.

---

### Post by kkimmell on 2006-02-13
Ok... I'm new to ubuntu but have *some* *nix experience.

I removed the apt-get portion of webmin and installed the latest via this how-to and all was seemingly working fine. I believe that it still is but I don't think it's running. I thought that it just needed to be added to the startups but I can't even seem to get it running with a restart or force-restart command.

I'm at a loss as far as how to troubleshoot the why's of this. Can anyone point me in the right direction?

A couple notes on my trouble shooting attempts:

1. trying an "/etc/init.d/webmin start" -- or restart, etc gives no output
2. stopping apache2 has no effect either (in case there was a conflict)
3. a "ps aux | grep webmin" only show the "grep webmin" line.

?? -KK

---

### Post by jcl on 2006-02-13
Kkimmell,

Try /etc/webmin/start... that's what I use.

---

### Post by kkimmell on 2006-02-13
[QUOTE=jcl]Kkimmell,

Try /etc/webmin/start... that's what I use.[/QUOTE]

I got ansie and removed webmin and reinstalled. I now see that the above mentioned script does indeed seem to work.

Now I've got a slightly different problem. At the part of the reinstall where I'm trying to get the startup script created I'm getting this error:

**Script was not run with the full path (failed to find /usr/local/webmin/init/atboot/pl under /usr/local/webmin/init#)**

I'm at a loss. I thought I could just use the webmin console to add it to the startup sequence and point it ot the script that you pointed out but after setting it up I'm unable to set is as "start at boot" as I'm getting the following error from webmin:

[B]Failed to save action: Failed to open /etc/rc.d/rc5.d/S99webmin for writing: No such file or directory
[/B]
So it would appear that webin is failing for the same reason the it's setup script fails.

Hmm....

---

### Post by calt129 on 2006-02-14
[QUOTE=kkimmell]I got ansie and removed webmin and reinstalled. I now see that the above mentioned script does indeed seem to work...
**Script was not run with the full path (failed to find /usr/local/webmin/init/atboot/pl under /usr/local/webmin/init#)**
[/QUOTE]

It should be atboot.pl not atboot/pl. You can just copy and paste the lines.

[QUOTE=kkimmell]
I'm at a loss. I thought I could just use the webmin console to add it to the startup sequence and point it ot the script that you pointed out but after setting it up I'm unable to set is as "start at boot" as I'm getting the following error from webmin.

[B]Failed to save action: Failed to open /etc/rc.d/rc5.d/S99webmin for writing: No such file or directory
[/B]
So it would appear that webin is failing for the same reason the it's setup script fails.

Hmm....[/QUOTE]

You're right, Webmin tries to find the init scripts under /etc/rc.d/init.d. So have you adjusted the rc.d paths under *module config* first? ;)

---

### Post by kkimmell on 2006-02-14
[QUOTE=calt129]It should be atboot.pl not atboot/pl. You can just copy and paste the lines.[/QUOTE]

That was a typo on my part. I did cut and paste from the script... but I hand typed the error message. I'm still unsure why I'm getting it. Here's an actual cut-n-paste: 

```
root@dtAlarm:/etc/init.d# cd /usr/local/webmin/init
root@dtAlarm:/usr/local/webmin/init# sudo sh -c 'WEBMIN_CONFIG=/etc/webmin WEBMIN_VAR=/var/log/webmin /usr/local/webmin/init/atboot.pl webmin'

-----
Script was not run with full path (failed to find /usr/local/webmin/init/atboot.pl under /usr/local/webmin/)
-----

```

[QUOTE=calt129]You're right, Webmin tries to find the init scripts under /etc/rc.d/init.d. So have you adjusted the rc.d paths under *module config* first? ;)[/QUOTE]

Okay... but what do I put in there? I'm assuming that master init scripts are in /etc/init.d but which of the rc#.d directories do I point to for the runlevel directories? Should it just be rc0.d?
:confused: 
-KK

---

### Post by calt129 on 2006-02-14
[QUOTE=kkimmell]That was a typo on my part...
Script was not run with full path (failed to find /usr/local/webmin/init/atboot.pl under /usr/local/webmin/)
[/CODE]
[/QUOTE]
I've no idea at this moment, but I'll look into it later.

> 
Okay... but what do I put in there? I'm assuming that master init scripts are in /etc/init.d but which of the rc#.d directories do I point to for the runlevel directories? Should it just be rc0.d?
:confused: 
-KK

*Directory in which runlevel directories are located*: **/etc/**
*Directory containing master init scripts*: **/etc/init.d**
The rest of the values should be OK the way they are.

---

### Post by kkimmell on 2006-02-15
[QUOTE=calt129]*Directory in which runlevel directories are located*: **/etc/**
*Directory containing master init scripts*: **/etc/init.d**
The rest of the values should be OK the way they are.[/QUOTE]

Cool. That did it!

Thanks.

-K

---

### Post by jinacio on 2006-02-17
> **calt129]Hi,

*I've posted this howto to howto section, but apparently the moderators thought it's not worth a howto, so that's why I'm posting this here, in case it can help someone.*

If you install the recent webmin package (v1.230-1) from the Ubuntu repository, you might end up with a broken webmin installation :mad: Furthermore, if you uninstall & reinstall it, you might really screw up things to a point where neither installation nor uninstallation is possible. I'm gonna show you how you can uninstall it if you've already installed the broken package (step 1) and install the package from webmin.com.
[LIST=1]
[*]**Run this step only if you have the package from the repository!**
During the uninstallation webmin would complain about 2 missing files: */etc/webmin/webmin.acl* & */etc/webmin/update.conf*. First create them with:
```
sudo touch /etc/webmin/{webmin.acl,update.conf}
```

Now you may proceed with the uninstallation:
```
sudo apt-get remove webmin-core webmin
```
*Note: If you do this via synaptic or aptitude, they might want to uninstall apache & other depended packages in case they are needed **only** for webmin and wouldn't be used otherwise. So **do not use synaptic or aptitude!** We'll need these packages later.*
[*]Now download the latest webmin package (at the time of this posting v1.250) from the [nearest webmin.com mirror]("http://www.webmin.com/index4.html").
[*]Unpack it with, cd to the directory (correct filename if needed):
```
tar xzvf webmin-1.250.tar.gz
cd webmin-1.250

```
and start the installation (change the target location if needed):
```

sudo ./setup.sh /usr/local/webmin/

```
Answer the few questions such as config-dir, etc.
*Note: Do not simply run setup.sh if you want to define the target yourself because setup.sh does **not** ask you for the target dir.*
[*]Most probably webmin can't create the startup script under /etc/init.d, check it with:
```
ls -al /etc/init.d/webmin
```
If this is the case, it is because webmin tries to create the script under */etc/rc.d/init.d*. So we'll create the directory temporarily, let webmin create the startup script, move the script to the correct location and delete the dir back.

First create the temporary directory:
```
sudo mkdir -p /etc/rc.d/init.d
```
And go to to the webmin dir and run the script with:
```
cd /usr/local/webmin/init/
sudo sh -c 'WEBMIN_CONFIG=/etc/webmin WEBMIN_VAR=/var/log/webmin /usr/local/webmin/init/atboot.pl webmin'

```
*Note: please replace the webmin, config & log directories with yours.*
Now move the script to its correct location with:
```
sudo mv /etc/rc.d/init.d/webmin /etc/init.d/
```
and delete the directory:
```
sudo sh -c 'rmdir /etc/rc.d/init.d said:**
> This script does **NOT** automatically start webmin at bootup, you should do this with, for example, with the following:
```
sudo ln -s /etc/init.d/webmin /etc/rc3.d/S13webmin
```
or similar. **_However, do not mess with startup scripts on the commandline if you do not know how init-scripts work and I would definitely recommend that you use webmin to mess with these scripts._**
[/LIST]

Now, finally you may open [http://localhost:10000/](http://localhost:10000/) (or whatever port you've set during the installation and start using webmin.

*EDIT - Post installation notes:*
The official webmin package is not optimized for ubuntu, that is, some paths in module configurations might be wrong. For example, Apache module might expect *apachectl* under /bin/apachectl whereas your system has it under */usr/local/bin/apachectl*, so you might tweak a few configs under apache. A big help here is the command-duo *updatedb* & *locate*. In order to find missing files just do an update first and search for the file with:
```
sudo updatedb
locate apachectl

```
Also note, in order to open webmin from another machine, you need to edit webmin.conf first, because only 127.0.0.1 is allowed until specified otherwise.

From there on, you're beyond this howto...

Please inform me, if this does or does not work for you! I'll update it this howto accordingly.

Cheers :D


WOW

hmm how this?

download the latest webmin release (currently 1.1260) 
tar xvf webmin-1.260.tar.gz
cd webmin-1.260
edit os_list.txt, and add this line:
```

Ubuntu Linux			$1	debian-linux	$1	$etc_issue =~ /Ubuntu.*\s([0-9\.]+)\s/i

```

sudo ./install.sh /usr/share/webmin
	Use SSL (y/n): y 
	Start Webmin at boot time (y/n): y	

now remove temporary files and login to webmin.
all the paths to the programs should be correct! :D

---

### Post by calt129 on 2006-02-18
[QUOTE=jinacio]...
edit os_list.txt, and add this line:
```

Ubuntu Linux			$1	debian-linux	$1	$etc_issue =~ /Ubuntu.*\s([0-9\.]+)\s/i

```

sudo ./install.sh /usr/share/webmin
	Use SSL (y/n): y 
	Start Webmin at boot time (y/n): y	
...[/QUOTE]

Nice, much cleaner than my method :) But, does this uninstall the old package as well or do you still have to uninstall manually? If you don't uninstall webmin, then does apt-database think it still has the old version or does webmin automatically update the apt-db by itself?

---

### Post by jinacio on 2006-02-18
[QUOTE=calt129]Nice, much cleaner than my method :) But, does this uninstall the old package as well or do you still have to uninstall manually? If you don't uninstall webmin, then does apt-database think it still has the old version or does webmin automatically update the apt-db by itself?[/QUOTE]

sorry, forgot that: you still need to uninstall the old version first.

hope it helps

btw: i submited a bug report in the webmin page asking for this support "out of the box". :)

---

### Post by jinacio on 2006-02-18
[QUOTE=jinacio]sorry, forgot that: you still need to uninstall the old version first.

hope it helps

btw: i submited a bug report in the webmin page asking for this support "out of the box". :)[/QUOTE]

Edit: 
it's official: that small patch will be included in the next webmin release :)

---

### Post by lakelovers on 2006-03-07
I've followed this thread and successfully installed the latest version of webmin (actually twice). After installing webmin and working with it, I logged off, shut down my computer, then when I started up the next morning I could not open webmin. This happened with both installations. I get the message that "The connction was refused when attempting to connect to https://127.0.0.1:10000." How can I correct this situation?

This is an update. I found the solution: **sudo /etc/webmin/start**

Now that's pretty easy but I was gonig bonkers trying to figure it out. What I haven't figured out is how to get my laptop XP using my Ubuntu desktop printer. I keep working with webmin and cups trying a zillion different configurations and inputs. So far, I haven't found the key. Wish me luck. . .

---

### Post by calt129 on 2006-03-08
[QUOTE=lakelovers]...when I started up the next morning I could not open webmin. ... This is an update. I found the solution: **sudo /etc/webmin/start**[/QUOTE]

There's a more standard and *elegant* way to activate init scripts at startup, using **update-rc.d** command. For more information see [UbuntuBootupHowto in Ubuntu-Wiki]("https://wiki.ubuntu.com/UbuntuBootupHowto").

---

