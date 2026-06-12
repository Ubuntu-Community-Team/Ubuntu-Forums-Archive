---
title: "Broken package isn't really broken"
date: 2012-01-31
forum: General Help
---

### Post by Ranko Kohime on 2012-01-31
Here's my situation in a nutshell: was running Xubuntu 11.04, 64-bit, with Guitar Pro 6 installed (this is a 32-bit-only app at the moment), and upgraded to 11.10 via the Update Manager.  It insisted on uninstalling GP6 in the process, and after the upgrade, I re-installed GP6.  dpkg gave an error on install, the Update Manager says there is an error, and to check Synaptic or apt-get, and both of these report that GP6 is broken, but don't say how.  However, GP6 starts up and runs just fine.

The only problem I'm having is that due to the "broken" package, Synaptic, apt-get and the Update Manager will not install programs or updates without forcing me to un-install GP6.  If I un-mark GP6, it then forces a list of changes that amounts to half of the packages on my system.  :confused:

I love when things break.  :D

Is there a way to force the package managers to recognize that GP6 is properly installed and working?

---

### Post by raja.genupula on 2012-01-31
If anything broken regarding packages we have the thing is 

**sudo apt-get install -f**

try that one in your terminal .

---

### Post by Ranko Kohime on 2012-01-31
> **raja.genupula said:**
> If anything broken regarding packages we have the thing is 

**sudo apt-get install -f**

try that one in your terminal .
That, unfortunately, asks me to install several dependencies which are already installed, and uninstall GP6.  (along with a dozen or so applications I use, such as Audacity, MuseScore, SeaHorse, Umit, and X.org, yes it wants to uninstall the X server.)  :-k

Like I said though, the GP6 package is not actually broken, the package managers just thinks that it is.  The program starts, and functions exactly as it should function.  I just can't install or update software.

---

### Post by ankspo71 on 2012-01-31
Hi,
```
sudo apt-get install -f
```
usually helps 90% of the time, but you can also use
```
sudo apt-get remove -f
```
which will remove broken packages if necessary.

You asked:
> Is there a way to force the package managers to recognize that GP6 is properly installed and working?

This might work:
Try going into Synaptic Package Manager and put a lock on the packagename for GP6. I'm hoping this should tell Synaptic to ignore GP6 and its dependencies when calculating the upgrades. So open Synaptic Package Manager, search for the packagename of GP6, select the package by highlighting it, then go to the menu, click on "Package", then click on "Lock Version". Next, click on the "Reload" button to refresh the repositories. Now you should be able to update your system using any package manager.



If all else fails.....  (technical stuff)

Here's a temporary workaround on this page: 
[http://journalxtra.com/linuxsanity/fixing-the-dreaded-errors-were-encountered-while-processing-errors-1495/](http://journalxtra.com/linuxsanity/fixing-the-dreaded-errors-were-encountered-while-processing-errors-1495/)
Then find the section that begins with:
> If you are still battling away after trying the above then you have no choice but to bring out your longsword and start swinging at dpkg's bowels 
then look over the following steps 1 through 9


I think it's also possible to use dpkg --set-selections to temporarily get past the problem until later.

To see the installed state of GP6:
```
dpkg --get-selections | grep GP6
```

Now to trick dpkg into thinking GP6 is correctly installed or removed, or tell it to hold the package. Use one of the following:

```
echo "gp6 install" | sudo dpkg --set-selections
echo "gp6 deinstall" | sudo dpkg --set-selections
echo "gp6 hold" | sudo dpkg --set-selections
```

Hope this helps.

---

### Post by Ranko Kohime on 2012-02-01
I used the directions on the page you directed me to, to edit the package list to reflect GP6 as being installed.  Thanks.  :D

---

