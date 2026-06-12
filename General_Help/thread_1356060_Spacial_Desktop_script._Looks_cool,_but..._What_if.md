---
title: "Spacial Desktop script. Looks cool, but... What if I want to go back?"
date: 2009-12-15
forum: General Help
---

### Post by Gonz_91 on 2009-12-15
Hi everyone!

After deciding my laptop just wasn't good 'nuff to run WoW, I came back to linux (xD).
I saw this article ([link]("http://www.omgubuntu.co.uk/2009/11/spatial-desktop-ubuntu-gorgeous-gnome.html")) and thought I'd try it.
And try it I did. Ran the script, got all the visual goodness downloaded and configured. But now I'm wondering: what if I want to go back?
The script has a "Restore" function, which doesn't seem to do anything at all (I didn't actually count on it working, I didn't intend on going back...).

So, is there a way to restore everything to defaults? Panels, themes, everything, like a fresh install, but without the backup-ing and all that.

Thanks in advance =D

---

### Post by LostinSpacetime on 2009-12-15
It seems like the script has a restore option. So you only need to run it again and choose that option.

---

### Post by Gonz_91 on 2009-12-16
Ahem...
The script does have a restore option, which doesn't seem to work:

```

Restore using:
$

```
And just waits for input, and I have no idea what to input there.
But that's not the point, I want to go back as far as the day I installed ubuntu, not how I had it before running the script...

Thanks a lot :)

---

### Post by 3rdalbum on 2009-12-16
It looks like the changes it made are only applicable for your user account, not system-wide.

You can make your user account "fresh" by deleting the hidden folders inside your home directory. The hidden folders contain your user account settings. Without the settings, your programs and your Gnome desktop will go back to default settings and write new settings files.

If you are careful and selective of which settings you delete, you should be able to pretty much reverse the effects of the script without (for instance) removing your e-mail.

---

### Post by Gonz_91 on 2009-12-16
> **3rdalbum said:**
> It looks like the changes it made are only applicable for your user account, not system-wide.

You can make your user account "fresh" by deleting the hidden folders inside your home directory. The hidden folders contain your user account settings. Without the settings, your programs and your Gnome desktop will go back to default settings and write new settings files.

If you are careful and selective of which settings you delete, you should be able to pretty much reverse the effects of the script without (for instance) removing your e-mail.

Just what I was looking for! Thank you very very much :D

---

