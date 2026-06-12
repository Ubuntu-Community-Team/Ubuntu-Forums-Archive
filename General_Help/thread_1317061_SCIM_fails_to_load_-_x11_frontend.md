---
title: "SCIM fails to load - x11 frontend"
date: 2009-11-06
forum: General Help
---

### Post by aeriph on 2009-11-06
After upgrading to 9.10 SCIM fails to load. The usual control+space trigger has no effect, and running "scim" in terminal shows why:

```
Smart Common Input Method 1.4.9

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to load x11 FrontEnd module.
SCIM has exited abnormally.
```

I've tried reinstalling scim and all related packages, as well as disabling and re-enabling the languages I use it for; nothing has worked.

---

### Post by pjbgravely on 2009-11-06
The end of [this link ](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/392250) may help you.

Paul

---

### Post by aeriph on 2009-11-07
Thanks but unfortunately that hasn't solved the problem. Anything along the lines of reinstalling doesn't seem to fix it...

---

### Post by zhongguohua88 on 2009-11-19
I have the same problem. I tried reinstalling everything and it still doesn't works.

---

### Post by Irihapeti on 2009-11-19
That error message means that Scim is already running.

If you are running 9.10, go to System -> Administration -> Language Support and make sure that the input method dialogue shows "scim-bridge". By default it is set to "none". Then log out and in again.

This takes the place of the terminal command:

```
im-switch -z [your locale language] -s "scim-bridge"
```

which was used in earlier versions. You can still use the terminal command if you want to.

---

### Post by deepclutch on 2009-11-23
@Irihapeti:thanks ,it worked for Me.I am using en_GB.utf8 as default locale

---

### Post by myhieu on 2010-06-04
> **Irihapeti said:**
> That error message means that Scim is already running.

If you are running 9.10, go to System -> Administration -> Language Support and make sure that the input method dialogue shows "scim-bridge". By default it is set to "none". Then log out and in again.

This takes the place of the terminal command:

```
im-switch -z [your locale language] -s "scim-bridge"
```which was used in earlier versions. You can still use the terminal command if you want to.

Yeah, you're right, that error means Scim has already run, just try Ctrl-Space (or hotkey you defined to trigger it)

---

