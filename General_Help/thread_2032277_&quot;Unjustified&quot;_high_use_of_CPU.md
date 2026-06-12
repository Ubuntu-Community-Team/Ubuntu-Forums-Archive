---
title: "&quot;Unjustified&quot; high use of CPU"
date: 2012-07-23
forum: General Help
---

### Post by nnmaxcom on 2012-07-23
Hi!

I have a Zenbook UX31E, i installed Ubuntu 12.04, before I had a Windows 7.

Whenever I'm playing an online video (youtube, twitch etc) the CPU fan goes crazy, i noticed this because never heard any noise when using windows. So I looked at top and (i dont know how to copy from top), but the top cpu consuming processes when the cpu is noisy is "plugin-containe", "xorg" and firefox.

Is my flash plugin or whatever broken? Is it normal? Win7's was very silent.

Thank you.

---

### Post by asmoore82 on 2012-07-23
Yes, it's normal. A real PitA, but normal.

Adobe's flash player for Linux is completely ignorant of hardware video acceleration. So it basically pumps way too much of the workload of video playback through the CPU. The Open Source gnash player is of course 10000% better on this but it is blocked or unrecognized at a lot of popular flash video sites.

---

### Post by nnmaxcom on 2012-07-23
> **asmoore82 said:**
> Yes, it's normal. A real PitA, but normal.

Adobe's flash player for Linux is completely ignorant of hardware video acceleration. So it basically pumps way too much of the workload of video playback through the CPU. The Open Source gnash player is of course 10000% better on this but it is blocked or unrecognized at a lot of popular flash video sites.

Crap, how disappointing. How is it that there's no solution for that yet if it's so known and general? I mean, just wasting computer power senseless it's ridiculous, specially for a laptop. It renders a lot of regular internet activity unfordable.

I'm surprised and disappointed. Thank you for the answer anyways.

---

### Post by lukeiamyourfather on 2012-07-23
> **nnmaxcom said:**
> Crap, how disappointing. How is it that there's no solution for that yet if it's so known and general? I mean, just wasting computer power senseless it's ridiculous, specially for a laptop. It renders a lot of regular internet activity unfordable.

I'm surprised and disappointed. Thank you for the answer anyways.

It seems that Adobe is focusing less on Flash these days. Not just in Linux but across the board. For example their HTML5 tool similar to Flash called Edge. This is probably for the better as Flash is frequently exploited and has inconsistent platform support (especially on mobile devices and Linux). Hopefully websites will stop requiring it and offer alternatives (like the HTML5 mode on YouTube and Vimeo).

---

