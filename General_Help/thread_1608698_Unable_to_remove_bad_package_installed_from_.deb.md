---
title: "Unable to remove bad package installed from .deb"
date: 2010-10-29
forum: General Help
---

### Post by amish_geek on 2010-10-29
I attempted to install the CLI management tool for my Highpoint Rocket Raid card (rr62x) downloaded from this page: [http://www.highpoint-tech.com/USA_new/series_rr600.htm](http://www.highpoint-tech.com/USA_new/series_rr600.htm)


When I tried installing it, this is what happens:
```
# dpkg -i hptraidconf_3.5_amd64.deb 
Selecting previously deselected package hptraidconf.
(Reading database ... 68853 files and directories currently installed.)
Unpacking hptraidconf (from hptraidconf_3.5_amd64.deb) ...
Setting up hptraidconf (3.5) ...
dpkg (subprocess): unable to execute installed post-installation script: No such file or directory
dpkg: error processing hptraidconf (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 hptraidconf

```

I've tried removing it, purging it, reconfiguring it... no matter what I do, it stays in a failed-config state.


```

# dpkg -l hptraidconf
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                 Version                                              Description
+++-====================================================-====================================================-========================================================================================================================
rFR hptraidconf                                          3.5                                                  HighPoint RAID Management command line interface
root@vault:# aptitude purge hptraidconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  hptraidconf{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1,012kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing hptraidconf (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 hptraidconf
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

root@vault:# dpkg -l hptraidconf
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                 Version                                              Description
+++-====================================================-====================================================-========================================================================================================================
pFR hptraidconf                                          3.5                                                  HighPoint RAID Management command line interface
root@vault:# dpkg -P --force-all hptraidconf
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 51738 files and directories currently installed.)
Removing hptraidconf ...
dpkg (subprocess): unable to execute installed pre-removal script: No such file or directory
dpkg: error processing hptraidconf (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 hptraidconf
root@vault:# dpkg -r --force-all hptraidconf
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 51738 files and directories currently installed.)
Removing hptraidconf ...
dpkg (subprocess): unable to execute installed pre-removal script: No such file or directory
dpkg: error processing hptraidconf (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 hptraidconf
root@vault:# dpkg -l hptraidconf
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                 Version                                              Description
+++-====================================================-====================================================-========================================================================================================================
rFR hptraidconf                                          3.5                                                  HighPoint RAID Management command line interface


```


How can I get this package removed?  I was able to get a different management tool installed to configure my RAID so I don't need this one.  My system appears to be working, but everytime I use apt-get to install something else, it shows the hptraidconf package as failed.

---

### Post by matt_symes on 2010-10-29
Hi

Have you tried

sudo apt-get install -f

Kind regards

---

### Post by amish_geek on 2010-10-29
```
root@vault:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hptraidconf needs to be reinstalled, but I can't find an archive for it.

```

It was installed from a downloaded .deb file


I should add, this is Ubuntu 10.04 server

---

### Post by matt_symes on 2010-10-29
Hi

Can you print the output of  

cat /var/lib/dpkg/status | grep hptraidconf

Kind regards

---

### Post by amish_geek on 2010-10-29
```
root@vault:/# cat /var/lib/dpkg/status |grep hptraidconf
Package: hptraidconf
root@vault:/# 

```

hptraidconf is in RED.

---

### Post by matt_symes on 2010-10-29
Hi

There is a way to manually remove a package from dpkg.
This is assuming you have tried _all_ other methods.
i.e Purging and removing the package from dpkg.

As unless you know what you are doing you can do serious damage. If you want to be sure, it might be worth trying it in a VM first.
And make a backup the /var/lib/dpkg directory. I dont want to break your setup. Use at your own risk. Also i used this under debian.

1. dpkg -P hptraidconf

If this does not work

2. dpkg -L hptraidconf

This will list the files that hptraidconf uses.

Navigate to.

3. /var/lib/dpkg/info

Delete the file.

4. hptraidconf.postrm

Run

5. apt-get remove --purge hptraidconf

Remove all files and directories you found with dpkg -L

Then run 

6. apt-get update.

Kind regards.

---

### Post by amish_geek on 2010-10-29
That worked!  Thank you so much!

---

### Post by AllGamer on 2011-04-23
Thank you this worked perfectly.

just 1 more note to add

you can also remove the **htpsvr** as well using this method.

The **htpsvr** fails to install properly in 10.10 just like hptraidconf


***** UPDATE *****

Created a new Guide to install the GUI version of the RAID management software
[http://ubuntuforums.org/showthread.php?p=10712667](http://ubuntuforums.org/showthread.php?p=10712667)

---

### Post by dmovad on 2011-09-15
Interesting how there are others, perhaps many with the same issues.  This RocketRAID hardware/software has been a curse for the past 2 weeks and I just found this thread.  Never again will I purchase anything made by HighPoint! GARBAGE!

I did all the above several times and I still get the error:

E: I wasn't able to locate file for the hptraidconf package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the hptraidconf package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

This is causing frequent errors in my recently reinstalled system.  I'll loose a lot if I have to reinstall the OS.  Any help would be appreciated...

---

### Post by dmovad on 2011-09-17
I finally found a solution from searching for two days:

dpkg --remove --force-remove-reinstreq hptraidconf

I want to reaffirm "NEVER AGAIN WILL I BUY ANY RocketRAID PRODUCT"!

---

### Post by ionospheric on 2011-12-23
I got my package management back- thank you matt_symes!!:D

---

### Post by ionospheric on 2011-12-23
I am actually pretty happy with the controller, now that I got the driver working.

[http://ubuntuforums.org/showthread.php?t=1899544]("http://ubuntuforums.org/showthread.php?t=1899544")

Sure, having no working deb packages sucks, but at least they do support Linux, and with a bit of work, you can get it to work with Ubuntu. I don't know of any other PCI-Express RAID controllers with Ubuntu drivers, but at this point, I would buy from Highpoint again.

---

### Post by romanodog on 2012-03-06
I hate to resurrect an old thread like this but I have the exact same problem and the steps shown did not fix it for me.  I'm wondering if there is something else I can do.

When I run:  sudo apt-get remove --purge hptraidconf or if I try to install anything else
This is the output I get:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package hptraidconf needs to be reinstalled, but I can't find an archive for it.

```

I've done the rest of the steps but it still isn't removed from apt.  I'm grasping at straws here.

---

### Post by raja.genupula on 2012-03-06
> **romanodog said:**
> I hate to resurrect an old thread like this but I have the exact same problem and the steps shown did not fix it for me.  I'm wondering if there is something else I can do.

When I run:  sudo apt-get remove --purge hptraidconf or if I try to install anything else
This is the output I get:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package hptraidconf needs to be reinstalled, but I can't find an archive for it.

```

I've done the rest of the steps but it still isn't removed from apt.  I'm grasping at straws here.

please start new thread for better support. are you seeing anything like that pkg in Synaptic or software center .

---

### Post by Gerph on 2013-02-09
This might be an old thread, but I found it whilst searching for a solution to the same problem, so the solution may be useful to others.

The CLI RAID tools for the HighPoint 644L card (and others) have clearly not been tested on a Debian system as they do not install properly. However, the problem is minor and easy to fix. The issue is that the 'postinst' scripts in the deb have been saved in DOS format - with CR-LF line endings. The result is that the 'postinst' script cannot be executed because the file '/bin/sh<cr>' cannot be found. The file is actually completely redundant as well - it does nothing. <sigh>

Fixing it is easy. Run :

```
sudo dos2unix /var/lib/dpkg/info/hptraidconf.postinst
```

and then
```
sudo apt-get install
```

and the problem should now be fixed. If you don't have dos2unix installed, you can just make an empty file - become root with:

```
sudo -s
```

and then empty the file with

```
echo > /var/lib/dpkg/info/hptraidconf.postinst
```

and then do the

```
apt-get install
```

should also fix it (remember to exit from root afterward).

Although the file will not do anything right now, performing the 'dos2unix' is a better solution as it will keep things working even if in the future HPT supply a fuller 'postinst' file.

The same problem may exist with the 'prerm' file, so you may need to use the same trick to allow the package to be removed (which was the OP's question - I've addressed 'how to make these packages install', but the fix is similar for removal).

Anyhow, once you've done this, the CLI tools will work just fine. However, don't try to install the Web GUI tools at the same time; they won't work together without some manual modifications. I've written more detail on how to address the coexisting GUI+CLI on my diary at [http://gerph.org/diary/2013/diary-feb.html#9_Feb_2013](http://gerph.org/diary/2013/diary-feb.html#9_Feb_2013) which may help others looking at similar problems.

This is only a minor problem with the installation of the .debs that HighPoint supply, and once installed the CLI drivers appear to work relatively well.

---

### Post by wildmanne39 on 2013-02-09
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

