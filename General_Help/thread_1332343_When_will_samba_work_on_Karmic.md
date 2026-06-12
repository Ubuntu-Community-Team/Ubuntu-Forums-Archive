---
title: "When will samba work on Karmic?"
date: 2009-11-20
forum: General Help
---

### Post by fjm03 on 2009-11-20
Upgraded to Karmic and lost the ability to write to windows shares on my NAS. Samba is apparently mis configured on Karmic.

Is there a universal workaround that _newbies_ can employ until the problem is fixed? Other threads address the problem on an individual basis which does not match the diagnostics (file outputs) of my machine.

Another curiosity. Samba, a fairly common tool, wasn't even included in the Karmic upgrade. Had to add it through SPM, and then it contained a warning for xinetd users.

Whatsup?

---

### Post by Mighty_Joe on 2009-11-20
> **fjm03 said:**
>  Samba is apparently mis configured on Karmic.


Works fine for me but I did a fresh install.
Perhaps you can share the details of what you're seeing with us.

---

### Post by Giblet5 on 2009-11-20
This is due to your "create mask 0600" default setting in the config (/etc/samba/smb.conf).

Uncomment the setting and change the mask to 0666 and restart samba via ```
sudo /etc/init.d/samba restart
``` and anyone can destroy everything (aka Windows Nirvana Mode - Chaos Boogaloo Remix).

By default, you can create a new file, but then that file's read-only (default mask is 0744 -rwxr--r--). (Protecting Windows users from themselves)

That will only affect newly created file on the share...

This command will apply WNM-CBR to your existing files:

--assumes samba share is /samba--
```
sudo find [COLOR="DarkRed"]/samba[/COLOR] -type d -exec chmod 777 {} \; ; sudo find [COLOR="DarkRed"]/samba[/COLOR] -type f -exec chmod 666 {} \;
```

I don't really recommend doing that, but it will do what you think you want. I recommend learning how to admin a professional server class OS (learn about permissions, samba user accounts, samba configuration, etc).

---

### Post by fjm03 on 2009-11-20
To Giblet5:

First, thank you.
I appreciate the advice about doing the homework first. Stuck in the same rut on FreeBSD.
I understand the drift of things but don't understand whether your admonition, "I wouldn't", applied to both the manual edit and the *chmod* or just the *chmod*?

---

### Post by fjm03 on 2009-11-20
Giblet5:

The problem effects all files; not just new files. Files moved from the NAS and then back to the NAS are also rejected.

Any transfer attempts from Karmic to a windows share on the NAS brings back: INVALID ARGUMENT

Tried manually editing samba.conf (uncommented *create mask = 0600* and changed it to *create mask = 0666)* with no success.

---

