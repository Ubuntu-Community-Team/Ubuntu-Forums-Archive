---
title: "Adding &quot;-notrayicon&quot; to Opera link in Gnome-Do"
date: 2009-10-01
forum: General Help
---

### Post by solwic on 2009-10-01
Trying to be able to open Opera from Gnome-Do and not have to look at the ugly system tray icon.  The "-notrayicon" works fine if I open Opera from Applications -> Internet...but that defeats the purpose of using Gnome-Do.  

There almost has to be a way to do this, I just can't find it.  Anybody help?

---

### Post by solwic on 2009-10-01
Ok, I found a solution:

```

Another solution to this problem:

This solution will work no matter how opera is launched:

Modify the /usr/bin/opera file to have the -notrayicon switch with 
Code:
sudo gedit /usr/bin/opera
Scroll to the bottom of the file where it says:

Code:
exec "$OPERA_BINARYDIR/opera" "$@"
and comment that line by adding a # to the beginning

Code:
#exec "$OPERA_BINARYDIR/opera" "$@"
Finally make a new line but with the notrayicon as the argument so that the end of the file looks like this:
Code:
#exec "$OPERA_BINARYDIR/opera" "$@"
exec "$OPERA_BINARYDIR/opera" "-notrayicon"
save and close the file.

```

Found it here:  [http://www.ubuntu-inside.me/2009/08/howto-disable-opera-10s-tray-icon_08.html](http://www.ubuntu-inside.me/2009/08/howto-disable-opera-10s-tray-icon_08.html)  

In the comments, second or third entry.  

Thanks anyway, guys.  Hope this helps someone else.

---

