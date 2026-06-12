---
title: "Compiz issue (referring to kde4 in Ubuntu)"
date: 2010-10-15
forum: General Help
---

### Post by Marceau on 2010-10-15
I've followed all the threads on Compiz issues with 10.10, but so far, I've found no solace.

I've tried completely reinstalling Compiz from synaptic, but it hardly fixed anything.

The latest status is that I can get Compiz running for about 10 to 15 seconds. When it runs, menu bars are gone. After that, all falls back to metacity.

When trying compiz --replace, I see the following:

```
marceau@computer:~$ compiz --replace libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory kde-window-decorator(3201) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen" kde4-window-decorator: Could not enable decorations on display ":0.0" kde-window-decorator(3199) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen" kde4-window-decorator: Could not enable decorations on display ":0.0" i915_program_error: Exceeded max nr indirect texture lookups (5 out of 4)  Launching fallback window manager
```I find that strange as I'm in (Gnome) Ubuntu 10.10. This is on an Eeepc that was running Compiz fine on 10.04.

Any suggestions?

---

### Post by 3Miro on 2010-10-15
Are you running KDE or Gnome? If compiz fails under KDE, then it will return you to kwin not metacity, however, compiz is trying to run kde-windows-decorator and it cannot find libgconf without which gnome will not work.

Try installing libgconf from synaptic (or the KDE package manager).

---

### Post by Marceau on 2010-10-15
> **3Miro said:**
> Are you running KDE or Gnome? If compiz fails under KDE, then it will return you to kwin not metacity, however, compiz is trying to run kde-windows-decorator and it cannot find libgconf without which gnome will not work.

Try installing libgconf from synaptic (or the KDE package manager).

The crazy thing is that I'm on a vanilla Ubuntu 10.10 UNE install, which, as far as I know/knew is strictly gnome.

I have not installed anything even related to KDE as far as I know.

Also, I just checked and Libgconf is installed normally.

---

### Post by 3Miro on 2010-10-15
Go to CCSM (install it if you have to) and open the settings. Go to windows decorations and you should see "kde-window-decorator". Change that to "gtk-window-decorator". Then check to see if you get any errors and what are they.

---

### Post by Marceau on 2010-10-15
> **3Miro said:**
> Go to CCSM (install it if you have to) and open the settings. Go to windows decorations and you should see "kde-window-decorator". Change that to "gtk-window-decorator". Then check to see if you get any errors and what are they.

Hm. I have it installed, and can only locate 'general settings'. I can see that gnome support is enabled and kde support is disabled. I don't see an option to set a specific window decorator.

---

### Post by 3Miro on 2010-10-15
Scroll down from general. There should be Accessibility, Desktop and then Effects. In the Effects section, there is an option Window Decoration and you have to go inside to add the "gtk-window-decorator".

Make sure you have compiz-plugins-main installed, this may be the problem.

---

### Post by Marceau on 2010-10-15
> **3Miro said:**
> Scroll down from general. There should be Accessibility, Desktop and then Effects. In the Effects section, there is an option Window Decoration and you have to go inside to add the "gtk-window-decorator".

Make sure you have compiz-plugins-main installed, this may be the problem.

You put me on the right track there. Going through all of compiz once again in synaptic, I noticed compiz-kde. When I went to remove that, two items were automatically offered for installation compiz-gnome and something else. After finishing that, I'm now running compiz without problems (so far). This is the first time in a week I've been able to run it longer than 10 seconds.

Thanks for your patience.

By the way, would you happen to know a workaround for max texture size which causes compiz to quit for me with two monitors running?

---

### Post by 3Miro on 2010-10-15
Glad to help, compiz-kde should not have been installed in the first place, but at least now you have it fixed.

As for the texture size, I have a feeling that this may be an issue with the video card (i.e. not enough memory). Video memory is very tricky, it is far from being as simple as 256MB or 512MB or something like that. There are subdivisions of memory that are fixed in size (depending on the device).

You can try playing with CCSM to reduce the number of workspaces, animations, effects and so on. Also, try to match the notebook screen to the external screen in resolution and what they are showing (i.e. have the same picture on both). Maybe this is not what you need, but it is the best I can do.

PS You should mark this thread as solved and possibly start a new one.

---

### Post by Marceau on 2010-10-17
> **3Miro said:**
> Glad to help, compiz-kde should not have been installed in the first place, but at least now you have it fixed.

As for the texture size, I have a feeling that this may be an issue with the video card (i.e. not enough memory). Video memory is very tricky, it is far from being as simple as 256MB or 512MB or something like that. There are subdivisions of memory that are fixed in size (depending on the device).

You can try playing with CCSM to reduce the number of workspaces, animations, effects and so on. Also, try to match the notebook screen to the external screen in resolution and what they are showing (i.e. have the same picture on both). Maybe this is not what you need, but it is the best I can do.

PS You should mark this thread as solved and possibly start a new one.

Thanks again for all the help. I'm pleased to say I don't even have the max texture size issue anymore. Seems like 10.10 is a winner after all.

---

### Post by fcserg on 2010-12-18
Hi guys. I had similar situation. I installed UNE on Acer Aspire One, but compiz didn't work. A check, that compiz use gnome decorator, but still have same error "exceeded max nr indirect texture lookups". Maybe video adapter in thia Acer is not enought good for compiz? I use compiz-check tool, and it says that everything is OK. Thank a lot

---

