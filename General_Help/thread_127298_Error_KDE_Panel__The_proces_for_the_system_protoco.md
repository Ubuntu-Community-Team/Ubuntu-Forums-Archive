---
title: "Error KDE Panel : The proces for the system protocol died unexpectedly"
date: 2006-02-08
forum: General Help
---

### Post by windmill on 2006-02-08
HEllo,

I got a strange error each time I login :
Error KDE Panel : The proces for the system protocol died unexpectedly

Idon't know how to solve this. It isn't a problem to work with KDE.
I work on 3.5.1 KDE kubuntu trough a nx-client freenx server.
As I'm quite new to the linux world, I would like to know which error .log I should consider to search for this problem.

Thank you very much

---

### Post by troywill1 on 2006-03-01
I see this same problem, but on Kubuntu Dapper (installed yesterday from daily build).  In fact, any call like: kfmclient openProfile webbrowsing (as an example, no profiles are working for me) returns: WARNING: DCOPReply<>: cast to 'QCString' error.

---

### Post by tisuang on 2006-03-19
I also need help for the same problem =/

---

### Post by SeanTater on 2006-03-19
DCOP is a process that takes all of kde's programs and arranges it so that they can communicate efficiently. It seems as though dcopserver has crashed. It isa good idea to report these to both the ubuntu launchpad and bugs.kde.org, but if you choose to do so; please try to do whatever you did before and see if it happens again. If it does, tell them down to the jot exactly what it took for it to occur, and what happens. In an open source community, that is the fastest way to get something fixed without fixing it yourself.

If you want to read a log; go to the xsession-errors log. It should be easily found in KSystemLog. If you want to know exact where it is, look in your home folder. You will need to enable "show hidden files" in konqueror to see it; similar in other dialogs. It's name is .xsession-errors (The preceding period is important).

*_NOTE: Please be patient, and use find utilities, whatever you do. We'd rather you be a little less through than to lose patience and report nothing at all. *_

---

### Post by cyB3r4rd on 2006-03-20
I have the same problem. But it seems it's a systemwide bug. I can't log in neither to GNOME, nor to KDE, only minimal terminal from GDM.
In case of logging in to KDE the progress stops at Loading peripherals. After a few seconds (rather lot) I get the blank lightblue screen, with no KDE, no nothing...
In case of GNOME there isn't even a splash... :???:

Other strange things related to this (at least I think): I'm unable to access / either in konqueror/krusader AND mc. :( 

So at the moment I'm sitting on top of a junk. Please find a solution for this, as this makes a system practically unusable. :neutral: 

And I start to get bored with daily reinstalls+updates... :-? 

Yes, I know Dapper is still beta... but... this seemed to be the most stable among the 1CD distros... :cry:

---

### Post by tisuang on 2006-03-21
My .xsession-errors is too big, i can't post it.

---

### Post by ltmon on 2006-03-21
I started getting that error when I installed knetworkmanager.

Knetworkmanager didn't actually work for me, so I uninstalled it and the errors stopped.

Just in case this helps anyone...

L.

---

### Post by tisuang on 2006-03-21
I haven't knetworkmanager. And I didn't install any new software.

---

### Post by dragonflyFZX on 2006-04-30
i have the same problem on dapper.  I did not have it before, only after installing knetworkmanager.  Knetworkmanager did not work in the beginning, so i took it off again and the error dissapeared.  Got knetworkmanager on dapper going now after consulting [the wiki]("https://wiki.ubuntu.com/NetworkManager").  But the error is back.  What to do about this?  Should I file this as a bug? I have never done this before.

---

### Post by dr_dano on 2006-05-09
Hello, I get the same error after updating to KDE 3.5.2 on Kubuntu breezy.
The error appears after a few minutes starting the session.
I don't have knetworkmanager installed (I don't have this on my repository list).
after this error the system menu is empty (I can't access directly to my home folder or the mounted devices from the taskbar).
Kopete have a lot of problems to connect with msn.

What can I do?

---

### Post by leif81 on 2006-05-18
This error just began occuring for me.

I'm used Fedora Core 5 however. The error sort of crept up out of nowhere. I turned on my laptop and seconds after logging into my KDE desktop I get this KDE Panel error. After clicking OK my wallpaper goes blank (black) and it prevents me from starting konqueror. However I was able to start Konsole. My Kpanel is still alive however the rest of the desktop portion is dead ( I can't right click on the desktop and my icons are gone).

---

### Post by regx on 2006-09-04
I was getting this too ever since I installed to dapper. I had several problems, bluetooth - etc that were causing my loggin to hang, but the problem causing this error was with keep. Basically it was a permissions problem. Anyway, I think keep is installed by default. Try removing keep and see if the error goes away. If your loggin is hanging, and you are not using bluetooth, try removing that as well. This fixed my problems! No annoying errors when NX-ing in, and my profile loads quickly.

---

### Post by linux_newbie on 2006-09-21
I have the same problem. I am not able to open the System menu on my KDE Panel.

Where do I report the bug ? is it a KDE bug or a kubuntu bug. I am running Dapper.

I switched to KDE coz my Gnome wont load anymore.

---

### Post by doubled on 2007-02-26
> **regx said:**
> . . . Try removing keep and see if the error goes away. .

That's what fixed it for me. I had been using keep for a few weeks and then suddenly ("unexpectedly") the error appeard. I could replace the System icon from the add applets on the panel, and it would fix things until the next logout or reboot. But removind "keep" is the solution for now.

---

### Post by VMbuseck on 2007-07-01
> **regx said:**
> ... Try removing keep and see if the error goes away. ...

I also removed the icon from the panel and the problem vanishes. But what's the reason for the problem ?

---

