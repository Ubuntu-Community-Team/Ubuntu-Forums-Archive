---
title: "Ubuntu Software Center does not have a &quot;Check for updates&quot; button"
date: 2012-01-09
forum: General Help
---

### Post by trafo23 on 2012-01-09
Ubuntu 11.10, how can there not be such a button?

Thanks

---

### Post by misfitpierce on 2012-01-09
I don't understand exactly what your looking for? Check for updates as in look for updates for apps you have installed? 

If thats the case then linux uses an integrated update system through update manager for all apps installed via the software center through repositories. So if you open update manager and a newer version is avail from the repo it will show you and prompt you to update unless you have it set to auto install updates at which point it will just install them for you.

---

### Post by Mark Phelps on 2012-01-09
The Software Center serves as a front-end to the repositories (repos) you have configured with your setup.  The repos tend to be Ubuntu version-specific.

What this means, for example ...

Let's say you're running Ubuntu 11.10 and using an app from a repo version 5.6.  Then, Ubuntu 12.04 comes out and the app version in that repo is 5.7.  Will the Software Center on your PC see this "update"?

The answer is NO.  Because the repo version for Ubuntu 11.10 will not be updated with the app version for 12.04.

When version upgrades get loaded into a repo, your Update Manager will see that (when it does a check) and notify you that an upgrade is available. But, the Oneiric repos will not reflect changes made to the Precise repos for 12.04.  Thus, you will get no updates for apps versions associated with Ubuntu 12.04.

---

### Post by MartijnNL on 2012-01-09
Perhaps the OP just means that Synaptic (and apt-get) have ways to update the database of available packages (reload button/apt-get update) and the Software Center hasn't? (I don't use the Software Center so can't tell myself.)

---

### Post by pretty_whistle on 2012-01-09
> **trafo23 said:**
> Ubuntu 11.10, how can there not be such a button?

Thanks
I agree.  You think there'd be one since updated versions of programs exist.  Synaptic has it but I can't get it to work.

---

### Post by Ignus Fatum on 2012-01-09
I have no idea since I hardly ever use the software center but you can manually check for and install updates trough the terminal with the following commands:

apt-get update – refresh available updates
apt-get upgrade – upgrade all packages
apt-get dist-upgrade – upgrade with package replacements; upgrade Ubuntu version
apt-get install pkg – install pkg
apt-get purge pkg – uninstall pkg
apt-get autoremove – remove obsolete packages
apt-get -f install – try to fix broken packages

---

### Post by Double.J on 2012-01-09
> **Ignus Fatum said:**
> I have no idea since I hardly ever use the software center but you can manually check for and install updates trough the terminal with the following commands:

apt-get update – refresh available updates
apt-get upgrade – upgrade all packages
apt-get dist-upgrade – upgrade with package replacements; upgrade Ubuntu version
apt-get install pkg – install pkg
apt-get purge pkg – uninstall pkg
apt-get autoremove – remove obsolete packages
apt-get -f install – try to fix broken packages

don't forget apt-cache search! ;)

---

### Post by trafo23 on 2012-01-09
> **misfitpierce said:**
> I don't understand exactly what your looking for? Check for updates as in look for updates for apps you have installed? 

If thats the case then linux uses an integrated update system through update manager for all apps installed via the software center through repositories. So if you open update manager and a newer version is avail from the repo it will show you and prompt you to update unless you have it set to auto install updates at which point it will just install them for you.

Yes, Check for updates as in update ubuntu and look for updates for apps i have installed.

Some time ago a window appeared that suggested that some programs can be updated but i did not have time for that and pressed cancel.

Now i want to press a button that checks for updates and displays me the same window. I know the apt-get way to do it, its just strange that there is not a button for that.

What is the purpose of Software Center if there is Synaptic?

---

### Post by pretty_whistle on 2012-01-09
> **trafo23 said:**
> Yes, Check for updates as in update ubuntu and look for updates for apps i have installed.

Some time ago a window appeared that suggested that some programs can be updated but i did not have time for that and pressed cancel.

Now i want to press a button that checks for updates and displays me the same window. I know the apt-get way to do it, its just strange that there is not a button for that.

What is the purpose of Software Center if there is Synaptic?
What's the purpose of Software Center if there is Synaptic?

The user ratings.  Synaptic doesn't provide this.

---

### Post by mcduck on 2012-01-09
> **trafo23 said:**
> Yes, Check for updates as in update ubuntu and look for updates for apps i have installed.

Some time ago a window appeared that suggested that some programs can be updated but i did not have time for that and pressed cancel.

Now i want to press a button that checks for updates and displays me the same window. I know the apt-get way to do it, its just strange that there is not a button for that.
Just start the Update Manager from Dash, or use the System menu in top right screen corner (the menu should have a message about update status, clicking that opens the Update Manager)

> **trafo23 said:**
> What is the purpose of Software Center if there is Synaptic?Easier installation of popular graphical applications (Synaptic's user interface is less friendly to non-technical users, and it lists all the available packages, including all kinds of technical stuff a typical desktop user probably does never need to know about...)

---

### Post by spacecheck on 2012-01-09
> **trafo23 said:**
> Ubuntu 11.10, how can there not be such a button?

Thanks
There IS a "Check" (for updates) button, but it isn't in "Ubuntu Software Center", which is a method and place where software can be researched and installed (and purchased).

The button you seek is found in the Update Manager. Just type "update m" into the search line of the application menu and then click on the "Update Manager" icon that appears.

You can either push the "Check" button or type Alt+k to search for the latest updates (even if some are already visible).

If that answers your question properly, thus solving the problem, please remember to use the thread tool to mark the item as [Solved].

Good luck!

---

