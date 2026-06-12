---
title: "Xubuntu 9.10 breaks after updates"
date: 2009-11-11
forum: General Help
---

### Post by excalq on 2009-11-11
Hello All,

I succeeded in helping a colleague install Linux on his old laptop. Since it's an older system, we installed Xubuntu 9.10 [Karmic]. It installed fine, but last night he applied the automatically available updates to the system, which caused something to break.

He had the system configured to log in automatically (to Xfce), bypassing username or password entry. After the updates, xdm or gdm (not sure which) is now showing after bootup, and when the user's password is entered, X apparently restarts, brining the system back to a fresh display of the login screen.

It seems like xdm or Xfce is broken after these standard updates.
The system was virtually unmodified since Xubuntu was installed earlier that day.

Any suggestions of what to try to diagnose the problem? Thanks!

---

### Post by MichealH on 2009-11-11
I have the same problem with my Ubuntu 9.10 i upgrade Firefox wont start Firefox anymore this is the 4th time I have failed setting Ubuntu up.

---

### Post by excalq on 2009-11-11
While not an ideal solution, I was able to rebuild the user's home directory, and recover that way.

I moved /home/[user] to /home/[user].broken
and recreated the default user home directory with
```

#mv /home/[user] /home/[user].broken
#mkdir /home/[new-user]
#cp /etc/skel/* /home/[new-user]
#chmod [user]:[user] /home/[new-user]

```

However, I only did this because it was a brand new installation. If not, you'd need to move over all your data, documents, .mozilla, .purple (if you use pidgin), etc....

---

### Post by excalq on 2009-11-11
MichealH: I don't think you're having the same problem. I think your problem is with Firefox, where as mine is with Xfce or X or something at that level.

I'd recommend recreating your .mozilla directory, and allowing firefox to recreate your profile:

Completely shutdown all firefox windows.
Then run:
```

mv ~/.mozilla ~/.mozilla.broken

```

The restart Firefox. You'll lose all bookmarks, saved passwords, etc. To get them back copy their .xml files from ~/.mozilla.broken to ~/.mozilla once your original problem is confirmed fixed.

---

