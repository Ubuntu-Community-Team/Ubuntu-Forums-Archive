---
title: "All windows 100% transparent"
date: 2010-04-06
forum: General Help
---

### Post by tripplehelix on 2010-04-06
I've used Compiz and enabled transparency. I've then selected the top panel to become transparent. Once applied however everything except my desktop wall paper has become transparent.

This means I'm unable to reverse what I have done and no longer have a working laptop. I've tried restarting, but it's all still transparent. I have a mouse.

Are there any shortcut keys (I use a macbook) I could use to disable compiz? Or is there another way of fixing this issue?

Many thank in advance,
Tom

EDIT: Am I able to send a remote command form my other Macbook?

---

### Post by mechro on 2010-04-06
Try **Alt + F2**, run **gnome-appearance-properties**. Disable Visual Effects from there.

... er... unless, of course, it's transparent! :?

---

### Post by whiskeylover on 2010-04-06
Or maybe "killall compiz"?

---

### Post by sisco311 on 2010-04-06
You can set the transparency of a window with Alt+scroll down/scroll up.

To disable compiz, press Alt+F2 & type:
```
metacity --replace
```then press Enter.

Or press Ctrl+Alt+F2, log in & run:
```
export DISPLAY=:0.0
metacity --replace
```[noparse]then press Ctrl+Alt+F7(or F8).[/noparse]

Or try to reset the opacity settings:
```

export DISPLAY=:0.0
gconftool-2 --recursive-unset /apps/compiz/plugins/opacify
gconftool-2 --recursive-unset /schemas/apps/compiz/plugins/opacify
```

---

### Post by tripplehelix on 2010-04-06
> **sisco311 said:**
> You can set the transparency of a window with Alt+scroll down/scroll up.

All very helpful and all, but I can't see any windows. I lucky have a guest account. Is there anyway to do it from that?

---

### Post by mechro on 2010-04-06
At the log-in screen can you try a Failsafe Gnome session or a Failsafe Terminal session? Perhaps one of those will log you in without compiz enabled.

---

### Post by tripplehelix on 2010-04-06
Ok, fixed it.

For any other fools like me:

1. Login to the guest account

2. Uninstall compiz

3. Log back into main account

4. Edit settings that you've fluped up

5. Install compiz.

---

### Post by sisco311 on 2010-04-06
> **tripplehelix said:**
> All very helpful and all, but I can't see any windows. I lucky have a guest account. Is there anyway to do it from that?

If that's easier, then yes, you can login as guest, open a terminal and run:
```
su - username
```
to login as your normal user (replace username with your login name). Then run:
```
gconftool-2 --recursive-unset /apps/compiz/plugins/opacify
gconftool-2 --recursive-unset /schemas/apps/compiz/plugins/opacify
```to reset the opacity settings or
```
gconftool-2 --recursive-unset /apps/compiz/
gconftool-2 --recursive-unset /schemas/apps/compiz/
```to reset compiz to the default settings.

---

### Post by sisco311 on 2010-04-06
> **tripplehelix said:**
> Ok, fixed it.

For any other fools like me:

1. Login to the guest account

2. Uninstall compiz

3. Log back into main account

4. Edit settings that you've fluped up

5. Install compiz.

Cool!

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

