---
title: "how do I reinstall grub2 from an ubuntu 9.10 live cd?"
date: 2010-02-14
forum: General Help
---

### Post by pythonscript on 2010-02-14
I want to reinstall windows to its partition on my computer, but I want to be able to restore grub2 afterwards. I use a lot of custom scripts in the /etc/grub.d/ directory on my ubuntu partition, so how can I reinstall grub to the MBR using those specific scripts? Just running "sudo install-grub" or "sudo update-grub" doesn't work for me (I don't know the exact problems, but I can't reproduce it right now). If there's a way to install just the defaults (without overriding my custom scripts!) maybe I can just do that, but I'd really like to put the live cd, run a few commands, and install those custom scripts to the mbr and be on my way. Thanks for the help!

---

### Post by eraevous on 2010-02-14
Do either of these help?
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

