---
title: "Problem with synaptic"
date: 2006-02-27
forum: General Help
---

### Post by bardu on 2006-02-27
Hi all,

first off all, for a couple days I have Ubuntu 5.10 on my Toshiba Satellite A10. Everything looks and works great so far, which I couldn't say about my previous insatllations Suse and Soloaris 10.

Since I downloaded some packages yesterday, I remember the last one was acroread, I get today this warning message when I start synaptic:
```
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```

Can someone please tell me what to do in this case.

Another problem: Ubuntu doesn't restart the machine. After Ubuntu is down the screen turn black and freezed.

Thanks in advance for any advice.

Stephan

---

### Post by aysiu on 2006-02-27
Follow these instructions, especially the bottom bit:
[http://www.psychocats.net/linux/sources](http://www.psychocats.net/linux/sources)

Otherwise, have you tried shutting down from the command-line? I believe the command is ```
sudo shutdown -h now
```

---

### Post by bardu on 2006-02-28
Thanks aysiu for that link. It fixt my problem with synaptic.

Stephan

---

### Post by aysiu on 2006-02-28
Are you able to shut down from the command-line?

---

