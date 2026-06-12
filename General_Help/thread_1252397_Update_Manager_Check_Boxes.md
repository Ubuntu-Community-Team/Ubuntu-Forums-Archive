---
title: "Update Manager Check Boxes"
date: 2009-08-28
forum: General Help
---

### Post by greenco on 2009-08-28
Is there an easy way to remove the " CHECK MARKS " out of the Update Manager's window? I have stopped letting it install all of the new updates and I am selecting the ones I want to install. I just unmarked 76 updates and kept 6 to be installed. I hope that there is an easier way to do this.
Thanks

---

### Post by zvacet on 2009-08-29
In synaptic find package you don´t want to update and mark it>p**ackage tab>lock version.**

---

### Post by greenco on 2009-08-29
Thanks zvacet, I am not sure what you are refering to. I have opened "Synaptic Manager" and tried to find the feature you mentioned, but I can;t find it. From the sound of it, this method sounds as bad as unchecking the boxes.

---

### Post by ks07 on 2009-08-29
> **greenco said:**
> Thanks zvacet, I am not sure what you are refering to. I have opened "Synaptic Manager" and tried to find the feature you mentioned, but I can;t find it. From the sound of it, this method sounds as bad as unchecking the boxes.
You need to open up synaptic and go to the 'Installed (Upgradeable)' section in the status view on the left hand side to show anything with available updates. Then go down the list that appears highlighting anything you don't want to update with ctrl+click. Then at the top menu bar, choose package > lock version.

---

### Post by 3rdalbum on 2009-08-29
In Synaptic, find the package you don't want to update. Click it, go to the Package menu in the menubar, and come down to Lock Version.

This potentially causes problems with dependency resolution, because it prevents Apt from working out a solution to a dependency problem that involves upgrading that package.

The best solution is to apply all updates.

The second-best solution is to use Synaptic to look at updates, rather than Update Manager. Click the "Status" button and then "Installed (Upgradable)" in the left pane.

---

### Post by greenco on 2009-08-29
Thanks for the replies and as a rule the updates have worked well. The reason I posted this was because there have been times when Ubuntu has changed file names or placed them in a different folder and then my installed apps would fail to start. I would have to spend several hours on Google to find out how to fix the problems. I just wanted a quick way to remove all of the check marks, so that I could select just the ones that I wanted. The updates for Firefox, Thunderbird, K3b, Brasero, Movie Player and etc. are good and I have no problem with those updates. The updates for Python, Library files, Java and etc. are the ones that I am worried about. Again, Thanks for your inputs!!!

---

