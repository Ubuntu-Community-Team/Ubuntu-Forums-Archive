---
title: "New firefox window forgets toolbar settings."
date: 2010-02-10
forum: General Help
---

### Post by PureRumble on 2010-02-10
Hello.

I use Kubuntu 9.10. All packages are up-to-date.

The problem: When opening a new window in firefox, the new window forgets the toolbar settings.

So when I start firefox and the first window shows up, it shows my toolbar settings correctly, which is pretty minimalistic actually (no buttons, bookmark menu, google searchbar, etc.).

But when I then open a new window from the original one, the new window has forgotten my toolbar settings and shows all the buttons, the searchbar, etc..

This happens irrespective from if I hit Ctrl+N, or print firefox after hitting Alt+F2 (which just opens a second window since the firefox process is already running).

What can I do? I read in some other post that you should delete some settings file that might have gone corrupt, but I have done this and it did not help.

Do you have any advice? This is reaaaaally annoying!

Best regards!

---

### Post by PureRumble on 2010-02-12
bump. anyone?

---

### Post by lovinglinux on 2010-02-12
> **PureRumble said:**
> bump. anyone?

Delete *localstore.rdf* file from your FF profile. It will reset all your toolbars. This usually fixes toolbar issues.

---

### Post by m_kylli on 2010-02-13
I have the same problem and lovinglinux solution didn't work for me.

I'm using netbook edition by the way.

---

### Post by lovinglinux on 2010-02-13
> **m_kylli said:**
> I have the same problem and lovinglinux solution didn't work for me.

I'm using netbook edition by the way.

Are you opening the new window from the menu/toolbar or is it a web page that opens it as pop up?

---

### Post by m_kylli on 2010-02-14
Doesn't matter if I do File->New window, Ctrl+N or close firefox and open it again from shortcut or command. Toolbar will reset in any case, deleting localstore.rdf doesn't help.

---

### Post by lovinglinux on 2010-02-14
> **m_kylli said:**
> Doesn't matter if I do File->New window, Ctrl+N or close firefox and open it again from shortcut or command. Toolbar will reset in any case, deleting localstore.rdf doesn't help.

Does it also resets the main window toolbar when you restart firefox? If this is the case, then try to start Firefox with this command

```
firefox -safe-mode
```

Then configure your toolbars, then close Firefox and start again with the same command. If the toolbars doesn't change, then you have a theme or an extension messing with the localstore.rdf file.

---

### Post by PureRumble on 2010-02-15
m_kylli, it is the tab mix plus add-on that is messing around.

At least that was the cause of my problem.

Just disable the add-on and try again.

What is really odd is that my stationary has tab mix plus too but there is no problem there with opening new windows... very odd.

---

### Post by m_kylli on 2010-02-17
Nevermind, problem solved by deleting localstore.rdf while firefox was running with one exception. The Bookmark in Launcher button of the Netbook Editions preinstalled webfav extension reappears on the toolbar no matter what I do.


Correction: I just restarted Firefox after an extension update. The toolbar settings went to the crapper again.

---

