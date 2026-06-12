---
title: "Nautilus Actions 3.0.5 in Natty missing several addons in context menu"
date: 2011-04-30
forum: General Help
---

### Post by inameiname on 2011-04-30
Upon a fresh installation of Ubuntu Natty, I have noticed only a couple of my nautilus-actions are actually showing up in the context menu. On further review, I noticed Nautilus-actions has changed a lot, and I cannot seem to figure out why most of my actions are not showing up. It seems no matter what I change, they will not show up.

Some of the ones I cannot seem to get up are 'Wipe' commands and several of my homemade ones that worked flawlessly in past Ubuntu versions, such as Chown, Make Executable, Renamer, among others.

Oddly, two of them work just fine, Search Here and Open Root Nautilus. I am not sure why these work, while the others do not, other than they are not used by selecting item(s)/folders.

Also, I noticed there is a change with the parameters, in which now all of them use %F instead of %M. Does anybody know why that is, and/or does it really matter.

FYI, I am using the classic version, not Unity as my desktop.

---

### Post by inameiname on 2011-04-30
I managed to 'fix' this by adding every single nautilus-action by hand. For some reason the ones that I exported from Maverick, while they showed up in the nautilus-actions configuration tool, they just were not showing up in nautilus.

So, while this is not really a fix, as I do not know why they were not showing up from those I imported, they show up now after putting them all in by hand.

