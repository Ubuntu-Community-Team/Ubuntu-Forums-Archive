---
title: "Terminal with &quot;Copy input to&quot; function (konsole alternative)?"
date: 2009-10-06
forum: General Help
---

### Post by kc600 on 2009-10-06
I use konsole because it has the possibility to automatically copy what you type in one terminal to another terminal. This is handy if you have mirrored servers, where you want to do the same on both.

However, installing konsole on karmic requires 190Mb extra ([http://pastebin.org/37030](http://pastebin.org/37030)). This seems like an overkill for such a simple feature.

Is there an alternative to konsole which has the "Copy input to" function and does not have this enormous overhead?

---

### Post by sedawk on 2009-10-06
Yes, there is clusterssh and I love it!

You can get it here:
[http://sourceforge.net/projects/clusterssh](http://sourceforge.net/projects/clusterssh)

In a configuration file you define a cluster and then
it opens ssh connections to all machines and you
can type commands for all machines in a "master" window.

It is really funny to watch people when you do a change
to a whole cluster that would have taken them 30 minutes
and you do it in 2 ;-)

I tried other tools but they required lots of additional
perl modules I couldn't install or failed to compile
on my machines.

Now I only need perl+tcl+tk and setup was easy.

---

### Post by kc600 on 2009-10-06
Thanks, I'll give it a try!

---

### Post by kc600 on 2009-10-07
Hmm... couldn't get it to work on Karmic yet: [http://sourceforge.net/tracker/?func=detail&aid=2874145&group_id=89139&atid=589145](http://sourceforge.net/tracker/?func=detail&aid=2874145&group_id=89139&atid=589145)
Will try again later.

---

### Post by kc600 on 2009-10-08
Works now. Was probably a Karmic issue.

And it works well!
[LIST]
[*]Separate window for input to send to all terminals
[*]Send input to just one terminal fast and intuitively
[*]Open several terminals with one command
[/LIST]

The only downside is that i miss colors in listings and most notably in vi, but that's minor. Maybe i should toy with my ~/.csshrc some more.

[edit]
terminal_args=+cm
[/edit]

---

### Post by sedawk on 2009-10-08
The color problem should also happen if you do a plain ssh
in an xterm.
So also check the general settings on your target machines.

---

