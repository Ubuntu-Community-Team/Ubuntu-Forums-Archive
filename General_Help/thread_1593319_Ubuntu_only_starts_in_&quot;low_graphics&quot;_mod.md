---
title: "Ubuntu only starts in &quot;low graphics&quot; mode"
date: 2010-10-11
forum: General Help
---

### Post by BTWriter on 2010-10-11
EDIT: Exact error message:Here's the exact error:
> 
Ubuntu is running in low-graphics mode

The following error was encountered.  You may need to update your configuration to solve this.

(EE) HID 0566:3107: failed to initialize over relative axes

Okay, so I'm on Lucid Lynx, 64 bit.  I installed libgvfscommon0 via synaptic manager, restarted, and it just sat on the Ubuntu screen loading.  For a long time.  I did a hard restart, and it said it was having an error with graphics, or somethig, and couldn't start into graphics mode.  It asked if I wanted to try low graphics mode.  I said yes.

Now I'm logged in but it's all text.  (As you can tell, I don't have much experience with this stuff.)  Would removing libgvfscommon0 unbreak my system?

Background:
I was trying to get my Ipod touch to work, so I was following the directions at [http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html](http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html)

On the third step, it gave me an error to the effect of: 
"Unmet dependencies:
     gvfs: conflicts: libgvfscommon0 but 1.6.1-0ubuntu1build1 is to be installed
E: broken packages"

That's when I went and installed it manually via synaptic manager, and then restarted and-kaput.

Should I try to use the command line to remove that package?  How would one do that?

I apologize if I'm not specific enough.  I freely admit to being an idiot, and will supply any additional information needed.

Thank you for your time.

---

### Post by Tynx on 2010-10-11
I can't tell you if it breaks even more if you remove the package...

But what i _can_ tell you is how to remove the package on the command-line:
[HTML]sudo apt-get remove <your-package>[/HTML]

or if you want to get rid of the config files and remove really everything of this package:
```
sudo apt-get purge <your-package>
```

Hope can you help in some way:)

---

### Post by BTWriter on 2010-10-11
Thanks Tinx I tried removing it but it's still dead.

Here's the exact error:
> 
Ubuntu is running in low-graphics mode

The following error was encountered.  You may need to update your configuration to solve this.

(EE) HID 0566:3107: failed to initialize over relative axes

---

### Post by iamnotloggedon on 2010-11-24
> **BTWriter said:**
> Thanks Tinx I tried removing it but it's still dead.

Here's the exact error:

I'm having the same issue trying to get my iPod to work on Kubuntu following the same instructions, however I did succeed in installing the gvfs library and can tell you that it's not the cause of your problems. Unfortunately I'm still getting that message (The following packages have unmet dependencies:
  gvfs: Conflicts: libgvfscommon0 but 1.6.1-0ubuntu1build1 is to be installed). I wouldn't suppose you've figured out by now how to connect your iPod.

---

### Post by BTWriter on 2010-11-24
Nope, sorry sir.  I ended up doing a complete reinstall, haha.  And now I just use my Windows computer when I need to transfer to my iPod.

In short, I gave up :(

---

