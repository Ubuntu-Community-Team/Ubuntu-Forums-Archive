---
title: "Backintime startup issue"
date: 2010-04-23
forum: General Help
---

### Post by Bridgestone24 on 2010-04-23
I've been attempting to use backintime for the last couple of days. I installed if by following the directions from this site:

[http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html](http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html)

> Setting up meld (1.3.0-2) ...

Setting up nautilus-actions (1.10.1-1) ...

Setting up backintime-common (0.9.26-3) ...

Setting up backintime-gnome (0.9.26-3) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dav@Dav:/usr$ Those are the last few lines- there are no errors of any sort. When i attempt to start or load the software by clicking on it via the applications/system tools icon a tab in the task bar pops-up which reads "starting Backintime" then it just disappears and nothing happens.

Any ideas on what to do? I've restarted and i've uninstalled and reinstalled and get the same result.  I'm running 9.10 glnx86 with an AMD 64 bit processor. I also have Grsync installed but i would like to experiment with backintime. 

Thanks in advance for the help!!

---

### Post by Bridgestone24 on 2010-04-25
Any ideas? Suggestions??

I tried running through terminal and received this message:
> dav@Dav:~$ backintime-gnome
Traceback (most recent call last):
  File "/usr/share/backintime/gnome/app.py", line 27, in <module>
    import pygtk
ImportError: No module named pygtk
dav@Dav:~$ 

   Does anyone know how to automate Grsync? I like how Time Machine does a backup every hour automatically. If i could find that or set up Grsync to do that it would be great. My hopes were that backintime would let me. 

Thanks for the help.

---

### Post by Bridgestone24 on 2010-04-25
I've been searching around for the last hour or so and discovered that pygtk is from the python package. I ran "sudo apt-get install python-gtk2" and it said it was up-to-date.

I followed another forum which suggested uninstalling and reinstalling python. I did so and then reinstalled my ubuntu-desktop which was uninstalled with python. 

After all that i reinstalled backintime and the same error as listed above appeared.

---

### Post by 2hot6ft2 on 2010-04-25
Don't you have it in your repos.?
[Back in Time click to install]("apt:backintime-gnome")
It's in mine but I run [Ubuntu Ultimate Edition]("http://www.ultimateeditionoz.com/downloads/") so I have more repos. I really don't know if it's in the standard repo. or not. I use it.

---

### Post by Bridgestone24 on 2010-04-25
Thanks for the reply. 

I used the install method from the first post a couple times then when searching the repos. I found backintime there and have been installing and uninstalling via package manager. I'm pretty sure the link above adds the backintime-common and gnome to the repos. list.

Still same error appears. I would really like to get this running.

---