I would mark this as solved, but unfortunately, while they do show up, they do not work. Restarting does not help. :(


UPDATE:

I figured out that '%F' instead of the previously used '%M' works, but not for folders/filenames with spaces. Therefore, this is still flawed as compared to previous versions of nautilus-actions.

---

### Post by xwindowsfan on 2011-05-01
i can confirm wipe and shred does not work with nautilus actions 3.0.5 after upgrading to ubuntu 11.04. even after manually re-adding the actions.

i resorted to installing a .deb for nautilus actions 2.3. I could not find any .deb for nautilus actions 2.9x and up. 2.3 works just as the previous 2.9 version with less options.

i have two actions seup for shred. one for 7 passes and one for 35 passes. just use different lables. with the parameter -n 7 or -n 35.

---

### Post by mc4man on 2011-05-01
Been fooling around a bit with the newer NA, (actually used also in maverick
While some of it is still a mystery and some things can cause issues (using a capability of 'Owner' is a no go here), if you didn't figure out yet - for spaces in filename or path use a %U in parameters

---

### Post by henriquemaia on 2011-05-01
I've bumped into this spaces on the filenames problem too. NACT seems overly complicated to get going and most of my previous actions aren't running. :(

---

### Post by henriquemaia on 2011-05-01
Well, I solved the problem by reverting to the old Maverick version.

The steps: 

```
sudo apt-get purge nautilus-actions
```

I then downloaded the old deb from here (choose the appropriate mirror):
[http://packages.ubuntu.com/maverick/i386/nautilus-actions/download](http://packages.ubuntu.com/maverick/i386/nautilus-actions/download)

then:

```
sudo dpkg -i /path/to/nautilus-actions_2.30.2-1_i386.deb
```

Now open synaptic to lock down the version of nautilus-actions in order to avoid updating it to the new one on your next upgrade:

```
sudo synaptic
```
(or use the menu)

On synaptic, look for nautilus-actions, select the package and go to the menu Package > Lock Version.

And you're done.

---

### Post by inameiname on 2011-05-04
Sad, sad, sad. I use nautilus-actions all the time and its a shame the latest version has so many bugs. 

Why they even released this version I do not know. If anybody else looked at the help guide for nautilus-actions, you will see they mention several issues with it. My question is if it is that problematic, why even update it?

Anyway, thanks for the tips. It seems the best solution for now is to purge the new version and install 2.3. Ah well.


FYI, I tried %U in place of %F and it still does not work.

---

### Post by mc4man on 2011-05-04
> **inameiname said:**
> 
FYI, I tried %U in place of %F and it still does not work.The %U works fine here when there are spaces in path and or file name. (used in parameters

Overall the new NA seems  bit overdone, though I guess there are those that find some new 'features' useful
(I only use Execution, Basenames and Mimetypes here

---

### Post by inameiname on 2011-05-04
So under parameters all you use is "%U"? And that is in replace of "%F"? 


Strange it doesn't work on my end then. I've tried refreshing nautilus as well as restarting and it still does not work. 

Regardless, filenames with spaces aside, several of the nautilus-actions do not always work anyway.

---

### Post by mc4man on 2011-05-04
> **inameiname said:**
> So under parameters all you use is "%U"? And that is in replace of "%F"? 
Generally I put any command options and %U in parameters

> **inameiname said:**
> 
Strange it doesn't work on my end then. I've tried refreshing nautilus as well as restarting and it still does not work. 
Possibly it's just specific to that action or couple of?
> **inameiname said:**
> 
Regardless, filenames with spaces aside, several of the nautilus-actions do not always work anyway.
That's for sure - and some I don't even have the slightest idea what they're for, working or not
The older version seems better for typical NA's

I thought I could make use of  the owner or not in Capabilities - that does bad things to nautilus here (or maybe I'm entirely misunderstanding the use of

---

### Post by inameiname on 2011-05-04
Okay, thanks for the tips, Mc4man.

It doesn't work for several of my nautilus actions.

The following do not work, nor always show up in the context menu: Chown me and Chown root, Make executable, Print, Renamer, Wipe, & Wipe (Quick Mode). Ones that do seem to work are: Open-Root-Nautilus and Search Here. Seems like the ones that specifically perform a function on whatever is selected are those nautilus-actions that are not functioning in Natty, but those that simply open something, no matter what is selected, works.

---

### Post by mc4man on 2011-05-04
Taking a guess at the 'make executable' it would seem that if there is a space in path or filename it won't work. If there isn't then %f works fine
'%f' does nothing except look good in the example text

---

### Post by inameiname on 2011-05-04
The 'Make Executable' is as follows:

Path: gnome-terminal
Parameters: -x sudo chmod +x %F
Working Directory: %d

This works just fine with files without spaces, but not with. 

Also, regardless of whether or not there is spaces in the filename, this nautilus-action won't even show up in the context menu if I have selected more than one file. In previous versions, it did, and worked as desired.

---

### Post by mc4man on 2011-05-04
> regardless of whether or not there is spaces in the filename, this nautilus-action won't even show up in the context menu if I have selected more than one file. In previous versions, it did, and worked as desired.
Now that does work here, multiple files aren't an issue, just spaces if trying to run a command on (vs. opening which is good with %U

---

### Post by inameiname on 2011-05-05
Hmmmm, could you possibly do me a favor and export those working nautilus-actions you have and tar them or something into a compressed file and post them on here? Just so I know for sure that it isn't something I am doing. 

I am sure you know how, but if not, its as easy as opening Nautilus-Actions Configuration Tool, going to Tools-> Export Adsistant, and exporting them.

In the past versions of nautilus-actions, there was the option to select it to work with folders, files, or both, and here, it is a little different. As such, I did not mess with the Basenames, Mimetypes, Folders, tabs as I did not know how they work. Maybe that causes trouble leaving them at default, I do not know.

---

### Post by mc4man on 2011-05-05
I can though for the most part they all are for opening which we've seen works.

As far as the make exec - I've no need for use as sudo, though did try your command. 
A non sudo version seems useful here - set up to be  seen on shellscripts and .exe's only

---

### Post by inameiname on 2011-05-05
Yep, it comes in very handy to me, especially for the many scripts I may happen to download or make on any given day. Well, at least it used to be. I used to just highlight all of them that I want and click "Make Executable" and voila, everything was made executable. It even worked through folders, so technically, by right-clicking the main folder (such as ~/.gnome2/nautilus-scripts), it would make executable all the files inside.

Anyway, I decided to just install Maverick's version of Nautilus Actions and be done with it. It would just fine on Maverick, and I do not really feel like figuring out all that needs to be altered for the latest to work with Natty. At least until they update it. The only real added burden I had to do was to make sure to put a hold on that package to avoid it updating, which was not a big deal. It is funny how with the 2.3 version %M suffices for all, instead of %F or %W. I do not know why, but whatever.

---

### Post by inameiname on 2011-06-18
My decision to downgrade to Maverick's version of Nautilus-Actions has worked fine for a while now, so while the issue really isn't solved, but 'fixed', I'll mark this as solved.

---

