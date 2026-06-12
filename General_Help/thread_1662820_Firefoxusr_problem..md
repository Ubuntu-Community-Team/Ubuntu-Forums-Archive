---
title: "Firefox/usr_problem."
date: 2011-01-08
forum: General Help
---

### Post by Firbewn9 on 2011-01-08
I've got three user accounts, 10.10 running on eeepc. Two of them work relatively well, but the on the third one firefox keeps crushing every 10 seconds or to be more precise every 2~3 link clicks.

There is a firefox crash info but no specific problem is being suggested. Same goes for terminal - clear.

Doesn't matter if I delete the 'old' third user and put new one. FF behaves always the same on fresh account. It also affects minefield.

Any (reasonable) help would be greatly appropriated.

---

### Post by lovinglinux on 2011-01-08
Do you have Prism or Moonlight installed?

Have you tried to create a fourth user account to see if the problem persists, without deleting the third one?

---

### Post by ajgreeny on 2011-01-08
Try renaming the **~/.mozilla** folder in the home of the third user where FF keeps crashing; it sounds like a bad profile for some reason or other.

---

### Post by lovinglinux on 2011-01-08
> **ajgreeny said:**
> Try renaming the **~/.mozilla** folder in the home of the third user where FF keeps crashing; it sounds like a bad profile for some reason or other.

The OP already recreated the Ubuntu user account, so the profile is already clean. It could only be a profile fault, if Firefox is loading an extension or plugin installed globally. In this case, deleting the profile won't help.

---

### Post by Firbewn9 on 2011-01-09
To be sure I created 4rd user - same story. As for addons - they are not accessible on new accounts. As I try to open them, firefox crashes (namoroka and minefield). It's pretty hard for me to even guess what's the problem since as I mentioned before the two previous accounts work well, no crashes. One of most bizarre unwanted behavior I came across in ubuntu.

---

### Post by lovinglinux on 2011-01-09
> **Firbewn9 said:**
> To be sure I created 4rd user - same story. As for addons - they are not accessible on new accounts. As I try to open them, firefox crashes (namoroka and minefield). It's pretty hard for me to even guess what's the problem since as I mentioned before the two previous accounts work well, no crashes. One of most bizarre unwanted behavior I came across in ubuntu.

There should be at least one extension installed on all profiles and accounts: Ubuntu Firefox Modifications. Additionally, plugins are also shared. So disable everything through Firefox Add-on manager and check if the problem persists.

---

### Post by lidex on 2011-01-09
So you're using two versions of firefox side-by-side? That could be the problem.

---

### Post by Firbewn9 on 2011-01-10
> **lovinglinux said:**
> There should be at least one extension installed on all profiles and accounts: Ubuntu Firefox Modifications.

It is installed but it's not active on minefield due to incompatibility.

[QUOTE=lidex] So you're using two versions of firefox side-by-side? That could be the problem.[/QUOTE]

Could you elaborate please? Since they both work on mentioned 2 account I find it less likely to be a problem.

---

### Post by lovinglinux on 2011-01-11
Try to copy the settings from one account that works, into the account that does not work. Start with ~/.mozilla/firefox and then move on to gnome settings if it doesn't work.

Because of privacy concerns, just do this for testing and delete the new profile afterwards, unless there is no problem about sharing profiles between users.

---

