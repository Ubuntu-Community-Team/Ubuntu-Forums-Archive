---
title: "Restoring the system"
date: 2011-10-26
forum: General Help
---

### Post by Kermit524 on 2011-10-26
Hi Everybody,
I hope you can help. I have just done the stupidest thing ever - managed to chmod 777 ALL my files and folders, yes, even those under root, and yes, recursively.
I know there's no way to reverse this, however - is there a way to reset or repair the system? - making a new installation without deleting the user files, or making a back-in-time system restore?
I'm on Ubuntu Lucid.
Many thanks in advance for any idea, and please feel free to shoot me afterwards. I just don't believe myself. :-s.

---

### Post by linuxwin2 on 2011-10-27
Try to do an upgrade to ubuntu 11.10.
Then check your files.

---

### Post by Lars Noodén on 2011-10-27
For that kind of thing, it is best to do a fresh reinstallation.  You'll have trouble with the home directory though because your backup will contain the wrong permissions.  You can do a quick fix of your home directory first, though:

```

chmod -R 750 ~Kermit524
chmod -R 700 ~Kermit524/.ssh/

```

Do that for each user.

There may be things that slip through the cracks but those are the default settings for most things created in your home directory.

---

### Post by Kermit524 on 2011-10-27
Thanks for both of you,
- Lars, what do you mean by fresh reinstallation: that I backup all my files and install from fresh (erasing all content)? 
- I checked and at the moment the pemission for my home directory is 755. So maybe I didn't do a lot of damage after all - Is it possible that even though no error message were displayed - the action didn't take place at all?
Thanks again for all your help!

---

### Post by Lars Noodén on 2011-10-27
> **Kermit524 said:**
> Thanks for both of you,
- Lars, what do you mean by fresh reinstallation: that I backup all my files and install from fresh (erasing all content)? 
- I checked and at the moment the pemission for my home directory is 755. So maybe I didn't do a lot of damage after all - Is it possible that even though no error message were displayed - the action didn't take place at all?
Thanks again for all your help!

If you do not have a separate /home partition, then to do a freash install, all content will get erased.  If you do have a separate /home partition, then the backup is just good practice.

Check ~/.ssh what are the permissions there?  If it is 700 then everything might be OK in the home directory.

---

