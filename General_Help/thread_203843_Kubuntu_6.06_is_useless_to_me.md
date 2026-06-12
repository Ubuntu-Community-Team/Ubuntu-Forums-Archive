---
title: "Kubuntu 6.06 is useless to me"
date: 2006-06-26
forum: General Help
---

### Post by Smiling Bob on 2006-06-26
Why?  No pda sync software what happened to Kpilot?  No html editor, WTF happened to Quanta?  Won't allow me to install Thunderbird, or Firefox.  Where the hell did they put gcc?  Without it you can't compile from source.  Won't allow me to install Gimp or any other GTK based software.

Who was responsible for authorizing the release of this incomplete piece of crap?:mad: 

Smiling Bob the Enzyte Man
[email]jbatt@fiberpipe.net[/email]
[B]
Update as of  22:40 CUT[/B]

aysiu and trigg3r

Thanks for the help.  I got everything I needed after enabling the extra repos that aysiu mentioned.  I tried apt-get and aptitude before and they were'nt able to find anything.  Firefox and thunderbird were listed in synaptic but it errored out everytime I tried to install them, something about "not being able to commit to the changes".

All three, apt-get, aptitude, and synaptic work great if you have the right list of repos.  The one that came with my install, obviously wasn't the right one.  I've been using Linux since Mandrake 6.1 (a little over 6 yrs.) and this is my first experience with a distro that isn't a Red Hat spinoff.

Thanks 4 the help

John

---

### Post by aysiu on 2006-06-26
Are you lacking an internet connection? If you are, Kubuntu will probably be useless to you, and you'd be better off with a multi-CD distro like Debian, Fedora, or Mandriva.

*build-essential* is on both CDs (Alternate and Desktop), but the others you'll probably need an internet connection for.

If you have an internet connection, you have no excuse for complaining. [Enable extra repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo aptitude update
sudo aptitude install quanta mozilla-thunderbird firefox gimp build-essential
``` Two commands make your day.

---

### Post by trigg3r on 2006-06-26
[QUOTE=Smiling Bob]Why?  No pda sync software what happened to Kpilot?  No html editor, WTF happened to Quanta?  Won't allow me to install Thunderbird, or Firefox.  Where the hell did they put gcc?  Without it you can't compile from source.  Won't allow me to install Gimp or any other GTK based software.[/QUOTE]

Bob, it would help if you described here what you meant by "Won't allow me to install Thunderbird, or Firefox". As for the other requirements, make sure you have the correct repositories in /etc/apt/sources.list and fire away.
```
sudo apt-get install kpilot quanta gcc -y
```

---

### Post by Xzallion on 2006-06-26
Did you bother clicking the add programs thing under applications?  Quanta is in there(you may have to check a checkbox for it to show).

I think both thunderbird and firefox are in the synaptic package manager.  Its under system>administration.  Use the search feature to find them.

To build stuff from source ```
sudo apt-get install build-essential
``` that will install gcc and anything else you need to build from source.

Edit: Darn Aysiu and trigg3r beat me, and are more helpful then me yet again.  And my foolish directions were for the Gnome desktop, sorry.

---

### Post by ltmon on 2006-06-26
Wow... all that anger.  Be nice to the developers please, most of them aren't paid to do this you know.

Anyway, getting to your questions, (K)Ubuntu comes with a very limited set of software that is meant for the "average" desktop user.  They are not enabled by default because the Kubuntu team does not directly provide support for the software.

You can install more software from additional repositories by following the documentation at: [http://doc.ubuntu.com/kubuntu/desktopguide/C/](http://doc.ubuntu.com/kubuntu/desktopguide/C/)

Pay particular note to the section here: [http://doc.ubuntu.com/kubuntu/desktopguide/C/ch03s06.html](http://doc.ubuntu.com/kubuntu/desktopguide/C/ch03s06.html)

Hope it helps, and please ask nicely next time.

Cheers,

L.

---

### Post by aysiu on 2006-06-26
[QUOTE=ltmon]Wow... all that anger.  Be nice to the developers please, most of them aren't paid to do this you know.[/QUOTE] I agree that you should be nice to the developers, but I was under the impression they were paid employees of Canonical.

---

