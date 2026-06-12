---
title: "Cannot update ubuntu 12.04"
date: 2012-09-11
forum: General Help
---

### Post by *^kyfds( on 2012-09-11
i'm running a fresh install of ubuntu 12.04 through wubi, and i've had this problem for about a week now (i'm not sure whether i've run the update manager on this machine successfully yet).

The update manager refreshes the list of updates normally, like it always has, but as soon as it starts downloading these updates i get a connection error (failed to fetch X file, file not found)


it's quite a number of updates (around 400).

My bt home hub has run updates through other machines in the past, so i know my network connection is fine.

any help would be appreciated,

thehumorouscheese.

---

### Post by critin on 2012-09-11
> The update manager refreshes the list of updates normally, like it  always has, but as soon as it starts downloading these updates i get a  connection error (failed to fetch X file, file not found)The update notifier is still up on the top menu if there are still updates to run.  Right click on it and choose 'Show Updates'.   Go to 'Settings' at the bottom and  then 'Other Software Sources'--find the PPA for the files that failed.  Remove the check from the box(s).  Uncheck the box on the download page too.  Then run update and it should work.

You'll want to check later for why that one  didn't work.  Perhaps reinstall that PPA.

---

### Post by cortman on 2012-09-11
I'd check /etc/apt/apt.conf to make sure there are't any configuration lines that would mess it up.

---

### Post by Frogs Hair on 2012-09-11
Removing a source from software sources won't allow the application from that source to update . After  you have installed the other updates add the source again and run check for updates and see if source is still causing problems.

---

### Post by *^kyfds( on 2012-09-15
> **Frogs Hair said:**
> Removing a source from software sources won't allow the application from that source to update . After  you have installed the other updates add the source again and run check for updates and see if source is still causing problems.

There are 406 updates.

i've already spent about 5 minutes checking boxes, and i'm just about half way.

(laaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaag.)

---

