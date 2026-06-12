---
title: "cleaning-deleting unnecessary files"
date: 2009-07-02
forum: General Help
---

### Post by tjk on 2009-07-02
There seems to be a lack of cleanup apps for Linux.

I have been running Linux (and upgrading versions) for several years now.  Basically I have my system configured just the way I like it, and I'm not willing to do a clean install because it would take months to reinstall and reconfigure everything the way I like it.

But...  I need to clean my system of unnecessary files.  For instance, I know that I have installed apps that I haven't used in months or even years -- but as far as I know there is no way to find out which apps these are, so I can remove them.  As well, I know that I have a huge number of duplicate music and photos files, but I have not found an app that can efficiently handle this situation (there's plenty of options for handling small amts of duplicates, but my system freezes with all the duplicate finders included with apps.)  Yes, I've tried commandline alternatives, but they are limited in their abilities.  I like to view and compare the duplicates visually before making any deletions.  I have found many programs for Windows that accomplish these tasks, why doesn't Linux have the same?  If you are aware of something to accomplish this, let me know, please!

---

### Post by wojox on 2009-07-02
I use BleachBit.
It works rather nice.

---

### Post by tjk on 2009-07-02
> **wojox said:**
> I use BleachBit.
It works rather nice.
  
I think BleachBit is a wonderful app and I use it from time to time.  **But does it uninstall unused apps or delete duplicate files **(read the details of my initial post)**?**  I didn't find these features....  it would be nice if it did...

---

### Post by abhi_69 on 2009-07-02
if u r in KDE, may be ***sweeper*** can be a good solution for u. it cleanup all unneeded files & junk from ur disk & free-up space. it is much similar to CCleaner of windows.
in ubuntu, terminal tools like-
[B][I]apt-get autoremove
apt-get autoclean
apt-get clean
aptitude clean[/I][/B]
can help in some how. ***Ubuntu tweak*** software can also clean unneeded packages & cache to free disk space.
***computer janitor*** in ubuntu also helps in certain cases.
u don't need to worry about disk cleanup in linux like windows. becoz, unlike windows, it can't effect largely in ur system speed.

---

### Post by donkyhotay on 2009-07-02
I generally run
```

sudo apt-get autoremove
sudo apt-get autoclean

```
a couple times per week and that seems to get rid of the worst of the stuff taking up space. I also use gtkorphan (it's in the repos) from time to time but you have to be careful as gtkorphan will sometimes accidently take out good stuff too. Just pay attention to what it recommends removing and if something doesn't work after using it then reinstall whatever was removed and do a little research in what it wants to remove next time.

---

### Post by abhi_69 on 2009-07-02
> **wojox said:**
> I use BleachBit.
It works rather nice.
i never hear before about Bleachbit. after hearing from u first, i try it out.....its cool!!!!!!!!!
i am looking for something like this  for my ubuntu 9.04 for long time, becoz i can't use sweeper (i don't hav KDE).
i think its a good choice as a cleaner.

---

### Post by oldos2er on 2009-07-02
I use fslint mainly for finding duplicate files, but it does more than that. It can find bad symlinks, empty directories, etc.

---

### Post by tjk on 2009-07-02
> **oldos2er said:**
> I use fslint mainly for finding duplicate files, but it does more than that. It can find bad symlinks, empty directories, etc.

Correct me if I'm wrong, but fslint doesn't allow you the control -- to scroll through a list of duplicates to make the final selection for deletion?  Nor does it allow me to view the selected photos before I delete them...

---

### Post by wojox on 2009-07-02
fslint's powerful.
It hosed my .conf files.

---

