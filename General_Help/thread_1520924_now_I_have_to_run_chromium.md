---
title: "now I have to run chromium"
date: 2010-06-30
forum: General Help
---

### Post by MacHaddock on 2010-06-30
So I installed the updates for firefox and now when I try and start it it goes right into sleepmode at least that's what the system monitor says.
The firefox-bin process is an the waiting channel hrtimer_nanosleep and the firefox process and the run-mozilla.sh process is in a do_wait waiting channel.

I do not know what this means but I have tried to uninstall everything that has to do with firefox in the synaptic package manager and reinstalling it in a few different ways. Nothing works. So right now I'm running chromium. But I have a lot of plugins and stuff that I like on firefox so if someone could please help me solve this I would be oh so happy. Thanks

---

### Post by kamratanders on 2010-06-30
I had the same problem. Running firefox -P in a terminal and creating a new profile seems to have worked for me.

Edit: I did some more testing and deleting secmod.db in ~/.mozilla/firefox/<YOUR PROFILE> folder works for me.

---

### Post by beow on 2010-06-30
Me too. Never happened before. Maybe it is some kind of exciting date bug since it pops up for several users just now...:p

---

### Post by vimsy on 2010-06-30
Deleting ~/.mozilla/firefox/RANDOM.default/secmod.db worked for me too. 
Thanks kamratanders... :-)

---

### Post by iacobaeus on 2010-07-01
Thanks kamratanders. It worked like a charm (and almost drove me crazy)

---

### Post by MacHaddock on 2010-07-01
that seems to have worked for me as well. Thanks.

---

### Post by kaninfaan on 2010-07-01
and me...

anyone know why?

---

### Post by LindisfarneJazzClub on 2010-08-02
... and for me as well. 
Strange indeed!

---

### Post by lovinglinux on 2010-08-07
I know is not a solution, but I have created a new Firefox extension that allows to delete secmod.db and compatibility.ini automatically when exiting Firefox, so you don't need to do it manually.

[http://profilecleaner-extension.blogspot.com](http://profilecleaner-extension.blogspot.com)

After installation, the extension will start without deleting the files by default and it will prompt for selecting the files you want to delete.

I have included compatibility.ini because that is causing the same issue here, with Firefox 3.6.8.

---

