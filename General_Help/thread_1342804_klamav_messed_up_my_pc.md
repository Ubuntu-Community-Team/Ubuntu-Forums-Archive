---
title: "klamav messed up my pc"
date: 2009-12-01
forum: General Help
---

### Post by linuxhippy on 2009-12-01
I'm using ubuntu/kubuntu/xubuntu 9.10 and used synaptic to install klamav.  I then updated the virus definitions and scanned / using sudo.  It found 190 viruses and tried to quarantine them but could not.  Then I rebooted and cannot login now.

Can I fix my messed up pc or do I need to just do a reinstall and never use klamav again?

---

### Post by linuxhippy on 2009-12-02
well, my pc boots again.  I was frustrated and didn't fully explain that klamav didn't find real viruses-it found files that it mistakenly thought were viruses (like firefox zip files???) and took action.  This was caused by my running klamav as the root (that's the only way I could get it to scan / but viruses wouldn't have root priveleges anyway in a SE Linux system).

I figured that I had messed up my pc and it wasn't worth the hours more of frustration so I did a reinstall on another partition and then copied over wanted files.

---

### Post by john newbuntu on 2009-12-02
If you have the clamtk gui, you could have seen all your false positive files in the quarantine and restored it.

---

### Post by linuxhippy on 2009-12-02
I still have ubuntu installed but I cannot login anymore.  How can I start ubuntu under single user mode and fix errors with the clam gui which I already have?

---

