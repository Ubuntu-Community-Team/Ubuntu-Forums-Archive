---
title: "Firefox addon messed with Firefox"
date: 2011-05-10
forum: General Help
---

### Post by ki4jgt on 2011-05-10
I recently installed this addon: [https://addons.mozilla.org/en-US/firefox/addon/facebook-friend-request-notifi/](https://addons.mozilla.org/en-US/firefox/addon/facebook-friend-request-notifi/)

I didn't like it because for some reason it messed with my clicking. I've uninstalled it, but now every time I click a button or link that is on the bottom half of the browser, it refuses to click. I have to scroll the link up to the top half of the browser. I've removed the addon. I've deleted the .Mozilla folder out of my home directory. Is there any other step I can take to fix this?

---

### Post by lovinglinux on 2011-05-11
I think it was just a coincidence. If you deleted the mozilla folder, then it should have reverted the effect. Unless the extension interfere with your gnome settings, which I doubt it does.

Which Ubuntu version and Firefox version you are using?

---

### Post by ki4jgt on 2011-05-11
> **lovinglinux said:**
> I think it was just a coincidence. If you deleted the mozilla folder, then it should have reverted the effect. Unless the extension interfere with your gnome settings, which I doubt it does.

Which Ubuntu version and Firefox version you are using?

I've actually installed this app before (The same thing happened then) I'm using 4.0 and 11.04

---

### Post by lovinglinux on 2011-05-11
> **ki4jgt said:**
> I've actually installed this app before (The same thing happened then) I'm using 4.0 and 11.04

I have tested it here and couldn't reproduce the problem.

Just for the sake of troubleshooting, go to Firefox Add-ons Manager, disable Global Menu Bar Integration and Ubuntu Firefox Modifications, restart Firefox and test it. Re-enable them afterwards.

---

### Post by ki4jgt on 2011-05-11
> **lovinglinux said:**
> I have tested it here and couldn't reproduce the problem.

Just for the sake of troubleshooting, go to Firefox Add-ons Manager, disable Global Menu Bar Integration and Ubuntu Firefox Modifications, restart Firefox and test it. Re-enable them afterwards.

I think it has something to do with my small screen. (Netbook) Because the last time it happened, I was using the netbook and I reinstalled the entire OS because of it. but today, everything seems to be fine. Maybe it worked itself out of the system. It was happening just randomly. Some of the buttons would allow me to click them and some of them wouldn't. It really acted weird on facebook. I couldn't click any buttons or links (This wasn't random) I had to move my mouse to the very top edge of every button before it would allow me to click it. I can upload a video if you like, but right now I'm going to do the global menus thing really quickly.

---

### Post by lovinglinux on 2011-05-13
Is not your screen or the global menu. This problem is affecting me too now. It affects my Ubuntu and another Windows machine, but only on specific pages. Scrolling up or down just a little solves the problem.

I don't think is that add-on causing the issue. The problem is not constant btw.

I have [reported this as bug]("https://bugzilla.mozilla.org/show_bug.cgi?id=656896") and encourage you to leave a comment there, specifying the conditions it happens on your machine and web sites it happens.

---

### Post by ki4jgt on 2011-05-13
> **lovinglinux said:**
> Is not your screen or the global menu. This problem is affecting me too now. It affects my Ubuntu and another Windows machine, but only on specific pages. Scrolling up or down just a little solves the problem.

I don't think is that add-on causing the issue. The problem is not constant btw.

I have [reported this as bug]("https://bugzilla.mozilla.org/show_bug.cgi?id=656896") and encourage you to leave a comment there, specifying the conditions it happens on your machine and web sites it happens.

To remedy the problem, I marked all firefox packages including global menu for reinstalation, I deleted the .mozilla folder in home directory, and also deleted all folders related to the gnome desktop. Unfortunately it also has been interfering with my desktop environment.

---

### Post by ki4jgt on 2011-05-13
Dude, it's the addon. I have a friend who installed it in FF3 and had the same problem. It's not FF4 only. I did visit the page in your bug and it didn't reproduce. (After I deleted all gnome folders and mozilla and reinstalled FF) This addon is causing the problem.

---

### Post by lovinglinux on 2011-05-13
> **ki4jgt said:**
> Dude, it's the addon. I have a friend who installed it in FF3 and had the same problem. It's not FF4 only. I did visit the page in your bug and it didn't reproduce. (After I deleted all gnome folders and mozilla and reinstalled FF) This addon is causing the problem.

Well, I never installed that add-on on the Windows machine and it shows the problem. I also can reproduce without any add-ons.

Perhaps is something in Firefox that is triggered by the add-on.

---

