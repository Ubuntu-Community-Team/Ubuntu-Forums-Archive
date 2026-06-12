---
title: "How to launch google chrome from the command line"
date: 2010-01-19
forum: General Help
---

### Post by madwoollything on 2010-01-19
I've tried typing 'chromium-browser' at the command line but this does not seem to work (xfce 4.6)

I can launch chrome from the main icon menu but have not been able to figure out how to look at the command that the menu uses to launch chrome in xfce 4.6 (there is no menu editor). Hence I'm even unable to create an icon to launch chrome.

---

### Post by ubername on 2010-01-19
try

/opt/google/chrome/google-chrome --enable-plugins

---

### Post by kdaemon on 2010-01-19
google-chrome works for me

---

### Post by howefield on 2010-01-19
or even..  google-chrome %U

An embarrassment of riches :)

---

### Post by madwoollything on 2010-01-19
Thanks for the suggestions.

Something seems to have broken and I've tried re-installing but still get the same error message:

Cannot chdir to / after chroot: Stale NFS file handle
[6115:6115:508182757:ERROR:/usr/local/google/home/chrome-eng/b/slave/chrome-official-linux/build/src/chrome/browser/zygote_main_linux.cc(522)] Failed to read from chroot pipe: 0
[6115:6115:508182941:FATAL:/usr/local/google/home/chrome-eng/b/slave/chrome-official-linux/build/src/chrome/browser/zygote_main_linux.cc(613)] Failed to enter sandbox. Fail safe abort. (errno: 0)

I'm running jaunty .... is that the problem with Chrome ... although initally the browser would run fine.

---

### Post by specialk1st on 2010-01-30
> **madwoollything said:**
> I've tried typing 'chromium-browser' at the command line but this does not seem to work (xfce 4.6)

I can launch chrome from the main icon menu but have not been able to figure out how to look at the command that the menu uses to launch chrome in xfce 4.6 (there is no menu editor). Hence I'm even unable to create an icon to launch chrome.

Just type: 

1.  google-chrome    (to launch the browser window)

OR...

2.  google-chrome "enter your url here"     (to launch a specific page -- the quotes are necessary)

---

### Post by meierbac on 2011-02-21
The quotes around the URL address are not required in the latest stable release.

---

### Post by Zarquan314 on 2011-09-05
i used chromium-browser and it worked fine

---

