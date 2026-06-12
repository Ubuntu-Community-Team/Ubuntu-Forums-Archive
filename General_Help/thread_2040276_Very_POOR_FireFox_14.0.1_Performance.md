---
title: "Very POOR FireFox 14.0.1 Performance"
date: 2012-08-10
forum: General Help
---

### Post by crjackson on 2012-08-10
Just did a clean install of 12.04 on my Desktop System (Listed in my Sig) and it's remarkably slow (especially when scrolling) in nearly every aspect.

I don't have this problem at all on my intel powered laptop with an intel video system using the same browser version on ubuntu 10.10

I just installed Chromium web browser and it's nice and fast in all aspects.

Does anyone have a clue what's going on, or how to correct it?

---

### Post by crjackson on 2012-08-11
Anyone?

---

### Post by sienile on 2012-08-11
I don't have a solution, but I switched to Chromium for that very reason. The weird thing is in Windows, Firefox is fast and Chrome is slow; it's the reverse in Ubuntu.

---

### Post by vasa1 on 2012-08-11
> **crjackson said:**
> ... or how to correct it?
Time for a [new profile]("http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles")?

---

### Post by crjackson on 2012-08-12
> **vasa1 said:**
> Time for a [new profile]("http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles")?

Yeah, tried that already, no difference.

---

### Post by crjackson on 2012-08-12
> **sienile said:**
> I don't have a solution, but I switched to Chromium for that very reason. The weird thing is in Windows, Firefox is fast and Chrome is slow; it's the reverse in Ubuntu.

I find it strange that the same browser version runs as fast as chrome when using Ubuntu 10.10

---

### Post by vexorian on 2012-08-12
Did you try unity-2D? It could be compiz.

---

### Post by crjackson on 2012-08-13
> **vexorian said:**
> Did you try unity-2D? It could be compiz.

I tried that too, no joy....

---

### Post by marlow59 on 2012-08-13
I had the same problem with firefox, maybe it's the program itself that is having problems. I actually switched to Chrome for the same reason.

---

### Post by crjackson on 2012-08-13
Well, since it seems that several people may be affected, I wonder where the appropriate place to file a bug report is, Mozilla or Launchpad.

---

### Post by d4m1r on 2012-08-13
You did a vanilla install of 14.0.1? No plugins/themes/etc?

Try disabling all plugins if you are running any in the first place...

---

### Post by crjackson on 2012-08-13
> **d4m1r said:**
> You did a vanilla install of 14.0.1? No plugins/themes/etc?

Try disabling all plugins if you are running any in the first place...

Clean install. Nothing else added.

---

### Post by marlow59 on 2012-08-13
I already tried to fill a bug report for Mozilla, but nothing seems to have changed. Anyway, I think it's more accurate to fill a bug report to mozilla.

---

### Post by vasa1 on 2012-08-13
> **crjackson said:**
> Well, since it seems that several people may be affected, I wonder where the appropriate place to file a bug report is, Mozilla or Launchpad.

I would go via Launchpad first since most people, and possibly you, use a version of Firefox modified to some extent by the [Mozilla Team]("https://launchpad.net/~mozillateam").

---

### Post by pqwoerituytrueiwoq on 2012-08-13
try updating your nvidia driver (i see you have a 8800 gt)
you may want to use the xswap ppa for that

disabling smooth scrolling is a option

---

### Post by crjackson on 2012-08-13
> **marlow59 said:**
> I already tried to fill a bug report for Mozilla, but nothing seems to have changed. Anyway, I think it's more accurate to fill a bug report to mozilla.

Great, thanks... If you get any results on this, let me know please.

---

### Post by crjackson on 2012-08-13
> **vasa1 said:**
> I would go via Launchpad first since most people, and possibly you, use a version of Firefox modified to some extent by the [Mozilla Team]("https://launchpad.net/~mozillateam").

Good  idea, I'll do that.

---

### Post by crjackson on 2012-08-13
> **pqwoerituytrueiwoq said:**
> try updating your nvidia driver (i see you have a 8800 gt)
you may want to use the xswap ppa for that

disabling smooth scrolling is a option

Tried all of the above already.  Disabling smooth scrolling eases the problem a little but it's not much better.

---

### Post by sienile on 2012-08-13
I would think Mozilla would be the one to report the bug to. It's the browser that is having the problem.

---

### Post by vasa1 on 2012-08-14
> **sienile said:**
> I would think Mozilla would be the one to report the bug to. It's the browser that is having the problem.
On the face of it, yes. But the fact is that what most Ubuntu users are using is a modified version of Firefox, modified by the Mozilla team.

---

### Post by vasa1 on 2012-08-14
The other interesting thing to note is that people forget to share the bug number!

---

### Post by crjackson on 2012-08-20
I have to confess, I haven't filed a bug report myself.  It's easier just to move from Firefox to Chromium.

---

### Post by jis on 2012-09-22
I have noticed the performance difference between Firefox and Chromium as well, now with Firefox 15.0.1. Firefox seems to require much more from X when scrolling, for example. On the other hand, Firefox respects better window manager's (say xfwm4) settings concerning e.g. raising a window when clicking inside it.

I use even older, less powerfull hardware: AMD Ahtlon XP without SSE2, NVIDIA Corporation NV17 [GeForce4 MX 420] (rev a3) graphics, so the browser ui responsiveness is important.

---

### Post by TenPlus1 on 2012-09-23
I am using Firefox 15 on an old Compaq laptop with intel gfx and it feels smoother and faster than Google Chrome on the same machine...  Maybe it's down to gfx drivers and their support, or it could be the fact that I disable web caching and it's all in memory...

---

### Post by jis on 2012-09-23
I also suspect there is something wrong in X. At least in ubuntu 11.04 on the same hardware even running grsync went unusually slow because X was using so much CPU. I guess displaying progress bar was not implemented optimally in X.

---

