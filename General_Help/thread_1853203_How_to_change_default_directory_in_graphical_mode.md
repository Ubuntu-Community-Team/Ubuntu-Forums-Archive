---
title: "How to change default directory in graphical mode?"
date: 2011-10-01
forum: General Help
---

### Post by kvvv on 2011-10-01
Has a bug been filed yet? Or has this issue been solved?

It's very, very weird.

I have this problem with Kubuntu default installation on Terminator. I then disabled plasma-desktop and logged into an openbox-kde session, and in that Terminator correctly started in the home directory.

Shift back to kwin-kde with plasma-desktop, the problem returns.

I saw the workaround posted, but it seems too "hacky" and not worth it.

Oh, importantly this problem doesn't happen if I use Konsole or Yakuake. How are the latter two related to KDE to prevent this from happening?

---

### Post by oldos2er on 2011-10-01
Post moved to its own thread.

Please tell us which version of Kubuntu and which version of KDE you're using.

---

### Post by 2F4U on 2011-10-02
[QUOTE=kvvv;11302283Oh, importantly this problem doesn't happen if I use Konsole or Yakuake. How are the latter two related to KDE to prevent this from happening?[/QUOTE]

I don't know Yakuake but Konsole is the default terminal application in KDE.

---

### Post by kvvv on 2011-10-02
> **oldos2er said:**
> 
Please tell us which version of Kubuntu and which version of KDE you're using.

I use Kubuntu 11.04, with KDE 4.7.1.

> I don't know Yakuake but Konsole is the default terminal application in KDE.

It looks like Konsole and Yakuake share the same configurations, at least as far as appearance and behavior go.

I worked around this issue by adding a parameter to the launcher in the menu editor, so it is now "terminator --working-directory $HOME".

However, it irks me that Gtk based terminals and KDE based terminals read different home directories in KDE.

---

### Post by kvvv on 2011-10-04
I have filed a bug here: [https://bugs.launchpad.net/ubuntu/+bug/867820]("https://bugs.launchpad.net/ubuntu/+bug/867820")

---

