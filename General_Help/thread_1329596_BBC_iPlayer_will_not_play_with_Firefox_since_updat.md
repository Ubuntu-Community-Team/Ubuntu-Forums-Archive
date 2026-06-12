---
title: "BBC iPlayer will not play with Firefox since update to 3.5.5."
date: 2009-11-17
forum: General Help
---

### Post by Scunnered on 2009-11-17
I accepted the latest update and was informed that I must restart Firefox to complete the update and now yet again **_[COLOR="Red"]BBC iPlayer will not play with Firefox.[/COLOR]_**

Having messed about with FF 3.5.4 and eventually getting things to work I am once again back to square one - WHY?

What is going on with Firefox.  This is totally unacceptable.

It is no bl---y good that what is claimed to be an upgrade is anything but.

Can anyone offer a solution to let me view TV and listen to radio on the BBC in the UK as before.  Failing that can someone kick Mozilla right up the Kyber pass to put matters right.

Yours in complete frustration

---

### Post by Scunnered on 2009-11-18
When viewing my posts this morning I found that I had received the following in respect of my original post BBC iPlayer will not play with Firefox.

GavCity advised as follows :

[B][I]Switching off the video playback option did not work for me but turning off effects did.

I did a bit more reading around though and came across this post on the compiz list which recommends the following remedy from launchpad.

' I forgot where I found this workaround, it worked on Karmic 64bits:
Open terminal and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
then add: "export GDK_NATIVE_WINDOWS=1" before the last line of text'

It works nicely here without having to disable effects.[/I][/B]

However following this advice did not resolve the problem.

Can anyone else offer a resolution to the problem?

---

### Post by varangian on 2009-11-18
If you haven't already found it the thread [_here_]("http://ubuntuforums.org/showthread.php?t=1326072") goes over this. It doesn't seem to be a specific 3.5.5 problem, maybe more an issue with the Flash plugin/Compiz/video driver/sound system not playing nice with each other. There are some things in that thread that you could try out.

---

### Post by Scunnered on 2009-11-18
**varangian**

Thanks for your post.  I had a look at things but like others I can listen & view iPlayer in Opera but not FF.  Everything worked perfectly prior to the last update so as far as I can see it is down to FF.

If this is not sorted out PDQ I will abandon FF and use Opera.

It is so frustrating to have everything work perfectly only for it to totally fall down when what is claimed to be an improvement is applied.

---

### Post by jaycee23 on 2009-12-18
Tried the workaround you put up Scunnered - worked a treat - been looking for an answer to the prob for ages so thanks for your post

---

### Post by PaulReaver on 2009-12-18
If you use iplayer a lot, have a look at "get_iplayer" in the repos.
its better than watching it in firefox.

---

### Post by Scunnered on 2009-12-18
**PaulReaver**

Thanks vm for your reply.  I was totally unaware that this was available in the repos.  Seems to be a well kept secret.

I will have a close look at it.  FF seems to have settled down a bit with some of the latest updates but I still experience problems with it.  Opera still winning hands down.


Edit : Loaded programme from Synaptic but unable to find it to see how it works in relation to FF.  Where does it hide in the menu or how do I activate it?

---

### Post by John Bean on 2009-12-18
> **Scunnered said:**
> I can listen & view iPlayer in Opera but not FF.  Everything worked perfectly prior to the last update so as far as I can see it is down to FF.

This is not a logical conclusion; if it was specifically Firefox's "fault" then the same thing would have affected me - and it hasn't. 

> If this is not sorted out PDQ I will abandon FF and use Opera.

Wow, that'll make 'em! jump to it... ;-)

But seriously...

> It is so frustrating to have everything work perfectly only for it to totally fall down when what is claimed to be an improvement is applied.

Yes, it's always annoying if an update breaks something but it's not necessarily the updated software that is the real cause of the problem, often just a symptom of it.

---

