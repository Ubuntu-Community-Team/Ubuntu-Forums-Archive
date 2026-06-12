---
title: "dual boot assistance"
date: 2009-11-07
forum: General Help
---

### Post by sites on 2009-11-07
I'm currently dual booting a laptop with Windows XP Pro and Karmic.  When i boot into Karmic and open a file browser, the Windows disc partition shows up in the directory on the left.  The drive doesn't auto-mount, and that's fine.  But i don't even want it showing up in the file browser.  How can i prevent this?

---

### Post by Zoot7 on 2009-11-07
Install the tool ntfs-config
```
sudo apt-get install ntfs-config
```

And then use that disable write support. It'll mean you can no longer write to ntfs partitions.

There might be a more elegant way but that's what I'd try.

---

### Post by sites on 2009-11-19
Thanks, but i'd rather not disable that feature permanently.

---

