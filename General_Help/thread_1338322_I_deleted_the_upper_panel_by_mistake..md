---
title: "I deleted the upper panel by mistake."
date: 2009-11-26
forum: General Help
---

### Post by mirchichamu on 2009-11-26
How can I bring it back? OR at least wireless and sound icons?
Thanks in advance.

---

### Post by akakingess on 2009-11-26
Is the bottom one still there?  If so, then I would just right-click on it and click on "add new panel", which may add it to the side or something, but you should be able to move it to the top, at which point you click on the blank panel and start clicking "add to panel" or whatever the command is to start adding all the stuff back that was there to begin with...

---

### Post by mirchichamu on 2009-11-26
> **akakingess said:**
> Is the bottom one still there?  If so, then I would just right-click on it and click on "add new panel", which may add it to the side or something, but you should be able to move it to the top, at which point you click on the blank panel and start clicking "add to panel" or whatever the command is to start adding all the stuff back that was there to begin with...

Thanks akakiingess for reply.
I made a new panel above but I am unable to bring the wireless icon and volume icons back. Now my wireless is connected but I cannot see it.

---

### Post by 73ckn797 on 2009-11-26
You can get the panels back up to the OEM state just after installation by running the following command using terminal.

Go to Applications/Accessories/Terminal

Paste this command in:

```
gconftool-2 --recursive-unset /apps/panel
```Restart the computer and all will be back to normal.

---

### Post by miniyak on 2009-11-26
wireless is included when you add "notification area" to the panel

---

### Post by akakingess on 2009-11-26
> **73ckn797 said:**
> You can get the panels back up to the OEM state just after installation by running the following command using terminal.

Go to Applications/Accessories/Terminal

Paste this command in:

```
gconftool-2 --recursive-unset /apps/panel
```Restart the computer and all will be back to normal.

Thanks for the tip, I will actually store that for later use, for when I accidentally delete the top panel.

---

### Post by mirchichamu on 2009-11-26
> **73ckn797 said:**
> You can get the panels back up to the OEM state just after installation by running the following command using terminal.

Go to Applications/Accessories/Terminal

Paste this command in:

```
gconftool-2 --recursive-unset /apps/panel
```Restart the computer and all will be back to normal.

One million thanks. It worked.

---

### Post by 73ckn797 on 2009-11-26
> **mirchichamu said:**
> One million thanks. It worked.


Sounds good. Enjoy.

---

