---
title: "Several problems with 11.04"
date: 2012-04-12
forum: General Help
---

### Post by brosville on 2012-04-12
I've been running 11.04 for some time, following a botched attempt to update to the latest version of Thunderbird using the terminal (I suspect I may have shut the computer down while "update" was running), I was left with a machine that refused to boot - the "repair boot" disc failed to fix things, so I bit the bullet and reinstalled 11.04, choosing the "save all my files" option.......
I now have a walking wounded version running - at first I thought I'd lost all my images and music files, but thankfully discovered them in "user", which is alongside a "new" version called "martin" in the "home" folder (which is full of empty folders)......
So my "to do list" is as follows - firstly, how do I get the new install to function using all the old files and folders in "user"?
How do I find all my old mail and address book from Thunderbird?
How do I get my monitor to work properly? (it's a 1440x900) - It wouldn't "find" the proper resolution, so I manually entered it in the Nvidia settings - it still gives me oval circles

When I've sorted those, it's moving the max/min buttons to the right, and getting rid of those daft hiding window sliders..........

---

### Post by SteveDee on 2012-04-15
> **brosville said:**
> ...how do I get the new install to function using all the old files and folders in "user"?
How do I find all my old mail and address book from Thunderbird?
..........

The /home/user folder will probably contain a number of hidden and regular folders (which in turn may contain hidden & regular files & folders).

Hidden folders & files have a leading "." (for example: /home/martin/.config).

The regular folders in your home generally contain the stuff you have created ( e.g. /home/martin/Documents/TaxReturn.odt). So most of your files can be copied over from /home/user to /home/martin although you may have to change file permissions to make them read/write by the user named "martin".

Only re-use the hidden folders/files that contain your data.

Your Thunderbird stuff will be in /home/user/.thunderbird
From memory you just need to copy the folder with the random name (e.g. ysb18h3.default) to /home/martin/.thunderbird, sort out file permissions, and then run Profile Manager from a terminal:-
```

/usr/lib/thunderbird/thunderbird -P

```
Give profile a name (e.g. “martin”)
Browse to select folder;  /home/martin/.thunderbird/{ysb18h3.default}

From Thunderbird you should now be able to see mail & addresses. If it does work you may find it useful to copy your email stuff into a new location, to make it easier to backup and restore, should you decide to wipe your disk in the future.
Example:-
Create a new folder: /home/martin/.tbird
Copy your profile folder {ysb18h3.default or whatever} to this new folder then rename:-
 /home/martin/.tbird/profile
Now run the Thunderbird Profile Manager as above.
Remember to include /home/martin/.tbird in your backups.

---

### Post by na5h on 2012-04-15
11.04 is obsolete...I would recommend waiting for the final release of 12.04 to come out at the end of this month, then try it out and see if the problems are still there. 

12.04 is the next Long Term Support Release and will be supported until April 2017 (the support for 11.04 will run out in October this year).

Remember to ALWAYS make a backup before upgrading...

---

### Post by marinara on 2012-04-15
this might help you with the screen res problem
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

