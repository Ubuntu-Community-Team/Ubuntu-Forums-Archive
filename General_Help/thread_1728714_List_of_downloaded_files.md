---
title: "List of downloaded files"
date: 2011-04-14
forum: General Help
---

### Post by Jeff Root on 2011-04-14
Maverick Meerkat 64-bit
 
A box comes up when I download a file or save an image.
Some time ago I disabled the saving of the data displayed
in that box.  Now I want to re-enable it.  How?
 
   -- Jeff, in Minneapolis

---

### Post by spikoley on 2011-04-14
It sounds like you are using Firefox.  Try looking under Edit then Preferences.

---

### Post by An Sanct on 2011-04-14
In firefox the keys Ctrl+Shift+Y pop up the downloads windows too.

In the menu look under Edit->Preferences, General tab in the "downloads" section.

---

### Post by Jeff Root on 2011-04-14
Thank you.  That appears to be the help I needed.  I didn't find
a setting in Firefox Preferences, but I looked in "about:config" and
found "browser.download.manager.retention".  Changing the value
from 0 to 1 did it.
 
I actually want to keep track of files downloaded by Synaptic
Package Manager, not Firefox, so I'll have to test to be sure
the change I made in Firefox also works outside of Firefox.
 
   -- Jeff, in Minneapolis

---

### Post by plucky on 2011-04-14
> I actually want to keep track of files downloaded by Synaptic
Package Manager, not Firefox, so I'll have to test to be sure
the change I made in Firefox also works outside of Firefox.


It won't

In Maverick, Ubuntu Software Centre keeps a "History" list of packages and updates that are installed on your system.

---

### Post by An Sanct on 2011-04-14
In synaptic under status (a button bottom-left), you get a list on the left, if you click on "installed", you get all the packages, that are installed.

selecting any package and selecting properties with the right click, brings you the deatils: Info/dependencies/installed files/version/description

there you can see the files installed ... but to list all would mean something like 140.000 entries on a somehow clean system :}

dpkg also knows all the packages, that are installed .. maybe you are looking for that?
```
dpkg -l
```

PS. Im sure, there is a better way :) anyone ? :)

---

### Post by Jeff Root on 2011-04-14
Before I started this thread, I nearly asked a completely
different question regarding the same problem.  But I realized
that I was being lazy-- What I should do is re-enable the list
of downloaded files, since it would tell me where my downloaded
files are at.
 
But I just downloaded a file with Synaptic, and-- as plucky
predicted-- the Download window did not even open, much less
tell me the file location.
 
So back to my original question:
 
At least as recently as March 25, I downloaded a set of
packages, I think with Synaptic, and saved them on another
internal drive for later installation.  No problem.
 
Yesterday I used Synaptic Package Manager to download two
small packages.  I checked the box that says to download only,
not install.  It didn't give me a dialog to specify the location
in which to save the files.  I watched the files download.
I looked at all the info Synaptic provides on the packages.
Quite a lot, but no hint of where they were saved.  I looked
in the system's "Downloads" folder-- It is empty.  I did a
file search.  It did not find the downloaded files.
 
Where are they?
 
(Should this question be in a new thread?)
 
   -- Jeff, in Minneapolis
 
.

---

### Post by plucky on 2011-04-14
> Yesterday I used Synaptic Package Manager to download two
small packages. I checked the box that says to download only,
not install. It didn't give me a dialog to specify the location
in which to save the files. I watched the files download.
I looked at all the info Synaptic provides on the packages.
Quite a lot, but no hint of where they were saved. I looked
in the system's "Downloads" folder-- It is empty. I did a
file search. It did not find the downloaded files.

Where are they?

**/var/cache/apt/archives**  is where SPM downloads the .deb files.

Open a terminal and ```
cd /var/cache/apt/archives
ls -l
```

Good Luck

---

### Post by d3v1150m471c on 2011-04-14
```

dpkg --get-selections | grep  -i install

```

That should list every package installed on your system.

---

