---
title: "Do I need to Reinstall Ubuntu"
date: 2009-07-05
forum: General Help
---

### Post by H4F on 2009-07-05
Do I ever need to reinstall Ubuntu like windows.

I thinking that my ubuntu becomes a bit slow and overloaded with tons of my experiments. 
I have messed up with all thinks that I could .
I have installed many app from repos
....
...

Now. Is there a way to make my ubuntu brand new without reinstall from cd and without loosing data.

---

### Post by ugm6hr on 2009-07-05
You do not need to reinstall, especially because of this:

> I thinking that my ubuntu becomes a bit slow and overloaded with tons of my experiments.

As for these...
> I have messed up with all thinks that I could .
I have installed many app from repos

You could undo all the things you have messed with, but it is often faster to just reinstall.

> Now. Is there a way to make my ubuntu brand new without reinstall from cd and without loosing data. 

Not without undoing everything you have done manually.

The simplest way to achieve this is to backup your /home directory, reinstall, and then copy back your files (i.e. not the entire directory, since that would reinstate some of your previous settings).

If you think this may be a problem in the future again, invest a little time now to create a separate /home partition.  This will allow you to recover again in the future very easily.

---

### Post by H4F on 2009-07-05
> **ugm6hr said:**
> 
The simplest way to achieve this is to backup your /home directory, reinstall, and then copy back your files (i.e. not the entire directory, since that would reinstate some of your previous settings).


but what about all programs which I have installed. nearly all of them have .folder in my home directory. and there is lots of space used by those .folders

---

### Post by tripolitan on 2009-07-05
remove .folders for packages that you have uninstalled and no longer need. If you use Synaptic to uninstall, always mark packages for complete removal. Install deborphan, a recommended package for Synaptic, it will enable Synaptic to remove all libraries and packages that are no longer needed. Once deborphan is installed, you can also run sudo orphaner to get rid of libraries that are no longer in use (orphaned), if they haven't been removed by Synaptic already.

---

### Post by ivanvajar on 2009-07-05
You don't backup entire /home directory. You need to backup files, not entire /home. If you restore entire /home, it will bring back some of your previous system settings.

---

### Post by H4F on 2009-07-05
> **ivanvajar said:**
> If you restore entire /home, it will bring back some of your previous system settings.
Is there a way to restore all settings to there Defaults.
Mostly i think thats the problem. all my settings are messed now I think.

---

### Post by tripolitan on 2009-07-05
removing .folder will reset the settings for that program. What EXACTLY do you think is messed up in your PC?

---

### Post by H4F on 2009-07-05
I have compiled many application from source.and some debs from web
I think that there are many libraries and stuff which is not required.
I have compiled from source alsa. but still my microphone is not working.

i am thinking reinstall may fix my problem with microphone

---

### Post by ivanvajar on 2009-07-05
Sometimes, it is faster to reinstall. Anyway, just backup files you need to save. You can do clean installation and restore files after it. You'll need to install programs again, but that's not allways a bad thing ;-)

---

### Post by ugm6hr on 2009-07-05
> **H4F said:**
> but what about all programs which I have installed. nearly all of them have .folder in my home directory. and there is lots of space used by those .folders

Just copy back all the non-hidden files and directories.

Anything that starts with a . is a hidden file or directory.

All program / desktop settings etc are stored in those directories, as you say.

---

### Post by tripolitan on 2009-07-05
Compiled from source? now you tell me! I think that after you re-install (whatever version you're using) you should run synaptic with deborphan in the future anyway, just to be sure...I have used all kinds of linux versions on various types of PCs and laptops for the past 10 years and never had to compile anything from source, I suggest you avoid compiling anything from source but in those very very very rare cases, you should find out what and where the files are deposited on your computer (/usr/local/lib/something).

If there is a problem with your Microphone, compiling alsa from source will not fix it.

---

### Post by ivanvajar on 2009-07-05
You only need to backup files from /home. Copy what you see in your /home. You don't need **.files**
Those are hidden and you don't need them on a fresh install.

---