### Post by 2hot6ft2 on 2010-04-25
You're welcome. Lets start with a clean slate.
```
sudo apt-get purge backintime-gnome
```
Are you familiar with adding PPA's?
If so here is the back in time ppa
[https://launchpad.net/~bit-team/+archive/testing](https://launchpad.net/~bit-team/+archive/testing)

If not say so and I can tell you how to do it.

---

### Post by 2hot6ft2 on 2010-04-25
It's so simple here it is. Each line is a separate command so run them one at a time. I could combine them but this is simple anyway.

```
sudo add-apt-repository ppa:bit-team/testing
sudo apt-get update
sudo apt-get install backintime-gnome
```
all done
Applications > System Tools > Back in Time

P.S. ubuntugeek is a good site but that was either for 8.10 or 9.04 since it was dated July 12, 2009

---

### Post by Bridgestone24 on 2010-04-25
Thanks for the help! hmm, I'm not familiar with that acronym. I do most work through the terminal but I'm still learning.

OKay...
 I purged backintime and then ran the three commands you listed. I tried to run backintime via the applications but still the same "starting backintime" then its killed.. I ran backintime-gnome via terminal and the same error appears. 

> dav@Dav:~$ backintime-gnome
Traceback (most recent call last):
  File "/usr/share/backintime/gnome/app.py", line 27, in <module>
    import pygtk
ImportError: No module named pygtk
I uninstalled, went into my sources.list and removed the le-web.org from the first time to make sure there wasn't a conflict with the install. I reinstalled and again got the same error.

---

### Post by 2hot6ft2 on 2010-04-25
Ok. Time to find pygtk 2.0 I guess. Back in a few.
This is going to sound stupid but do you have gmountiso installed?
The reason I ask is that it I found this "Gmountiso, a PyGTK GUI" and PyGTK is what it says it can't find.
Try installing it and see if it fixes the pygtk missing error
[gmountiso install link]("apt:gmountiso")

And see if gmountiso starts it will be in
Applications > System Tools > Gmount-iso
If gmount works then pygtk is not missing but backintime's not finding it.

---

### Post by Bridgestone24 on 2010-04-25
I was searching around too just now and ran "apt-cache search pygtk"

A large list with pygtk is printed including:
python-gtk-vnc - A VNC viewer widget for GTK+ (Python binding)
python-gtk2-dev - GTK+ bindings: devel files
python-gtk2-tutorial - tutorial for the GTK2 python library
**gmountiso** - This is Gmountiso, a PyGTK GUI to mount your cd images

and guess what- i run Gmount-iso and get this... 

> dav@Dav:~$ Gmount-iso
Traceback (most recent call last):
  File "/usr/bin/Gmount-iso", line 29, in <module>
    import gtk, gobject
ImportError: No module named gtk*becoming humorous* haha

 i ran "apt-cache search gtk"
python-galago-gtk - GTK+ widgets for the Galago presence library (Python interface)
python-galago-gtk-dev - Galago presence library (Python interface)


So then i just tried a random program that i know runs with pygtk , Rhythem Music Player, which also fails at startup.

---

### Post by 2hot6ft2 on 2010-04-25
Not only those but it looks like software center wont work either in that case. I keep ending up finding links to this thread.

Not sure how to approach this but it appears that it's not a problem with backintime per say but a larger problem.

This search is interesting now that we know it's not just one program: [ubuntu No module named pygtk]("http://www.google.com/search?q=ubuntu+No+module+named+pygtk&btnG=Search&hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&sa=2")
Now to find one that was solved.

Ahah,
```
sudo aptitude reinstall python-gobject
```
Found it here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1438507](http://www.uluga.ubuntuforums.org/showthread.php?t=1438507)

---

### Post by Bridgestone24 on 2010-04-25
working magic... brb

---

### Post by 2hot6ft2 on 2010-04-25
> **Bridgestone24 said:**
> working magic... brb
That's some slow magic...lol. Here's another thread with that issue that was solved.
[http://art.ubuntuforums.org/showthread.php?t=916419&page=3](http://art.ubuntuforums.org/showthread.php?t=916419&page=3)

---

### Post by Bridgestone24 on 2010-04-25
haha. No kidding. I went through and did a complete uninstall of backintime. I reinstalled python-gobject, I get the same error. Nothing that requires pygtk or gtk will run. I even tried running backintime vs backintime-gnome and i get "no module named bz2" which is related to tar files- no idea. 

still searching..

%%%%%%%% 
SOLVED: So after all that ridiculousness it was python all along. I went to the link in your last post and rename python to python-broken and backintime worked instantly. That is so ridiculous. Thank you SO much for all the help! that is a weird bug between 9.04 and 9.10, it seems it's happened to a number of people with various programs. 

Thank you!!

---

### Post by 2hot6ft2 on 2010-04-25
There doesn't seem to be a whole lot of info. on it considering how many things turn up in a google search. If you don't have it customized too much yet perhaps a re-install of ubuntu would be easier. Although I would like to find an answer for it.

What's funny is that you didn't even notice half the apps. didn't work.

---

### Post by 2hot6ft2 on 2010-04-25
There's a program I use to quickly backup home among other things here:
[http://www.quickstart.freeforums.org/quickstart-download-pics-t2.html](http://www.quickstart.freeforums.org/quickstart-download-pics-t2.html)

I have been using it for a couple years since it was created by a forum member mdpalow.

That way you can backup home and all your settings and restore them easily.
After an install it's the first thing I copy to my desktop and install to restore home. Before ever getting on the net. That way all my settings, bookmarks and all are still there.

---

### Post by 2hot6ft2 on 2010-04-25
> **Bridgestone24 said:**
> 
SOLVED: So after all that ridiculousness it was python all along. I went to the link in your last post and rename python to python-broken and backintime worked instantly. That is so ridiculous. Thank you SO much for all the help! that is a weird bug between 9.04 and 9.10, it seems it's happened to a number of people with various programs. 

Thank you!!
Awesome. Glad to hear it. now I know what to look for if I come across it again. And you're welcome.

---

### Post by Bridgestone24 on 2010-04-25
This machine is a work machine. I work in a research center and do a lot of various atmospheric modeling. This machine is immensely customized between the various modeling programs and such. I don't really do any besides work and all of those programs work well, wasn't until recently that i started messing with the others. My personal machine is a couple year old macbook which is going strong with no problems since day one *knock wood*.

---

### Post by 2hot6ft2 on 2010-04-25
I see. Not so easy to just re-install then. And all the more reason to want backintime.

---

### Post by Bridgestone24 on 2010-04-25
exactly- It works great. I see why everyone likes this program, It's super easy to use. I was just thinking the other day what would happen if my system were to crash then i went on a hunt for good backup software.

---

### Post by 2hot6ft2 on 2010-04-25
There are some bugs you may want to do a google search for
launchpad backintime
or
ubuntu backintime bug or bugs
The other app. I mentioned does a good job but for scheduling backups backintime is a better option.

---

### Post by 2hot6ft2 on 2010-04-25
Also if it's working good go to Synaptic find backintime select it and click on Packages > Lock version
That way it wont upgrade to one that may not work right.

---

