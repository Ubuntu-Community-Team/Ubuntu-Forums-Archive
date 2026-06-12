---
title: "&quot;Open in terminal&quot; from Directory Menu does nothing."
date: 2011-10-18
forum: General Help
---

### Post by bonheur1 on 2011-10-18
The "Open in terminal" shortcut from the navigable folder menu (Directory Menu) found on the Panel#2 of Xfce was working just fine with Xubuntu 11.04. But I was offered an upgrade to 11.10 and the "Open in terminal" command from the Directory Menu does not work anymore since then--clicking on it does nothing at all.

How do I repair this feature?

Eventually, is there a tool to check that the upgrade from Xubuntu 11.04 to 11.10 was done correctly?

Thank you in advance! :)

---

### Post by Toz on 2011-10-18
> **bonheur1 said:**
> The "Open in terminal" shortcut from the navigable folder menu (Directory Menu) found on the Panel#2 of Xfce was working just fine with Xubuntu 11.04. But I was offered an upgrade to 11.10 and the "Open in terminal" command from the Directory Menu does not work anymore since then--clicking on it does nothing at all.

How do I repair this feature?

Eventually, is there a tool to check that the upgrade from Xubuntu 11.04 to 11.10 was done correctly?

Thank you in advance! :)
Took a look and sure enough, it didn't work. However, when I went to SettingsManager->PreferredApplications->Utilities tab and changed "Terminal Emulator" to "Debian X Terminal Emulator", it worked again.

---

### Post by gsmanners on 2011-10-18
Are you using Nautilus for your file manager? I don't know that that has a working context menu for terminal.

You have the terminal working, though, right? Try out these:

```
apt-cache policy xfce4-terminal
apt-cache policy thunar
```

Should return:

```
xfce4-terminal:
  Installed: 0.4.8-1

thunar:
  Installed: 1.2.3-0ubuntu1
```

---

### Post by gsmanners on 2011-10-18
> **Toz said:**
> Took a look and sure enough, it didn't work. However, when I went to SettingsManager->PreferredApplications->Utilities tab and changed "Terminal Emulator" to "Debian X Terminal Emulator", it worked again.

Seriously? Worked fine for me no matter what setting I use. And the menu item reads: "Open Terminal Here" (not "Open in terminal").

---

### Post by Carborundum on 2011-10-18
> **gsmanners said:**
> Seriously? Worked fine for me no matter what setting I use. And the menu item reads: "Open Terminal Here" (not "Open in terminal").
I'm using xfce4-terminal and thunar, and the menu item reads: "Open in terminal". It also doesn't work. :P

Edit: Actually , I think we may be looking at different menus. If I right-click a directory while in thunar, the menu reads "Open terminal here", and it works. However, if I click the "Home" directory menu in the bottom panel, I get the behavior described above.

---

### Post by Toz on 2011-10-18
> **gsmanners said:**
> Seriously? Worked fine for me no matter what setting I use. And the menu item reads: "Open Terminal Here" (not "Open in terminal").

The OP is referring to the DirectoryMenu xfce4-panel plugin.

---

### Post by gsmanners on 2011-10-18
Oh! That explains it. Yeah, see I've been using Places rather than that DirMenu thing.

---

### Post by bonheur1 on 2011-10-18
> **Toz said:**
> Took a look and sure enough, it didn't work. However, when I went to SettingsManager->PreferredApplications->Utilities tab and changed "Terminal Emulator" to "Debian X Terminal Emulator", it worked again.

Your solution worked for me as well, thank you!

It may be a matter of perception, but I believe that the terminal takes longer to open now than with the previous release of Xubuntu. Maybe that just means that I should switch to Lubuntu or its Mint counterpart, after all, my computer is old.

---

### Post by Jose Catre-Vandis on 2011-10-18
Same issue showed up on clean install of Xubuntu 11.10, so not an upgrade issue. The fix by Toz also worked here. Thanks Toz :)

---

### Post by Rodney9 on 2011-10-18
> **Toz said:**
> Took a look and sure enough, it didn't work. However, when I went to SettingsManager->PreferredApplications->Utilities tab and changed "Terminal Emulator" to "Debian X Terminal Emulator", it worked again.

Thank you Toz, that worked for me also.

---

### Post by Toz on 2011-10-18
Bug report created: [https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/877811]("https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/877811").

---

### Post by gsmanners on 2011-10-18
You might want to point that to upstream: [https://bugzilla.xfce.org/show_bug.cgi?id=8018](https://bugzilla.xfce.org/show_bug.cgi?id=8018)

---

### Post by Toz on 2011-10-18
> **gsmanners said:**
> You might want to point that to upstream: [https://bugzilla.xfce.org/show_bug.cgi?id=8018](https://bugzilla.xfce.org/show_bug.cgi?id=8018)
Done. Thanks for the info.

---