### Post by tjk on 2009-07-02
> **donkyhotay said:**
> I generally run
```

sudo apt-get autoremove
sudo apt-get autoclean

```a couple times per week and that seems to get rid of the worst of the stuff taking up space.
I use these commands, but I disagree that it gets rid of the worst stuff.  I estimate that I have several gigabytes of duplicate and unused apps on my harddrive.
 > I also use gtkorphan (it's in the repos) from time to time but you have to be careful as gtkorphan will sometimes accidently take out good stuff too. Just pay attention to what it recommends removing and if something doesn't work after using it then reinstall whatever was removed and do a little research in what it wants to remove next time.I forgot about gtkorphan, and will use it again.  But this app still doesn't do what I'm wanting... search for unused apps (and duplicate photos-music files)

---

### Post by tjk on 2009-07-02
> **wojox said:**
> fslint's powerful.
It hosed my .conf files.

I agree with you!  It scares me!!  I would feel better if someone made a GUI for it and allowed you to verify all the files before it deleted them.

---

### Post by wojox on 2009-07-02
To get rid of unused app's go to

Applications > Add/Remove

---

### Post by ericab on 2009-07-02
can bleachbit be run on a CLI type ubuntu or does it require Gnome ?

---

### Post by tjk on 2009-07-02
> **wojox said:**
> To get rid of unused app's go to

Applications > Add/Remove

Ya right! lol 
I looked up how many apps I have installed... over 3700!!!  I'm not going to flip through all of them... that's why I would like an app to monitor which ones I don't use.  Besides, I don't have a clue what most of the app names represent (or if I use them).

---

### Post by tjk on 2009-07-02
> **ericab said:**
> can bleachbit be run on a CLI type ubuntu or does it require Gnome ?

I found this on the BeachBit site:[INDENT]**Update**: [BleachBit 0.5.0 released with support for Microsoft Windows]("http://bleachbit.blogspot.com/2009/05/bleachbit-050-released.html").
The new thread-free code also paves the way to implement a command-line interface (CLI) one day.
[/INDENT]It was dated May 11, 2009.  So if it hasn't been implemented, it may be soon.
You could also google for an answer... or check out the BeachBit forum: [http://bleachbit-project.appspot.com/forum/](http://bleachbit-project.appspot.com/forum/)

---

### Post by wojox on 2009-07-02
It'll run on gnome.

Go here  [http://bleachbit-project.appspot.com/download/](http://bleachbit-project.appspot.com/download/)

Download whatever version .deb then just click on it and it will install.

Good question app monitior?

---

### Post by ericab on 2009-07-02
> **tjk said:**
> I found this on the BeachBit site:[INDENT]**Update**: [BleachBit 0.5.0 released with support for Microsoft Windows]("http://bleachbit.blogspot.com/2009/05/bleachbit-050-released.html").
The new thread-free code also paves the way to implement a command-line interface (CLI) one day.
[/INDENT]It was dated May 11, 2009.  So if it hasn't been implemented, it may be soon.
You could also google for an answer... or check out the BeachBit forum: [http://bleachbit-project.appspot.com/forum/](http://bleachbit-project.appspot.com/forum/)

thanks, i hadnt seen that

---

### Post by TheForumTroll on 2009-07-02
> **tjk said:**
> Ya right! lol 
I looked up how many apps I have installed... over 3700!!!  I'm not going to flip through all of them... that's why I would like an app to monitor which ones I don't use.  Besides, I don't have a clue what most of the app names represent (or if I use them).

Really? You installed 3700 apps you don't know what is?
Well, maybe that'll teach you to keep your house clean on a day to day basis ):P

---

### Post by oldos2er on 2009-07-02
> **tjk said:**
> Correct me if I'm wrong, but fslint doesn't allow you the control -- to scroll through a list of duplicates to make the final selection for deletion? 

 Yes, it does.

---

### Post by donkyhotay on 2009-07-04
> **tjk said:**
> I use these commands, but I disagree that it gets rid of the worst stuff.  I estimate that I have several gigabytes of duplicate and unused apps on my harddrive.
 I forgot about gtkorphan, and will use it again.  But this app still doesn't do what I'm wanting... search for unused apps (and duplicate photos-music files)

Didn't know you were talking about apps and stuff, I'm careful about removing apps through synaptic if I don't need them. I don't have many photo/music so that isn't an issue as well. The main thing I worry about is the installation files and packages that get lost in the system.

---

### Post by oldos2er on 2009-07-04
> **tjk said:**
> I agree with you!  It scars me!!  I would feel better if someone made a GUI for it and allowed you to verify all the files before it deleted them.

 fslint is a GUI program.

---

### Post by tjk on 2009-07-08
> **oldos2er said:**
> fslint is a GUI program.

My bad.  Don't know what I was thinking.  I have tried this app a while ago, but I will give it another try as it seems to have a few useful features.  It appears it hasn't been updated in a while... too bad, since it has some potential.

---

### Post by doas777 on 2009-07-08
the part I want to deal with, are all the 'dot' directories in my /home. some of them are seriously from my feisty build. I guess sorting by access might work, but it would be nice if a script could inform me of all the 'dot' dirs that are for applications that are not currently installed.

---

### Post by Andrew.Z on 2009-09-16
> **ericab said:**
> can bleachbit be run on a CLI type ubuntu or does it require Gnome ?

[BleachBit 0.6.4 adds command line support](http://bleachbit.sourceforge.net/news/bleachbit-064-released), so you can use either CLI or GTK+.  The GTK+ works fine in GNOME, KDE, XFCE, etc.

---

