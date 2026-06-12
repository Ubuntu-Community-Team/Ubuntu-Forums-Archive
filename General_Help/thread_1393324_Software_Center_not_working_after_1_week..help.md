---
title: "Software Center not working after 1 week..help"
date: 2010-01-29
forum: General Help
---

### Post by sathyashrayan on 2010-01-29
My system specification:

I am using is in my PC(stand alone) with the following system config..

AMD Sempron(tm) processor
2500+
704 MB RAM
ASUS mother board..
ubuntu version 9.10


When I click ubuntu software center ->search any software ->select the software -> click the arrow at right corner->then click install button for me nothing happens. It was installing for one week and now it seems to be not. It gives no error message no action, but just static. Is that a paid version or i am missing something basic? I have tried to do the following 

sudo dpkg --configure -a 
sudo apt-get update
sudo apt-get upgrade

from 

[http://www.ubuntux.org/node/9157](http://www.ubuntux.org/node/9157)

and my system is update. My ubuntu is a fresh installation.. 


Thanks for any help..

---

### Post by sathyashrayan on 2010-01-29
I know things can be done through synaptic package manager. But still don't understand why software center not working

---

### Post by zvacet on 2010-01-29
In system>admin>software sources check all under ubuntu software and first two under updates tab.Reload.See if software center is working.Are you able to install with synaptic or apt-get?

---

### Post by sathyashrayan on 2010-01-29
> **zvacet said:**
> In system>admin>software sources check all under ubuntu software and first two under updates tab.Reload.See if software center is working.Are you able to install with synaptic or apt-get?

>Reload.

I don't know what does the term reload means. But I un-check one tick mark and re-tick, then clicked revert. I don't see any refreshment. But when I close it started to update packages by downloading. Still the Software Center doesn't work.

>See if software center is working.

No.. It does not do after that too..

>Are you able to install with synaptic or apt-get?

system->admin->synaptic package manager can able to install. I don't know what is apt-get.

one more issues:

If I go to places->other drives (I have 2 drives, one is having windows partition) I used to  open the windows drives from linux with mount/unmount. But it was also not working. It just tells that it can not mount and never asked any password too. Shall i start separate thread for that?

---

### Post by zvacet on 2010-01-29
> If I go to places->other drives (I have 2 drives, one is having windows partition) I used to open the windows drives from linux with mount/unmount. But it was also not working. It just tells that it can not mount and never asked any password too. Shall i start separate thread for that?

Yes!

---

### Post by zvacet on 2010-01-29
> I don't know what is apt-get.

Synaptic is fron end for apt-get.Apt-get is terminal way to install packages with command 

```
sudo apt-get install package_name
```

If synaptic works then it is software center issue.Look [here]("https://answers.launchpad.net/ubuntu/+questions?field.search_text=software+center&field.sort=RELEVANCY&field.sort-empty-marker=1&field.actions.search=Search&field.language=en&field.language=hr&field.language-empty-marker=1&field.status=OPEN&field.status=NEEDSINFO&field.status=ANSWERED&field.status=SOLVED&field.status-empty-marker=1") for possible answer.

---

### Post by sathyashrayan on 2010-01-30
Thanks to all. I think I can manage with synaptic.  But I can not close this thread as solved since software center still not working for me.. :)

---

### Post by plucky on 2010-01-30
> **sathyashrayan said:**
> Thanks to all. I think I can manage with synaptic.  But I can not close this thread as solved since software center still not working for me.. :)

Open a terminal and type ```
software-center
``` and try to install an application.If there are any errors it should show up in the terminal window.Post output to forum.


You could also try re-installing the software-center application.

from a terminal ```
sudo apt-get install --reinstall software-center
``` and see if that fixes the problem.


Good Luck

---

### Post by garvinrick4 on 2010-01-30
Three lines of code below first to get rid of software-center
second to clean out cache of software
third to install new software from repositories and not the same one from old cache.
Open a terminal and type or copy and paste one at a time.





sudo apt-get purge software-center


sudo apt-get clean


sudo apt-get install software-center

---

### Post by sathyashrayan on 2010-02-02
> **plucky said:**
> Open a terminal and type ```
software-center
``` and try to install an application.If there are any errors it should show up in the terminal window.Post output to forum.


terminal error:

WARNING:root:_on_trans_error: org.freedesktop.PolicyKit.Error.NotAuthorized: ('system-bus-name', {'name': ':1.65'}) is not authorized: org.debian.apt.install-packages


> **plucky said:**
> 

You could also try re-installing the software-center application.

from a terminal ```
sudo apt-get install --reinstall software-center
``` and see if that fixes the problem.


Good Luck

After reinstalling 

WARNING:root:_on_trans_error: org.freedesktop.PolicyKit.Error.NotAuthorized: ('system-bus-name', {'name': ':1.68'}) is not authorized: org.debian.apt.install-packages
WARNING:root:daemon dies, ignoring: 12: It seems that the daemon died.

---

