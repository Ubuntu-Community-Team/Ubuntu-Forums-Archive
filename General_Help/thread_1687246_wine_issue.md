---
title: "wine issue"
date: 2011-02-13
forum: General Help
---

### Post by xenocidecm on 2011-02-13
Sup folks,
I just started playing with ubuntu a few weeks ago. I installed it and I was configuring everything (programs and such) and when I went to install wine (I ran the sudo apt-get install wine) command, put my password in and let it run and then it got to the end and showed me the blue windows-esque splash screen about the eula. I tried to select ok but I wasn unable to it seemed as though the Terminal had crashed. I closed it, and restarted the comp. When I rebooted I checked to see if it had indeed installed, it was not listed under applications. So i again attempted to install it and then it gave me another error:
##E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?##
I then, figuring something had gone wrong with the installation tried to delete the files but nothing worked.
Any ideas? I am somewhat a noob when it comes to linux so any help would be appreciated.
Thanks.
Also, I saw somewhere someone print this out to screen, thought it might help:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  wine           <none>         (no description available)
un  wine-doc       <none>         (no description available)
un  wine-gecko     <none>         (no description available)
un  wine-utils     <none>         (no description available)
un  wine1.0        <none>         (no description available)
un  wine1.0-gecko  <none>         (no description available)
iU  wine1.2        1.2.2-0ubuntu2 Microsoft Windows Compatibility Layer (Binar
iU  wine1.2-gecko  1.0.0-0ubuntu4 Microsoft Windows Compatibility Layer (Web B
un  winesetuptk    <none>         (no description available)
un  winetricks     <none>         (no description available)

---

### Post by corncob on 2011-02-13
> **xenocidecm said:**
> Sup folks,
I just started playing with ubuntu a few weeks ago. I installed it and I was configuring everything (programs and such) and when I went to install wine (I ran the sudo apt-get install wine) command, put my password in and let it run and then it got to the end and showed me the blue windows-esque splash screen about the eula. I tried to select ok but I wasn unable to it seemed as though the Terminal had crashed. 

You lost me after this but what I think you needed to do to get over to the [OK] button was to use the TAB key.  Its not obvious that that's how you need to do it.
You might go to System > Administration > Synaptic Package Manager, search for Wine, mark for complete removal, and apply.  Then start all over again with the installation.

---

### Post by xenocidecm on 2011-02-13
Thanks for responding. I tried what you asked and I got another error.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by corncob on 2011-02-13
> **xenocidecm said:**
> Thanks for responding. I tried what you asked and I got another error.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Did you do what it said to do?  In the Terminal:
```
sudo dpkg --configure -a
```

---

### Post by initialhit on 2011-02-13
> **xenocidecm said:**
> 
 So i again attempted to install it and then it gave me another error:
##E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?##


With unix only one install can happen at a time, this means that something is using the superuser power / admininistrative powers and thus you cant install anything. Try doing the command like corncob said, and if you still cant get it to work try restarting again. Also in terminal your mouse doesnt work... tab and arrow keys are the only way to move, and enter to select!

---

### Post by xenocidecm on 2011-02-14
Worked. Suppose I should have just done what Linux told me to do. I'm used to errors being very vague or useless all together. Either way, thanks fellas for the help.

---

