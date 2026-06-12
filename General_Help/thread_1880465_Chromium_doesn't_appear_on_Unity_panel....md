---
title: "Chromium doesn't appear on Unity panel..."
date: 2011-11-13
forum: General Help
---

### Post by Reded on 2011-11-13
Hey all,

I went over to Chromium to give it a try over Firefox. I've tried installing through both Synaptic and Software Centre (Figured it can't hurt to try...) And I still get this issue.

Basically when I open a Chromium window, the icon in Unity panel doesn't have the little white triangle next to it to show I've got one opened. And if I minimise my window, it just disappears completely. Can't Alt+Tab it, as it doesn't seem to appear in that screen either.

Ubuntu 11.10 64-bit, any help appreciated, thanks!

---

### Post by fragos on 2011-11-13
Open a terminal window and initiate chromium from there. The name will be chromium-browser. You should see error messages in the terminal that should help you discover the problem. I'd also recommend that you try the stable version since it's least likely to have a problem.

---

### Post by Reded on 2011-11-13
Hey, thanks for reply! What do you mean by the 'stable' version, there's only one version in the software centre :(

I'll try Terminal and see what happens.

Terminal returned this:
[3:3:62009676368:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
[6:6:62010013033:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied

---

### Post by jmacx81 on 2011-11-13
I had the same issue. A simple restart resolved all issues I was having with it.

---

### Post by Habeouscorpus on 2011-11-13
If you installed it from the Software center, then chances are you have the "stable" version.

---

### Post by fragos on 2011-11-13
> **Reded said:**
> Hey, thanks for reply! What do you mean by the 'stable' version, there's only one version in the software centre :(

I'll try Terminal and see what happens.

Terminal returned this:
[3:3:62009676368:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
[6:6:62010013033:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied

There are PPA software sources for stable, beta and daily build. If you haven't chosen a PPA and are using the default I'd think you are with the stable. Firefox uses that library as well but appears to have it's own version. You might try running chromium as "sudo chromium-browser" but if you installed with the Software Center you shouldn't have permission issues. I've not run into your problem but I'm running chrome on Ubuntu 32 bit 11.10.

---

### Post by Reded on 2011-11-13
Simple restart fix worked! Let's hope it stays working, thanks for replying.

---

### Post by jmacx81 on 2011-11-14
> **Reded said:**
> Simple restart fix worked! Let's hope it stays working, thanks for replying.

You shouldn't have any problems with it now.

---

