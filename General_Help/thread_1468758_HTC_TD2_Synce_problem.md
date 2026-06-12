---
title: "HTC TD2 Synce problem"
date: 2010-05-01
forum: General Help
---

### Post by rules on 2010-05-01
Hi all

When I was running 9.10, I followed these simple steps ... [http://loongye.wordpress.com/2009/03/04/how-to-configure-ubuntu-810-intrepid-to-work-with-htc-touch-pro-or-any-wm6-device/](http://loongye.wordpress.com/2009/03/04/how-to-configure-ubuntu-810-intrepid-to-work-with-htc-touch-pro-or-any-wm6-device/) ... which got my phone syncing perfectly (files, contacts etc.). 

Now that I have changed to 10.04, these steps no longer work.

Any ideas?

Thanks.

---

### Post by rules on 2010-05-02
Read somewhere about software sources that aren't enabled by default so enabled them all, went into Synaptic and saw some of the synce goodies could be upgraded and proceeded.

It now syncs, but for some reason Multisync still does not want to play with. It tells me "Unable to read from one of the members" and from what I can tell it's the synce-opensync-plugin (which I'm gathering is the part that reads the PDA) that's at fault. 

Any ideas?

Cheers.

---

### Post by jo@tux on 2010-05-02
Hi,
which version of multisync you use. multisync0.90 0.91 ? I use this one.
On Friday i do an update from 9.10 to 10.04 and multisync0.90 stop to work.
On a console i see an Error like this.
```
synce-opensync-plugin had an error while getting changes error during get_changeinfo method
```
Search around the web doesn't really help me.
I have tried the following steps. I delete the partnership with my Phone (Xperia X1) and also delete the sync group in multisync0.90.
As a result deleting the partnership you lost all entry's you have sync before. Doing these is no Problem for my, because I sync once per week and Evolution is my master.
Then I create a new Partnership and a new group in multisync. After doing this syncing works as usual.
I think this is not the solution for this Problem, but a little workaround.
I am accustomed this kind of Problems after an update, but I don't like that a software which has worked for a long time, stop to work after an update.
Hope this can be an help for you.

---

### Post by rules on 2010-05-02
Thanks Jo :)

I had to do the delete procedure twice though as the first time it killed all the contacts on my phone ... second time round it put them all back again :)

Cheers.

---

### Post by jo@tux on 2010-05-10
Did you have test syncing again? Because I have made a change on my mobile and syncing stop working. We must look forward and wait what to do.

On Site [http://www.opensync.org/ticket/1131]("http://www.opensync.org/ticket/1131") ist spoken about this Bug. I have apply this and for me it will work now.

---

### Post by rules on 2010-05-14
For time being I have set up my phone and laptop to sync contacts with gmail, not perfect, but at least it works and is dead easy to do :)

---

