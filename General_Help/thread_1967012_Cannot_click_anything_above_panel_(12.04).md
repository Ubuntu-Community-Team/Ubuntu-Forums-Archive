---
title: "Cannot click anything above panel (12.04)"
date: 2012-04-27
forum: General Help
---

### Post by mode7 on 2012-04-27
As the title says, mouse clicks do not register above the KDE panel.
I've rebooted several times, and did the latest upgrades (Through another VT), including the kernel update that was just released.
Keyboard input works everywhere, and mouse input works only on the panel. For instance, I can open and close the application launcher, but I cannot click in it whatsoever.
Mouse clicks registered just fine in the live boot, and they work alright in KDM.

I did a fresh install of Kubuntu 12.04 over 11.10 on my desktop. KDE was working fine before.. And mouse input is working just fine here in Windows. I did not touch any settings after install.

I am completely confused as to what would cause this..

Anyhow, I will boot back into Kubuntu and attempt to disable virtual desktops (I never use more than 1 anyways), and disable effects too to see if that works.

If anyone has any insight, I would greatly appreciate it :)

(Also, I searched all over for similar posts. I apologize if this was already answered.. I could not find it. Just a similar complaint or two that were unanswered)

EDIT:
Well, I hate to have to edit this once again.
I had to mark as unsolved. This was not fixed. While disabling effects and logging out and in seemingly fixes the issue, it persists regardless of settings when the computer is restarted.
Thus I have to rule out proprietary drivers/compositing effects/and virtual desktops as the cause of this.
If I can't figure this out, I will need to revert to 11.10, use Linux Mint KDE, or change to standard Ubuntu, which I do not want to do. This basically makes my desktop unfeasible to use.

---

### Post by crono141 on 2012-04-28
I've got the same problem. Keyboard works everywhere, mouse clicks only work in unity. I'm a Linux noob, so I don't know keyboard shortcuts well enough to get around.  This is in standard ubuntu, so I don't think switching to standard ubuntu will work for you.  Additionally, when I boot off the live CD, I get no mouse click response at all.  The cursor moves, but its like clicks aren't registered.

Edit: Just installed 11.04 with wubi, and initially it was okay. Then the upgrade Window appeared and it began exhibiting the same problem too. I guess I can't use ubuntu at all.

Edit 2: And just like that, dismissing the upgrade and alt driver windows restored functionality. Makes me wonder if it isn't related to mouse capture and release.

---

### Post by crono141 on 2012-04-28
Bump. No one else is having this mouse issue?

---

### Post by crono141 on 2012-04-28
I got a work around. Though my work around makes me think we have different issues. Running in ubuntu 2D makes the problem disappear.

---

### Post by mode7 on 2012-04-29
Hey, crono141, I have also posted this in the [KDE forums]("http://forum.kde.org/viewtopic.php?f=66&t=101797"), where somebody else responded about having the same issue.

I was beginning to believe it may be an issue with KDE's window management behavior along with buggy focus management, but that may not be the case. I also did mess with the focus stealing prevention settings, which did not seem to change anything.

The fact you don't encounter it in Unity 2D means it may be an issue with higher-end compositing window managers. Or that it is indeed a different issue altogether.. I didn't try it in Unity.

Anyhow, as mentioned in my KDE thread, the issue disappeared on my desktop completely. I did not touch any settings or install updates. I gave up on it for the night, then booted it up the next.. so I have really no clue! I am still interested in this issue though, as I can't really let something go unless I know the exact cause of it. Plus I am a bit scared of it reoccurring :)

I tried using the fglrx drivers (Proprietary AMD drivers), but they had no effect on the issue when it was occurring. Do you have an ATI/AMD card, by chance? Might be a connection.

FWIW, I have Kubuntu 12.04 installed on my Macbook as well, and have not had this issue at all.

---