### Post by sathyashrayan on 2010-02-02
> **garvinrick4 said:**
> Three lines of code below first to get rid of software-center
second to clean out cache of software
third to install new software from repositories and not the same one from old cache.
Open a terminal and type or copy and paste one at a time.





sudo apt-get purge software-center


sudo apt-get clean


sudo apt-get install software-center

Same warning message:

WARNING:root:_on_trans_error: org.freedesktop.PolicyKit.Error.NotAuthorized: ('system-bus-name', {'name': ':1.72'}) is not authorized: org.debian.apt.install-packages

---

### Post by plucky on 2010-02-02
> **sathyashrayan said:**
> terminal error:

WARNING:root:_on_trans_error: org.freedesktop.PolicyKit.Error.NotAuthorized: ('system-bus-name', {'name': ':1.65'}) is not authorized: org.debian.apt.install-packages


After reinstalling 

WARNING:root:_on_trans_error: org.freedesktop.PolicyKit.Error.NotAuthorized: ('system-bus-name', {'name': ':1.68'}) is not authorized: org.debian.apt.install-packages
WARNING:root:daemon dies, ignoring: 12: It seems that the daemon died.

That looks like a problem with authorization.From a terminal ```
gksudo software-center
``` and see if that will install an application.

Do you have "admin" authorization on this account.Again from the terminal ```
id
``` and post output.

Found [this](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/444661)

Can you install from "Synaptic Package Manager" or the Terminal?

Good Luck

---

### Post by sathyashrayan on 2010-02-02
> **plucky said:**
> That looks like a problem with authorization.From a terminal ```
gksudo software-center
``` and see if that will install an application.


```
gksudo software-center
```

opens the software-center, when I try to install any software, it proceeds to install ACE application I get following error 

ERROR:root:error in _on_trans_finished 'ERROR: Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.

unace'

> **plucky said:**
> 
Do you have "admin" authorization on this account.Again from the terminal ```
id
``` and post output.


No i don't have a root username or password. When I install the ubuntu it has asked a username and pawword but not an root username. For every sudo, it askes for password with my name in it.

 I have installed RHEL, it asked for root username and pawword during installition. And later the linux got installed, it prompts for sub-user. 

```
id
```

Output:
----------
uid=1000(sathyashrayan) gid=1000(sathyashrayan) groups=4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),115(admin),120(sambashare),1000(sathyashrayan)

> **plucky said:**
> 
Found [this](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/444661)

Can you install from "Synaptic Package Manager" or the Terminal?


I can install Synaptic Package Manager and Terminal with sudo, but not through software center.

Good Luck

---

### Post by plucky on 2010-02-02
> 115(admin)

Ubuntu does not use a root password but your account allows you access through sudo.

Did you read the [bug report](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/444661)?

Try ```
sudo apt-get install --reinstall policykit-1-gnome
```

and see if that fixes it.

Good Luck

---

### Post by Artem Medeu on 2010-05-06
Hi, folks.

I had similar problem after update today. 
"PolicyKit Authentication Agent" in System -> Preferences -> Startup Applications was pointing to "/usr/lib/kde4/libexec/polkit-kde-authentication-agent-1" o.O
I'm using ubuntu and it's very strange option. So I changed it to "/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1" then restarted session. All works now :)

if for some reason it won't work, try to do this using Ubuntu Tweak tool (it shows some hidden options in autostart management page).

Registered few mins ago to make this post :)

PS. sorry for my english.

---

### Post by labinnsw on 2010-06-17
> **Artem Medeu said:**
> Registered few mins ago to make this post :)

PS. sorry for my english.

If you didn't, I would still be searching. Your English is fine.:KS

[See this post also.]("http://swiss.ubuntuforums.org/showpost.php?p=9525189&postcount=7")

---

### Post by dalpets on 2010-06-17
Hi,

This is crazy stuff!

I just uninstalled 8.04.4 because after 2 weeks all the repositories failed-no updates possible-so I couldn't upgrade as I wished to do. Installed 10.04 with great expectations and now not only authentication fails in the software centre but I can't even use the sudo command (my password is not recognized in a terminal) to try out the alternative recommendations given in these threads. I presume that using the automatic login option during install would not account for this problem.

 So after hours and hours over days and days trying to get things to work I'm no further advanced with Ubuntu.

Are the developers working on this apparent bug?

---

### Post by XSAlliN on 2010-06-17
Never heard of this problem, thy a reinstall - and wright it down if it's to complicated (the password).

---

### Post by dalpets on 2010-06-17
The password I use is simple to remember as I use it on other systems.

---

### Post by dalpets on 2010-06-18
Turns out that my Smoothwall firewall was blocking the Software Centre downloads. I hadn't pursued that until now because I never had the problem with my other linux systems.

---

### Post by XSAlliN on 2010-06-18
I use UFW by GUI (gufw) and runs just fine, a pretty decent one. :)

---

### Post by LorraineO on 2011-12-03
Tried this and it worked. 
Thanks for your help

---

