---
title: "Maximised application's icon does not show on Launcher"
date: 2012-06-03
forum: General Help
---

### Post by Paddy Landau on 2012-06-03
If I open an application maximised (e.g. Adobe Reader, GIMP), its icon momentarily shows on the Launcher, but then the icon disappears.

This is extremely frustrating, as it means Alt-Tab will not recognise the application's existence; and I obviously cannot click the icon to go to the application when on a different workspace.

How can I get the Launcher button to display and not disappear?

---

### Post by Paddy Landau on 2012-06-04
Oh... I realise that this is not only for maximised applications.

Certain applications do this every time.

In my case, Adobe Reader and GIMP.

Whether they are maximised or not, the icon appears briefly in the launcher before disappearing.

Any ideas?

---

### Post by Paddy Landau on 2012-06-05
Bumpety-bump!

---

### Post by Rebelde on 2012-06-07
Same for me here, but it happened only once I had installed the new GIMP 2.8 version. Before that all worked fine with the old version. I suspect it could be related to a bug with the unity launchpad... which is also giving me problems: does not work under autohide mode --although there is another [thread on this issue...]("http://ubuntuforums.org/showthread.php?t=1965991&highlight=autohide+bug") also unresolved so far. I'll check around and come back to this thread to see whether a solution has been found. Cheers and good luck!

---

### Post by Paddy Landau on 2012-06-07
> **Rebelde said:**
> ... although there is another [thread on this issue...]("http://ubuntuforums.org/showthread.php?t=1965991&highlight=autohide+bug")
Thanks for your reply, but that's not the same issue. This thread is about a specific icon not showing; the left-hand Unity bar shows perfectly well. The other thread is about a bug with the Unity bar auto-hide.

I shall raise a bug report for this problem.

EDIT: Oh... now it's working. :confused:

---

### Post by AnotherMuggle on 2012-06-07
> **Paddy Landau said:**
> Thanks for your reply, but that's not the same issue. This thread is about a specific icon not showing; the left-hand Unity bar shows perfectly well. The other thread is about a bug with the Unity bar auto-hide.

I shall raise a bug report for this problem.

EDIT: Oh... now it's working. :confused:

I noticed this issue with Gimp.  A restart fixed it and it didn't seem to happen again.

I wonder if it is at all releated to the known issue mentioned on this page: [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Known_Issues]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Known_Issues")

> Unity Launcher. If an application is pinned and then unpinned from the Unity Launcher using right-click->Un/Lock to Launcher repeatedly the application may vanish from the Launcher. It is necessary to log out and login again. This relates to an application monitoring framework called "Bamf" (978401) 

---

### Post by Rebelde on 2012-06-07
> **AnotherMuggle said:**
> I noticed this issue with Gimp.  A restart fixed it and it didn't seem to happen again.

I wonder if it is at all releated to the known issue mentioned on this page: [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Known_Issues]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Known_Issues")
Thanks a lot AnotherMuggle! Your solution worked for me: simply restarting resolved the icon problem and is working fine so far. If the condition returns I'll post again. Thanks again!

---

### Post by Paddy Landau on 2012-06-07
> **AnotherMuggle said:**
> I noticed this issue with Gimp.  A restart fixed it and it didn't seem to happen again.

I wonder if it is at all releated to the known issue mentioned on this page: [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Known_Issues](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Known_Issues)
The specific item is the [second Desktop Interface]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Desktop_Interface-1"). I don't recall pinning the items to the Launcher, but it's working now, so, oh well.

---

### Post by AnotherMuggle on 2012-06-07
> **Paddy Landau said:**
> The specific item is the [second Desktop Interface]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Desktop_Interface-1"). I don't recall pinning the items to the Launcher, but it's working now, so, oh well.

Gimp creates multiple windows on launch so maybe something funky is going on which confuses the launcher.

---

### Post by Paddy Landau on 2012-06-08
> **AnotherMuggle said:**
> Gimp creates multiple windows on launch so maybe something funky is going on which confuses the launcher.
I have been using the option to use a single window, available in the new GIMP, version 2.8. But Adobe Reader also gave me the problem. It's still working correctly today.

---

