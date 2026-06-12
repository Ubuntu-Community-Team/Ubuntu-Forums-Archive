---
title: "Constant program crashes with segfaults"
date: 2010-10-01
forum: General Help
---

### Post by Dogmatrix on 2010-10-01
I'm running ubuntu 10.04 lts.  Last night there was a recommended update for some things, which I ran.  There was probably some header upgrade in that since I had to reinstall my nvidia drivers after the update manager was finished.

Now, nearly every program that I run crashes. Looking at System>Admin>Log file viewer and I see lots of errors in kern.log

They look like this:
```
Oct  1 12:19:20 debbie-desktop kernel: [46110.312556] chromium-browse[4340]: segfault at aa06 ip 000000000000aa06 sp 00007fff2ab6a9f8 error 14 in libasound_module_conf_pulse.so[7fae2cc23000+1000]
```

So far, firefox, pidgin, xchat, and chromium crash.  Terminal, the log file viewer, synaptic and minecraft do not crash.  I can keep chromium from crashing (I think) as long as I don't click anywhere in the browser chrome.  If I use keyboard shortcuts, and just click links on web pages, it seems to be mostly ok.

I tried doing Fix Broken Packages in Synaptic and that doesn't appear to do much.

Does anyone have more suggestions or is there more information I need to provide?

---

