---
title: "Can't turn on terminal bell in gnome-terminal using remote screen session with irssi"
date: 2010-11-06
forum: General Help
---

### Post by mkarnicki on 2010-11-06
Hi guys,

I'm using 10.04, and gnome-terminal GNOME Terminal 2.30.2 . I have irssi running on screen session on remote host. And I've been struggling for quite many days to configure it to produce either visual feedback or ring terminal's bell when I receive a private message or one of those that are highlighted.

My compiz settings window in General tab has 'Audible bell' checked.

My GNOME terminal has 'Terminal bell' checked.

I also added 'set bell-style audible' to my ~/.inputrc

And I also tried to manually load pcspkr module into my kernel.

No of the above helped or at least I haven't been able to notice any difference.

I also used some commands for irssi to produce bell sign.


Any ideas?

---

### Post by karpox on 2011-06-28
I know this is pretty old topic but in my case i found that only solution was to install alternative terminal called "Terminator". I think that it is much better than "bundled" gnome terminal. [http://www.tenshu.net/terminator/](http://www.tenshu.net/terminator/)

---

### Post by mkarnicki on 2011-06-28
Thanks for your reply :)

Recently I've been running irssi locally and using notify.pl script, which calls to notify-send from libnotify for nice, slick notifications. Too bad their time length isn't configurable (stupid design decision to make all notifications 10 seconds long).
But I do plan going back to a remote irssi setup, so I'll give Terminator a try :)

---

