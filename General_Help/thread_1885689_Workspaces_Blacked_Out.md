---
title: "Workspaces Blacked Out?"
date: 2011-11-23
forum: General Help
---

### Post by 1,000,000,000 on 2011-11-23
So I've been using 11.10 for about a month now with no major problems, but recently my workspaces stopped working. When I click the icon in the Unity launcher the workspace screen shows, but only Workspace 1 shows, the rest are totally blacked out. I can't click them at all, and I can't use shortcuts to get to them. (Ctrl+Alt+Left/Right) It was working before, but stopped.

Thanks,
Chamberlain

---

### Post by lechien73 on 2011-11-23
You could try installing and running the Compiz Config Settings Manager:

```
sudo apt-get install compizconfig-settings-manager
```

Then run it, click on General Options, then Desktop Size. Make sure it's set to 2 horizontal x 2 vertical.

---

### Post by 1,000,000,000 on 2011-11-23
I've already got ccsm, but desktop size isn't an option. I made sure it was in the latest version.

Edit:

Nevermind, I was looking under the General tab, I didn't click on general options.

2x Edit:

But it didn't work.

---

### Post by lechien73 on 2011-11-23
Ok, odd...another solution I read said to try the following:

Log out of unity and log back in as guest. Do the workspaces work? If so, then log back in as yourself and try:

```
unity --reset
```

in a terminal window. Log out and back in again.

I haven't tried this, so please let me know if it works :)

---

### Post by 1,000,000,000 on 2011-11-25
Ok, so when I logged into the computer as a guest, workspaces did work, but that command didn't fix the problem in my account.

---

### Post by mc4man on 2011-11-25
Sounds like you're using unity-2d, if so the number of Ws's is set in gconf (gconf-editor

```
gconftool-2 -s -t integer /apps/metacity/general/num_workspaces 4
```

If you use gnome-shell then the above # of Ws's will be reset when when exiting Gs to the # of Ws's open when exiting Gs. This then affects what unity-2d shows. Improper behavior on Gs's part that hasn't been fixed

---

