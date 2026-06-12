---
title: "Natty dead keys issues"
date: 2011-06-02
forum: General Help
---

### Post by Hil0 on 2011-06-02
I just updated from 10.04 to 10.7 yesterday and to 11.04 today, and after both these updates (I tried between them and after 11.04) I'm unable to use my dead keys (swedish default keyboard layout) without putting them with a letter. é and so on works but just ^ doesn't work in any KDE programs.
I know I've had this problem before, though I can't remember when or how I solved it.
I'm not willing to use the eliminate dead keys option since I want to able to do accented letters.

---

### Post by Zorael on 2011-06-02
Try this;
```
$ im-switch -s default-xim
```
Then log out and back in. Run it with sudo to make it a system-wide change.

---

### Post by Hil0 on 2011-06-02
> **Zorael said:**
> Try this;
```
$ im-switch -s default-xim
```Then log out and back in. Run it with sudo to make it a system-wide change.

To that I got this reply 

No system wide default defined just for locale en_US .
Use "all_ALL" quasi-locale and set IM.
update-alternatives: using /etc/X11/xinit/xinput.d/default-xim to provide /etc/X11/xinit/xinput.d/all_ALL (xinput-all_ALL) in manual mode.

Which I'm not sure what it means.

[EDIT] I did still log out and in, and now it works. Thanks for the help. [/EDIT]

---

