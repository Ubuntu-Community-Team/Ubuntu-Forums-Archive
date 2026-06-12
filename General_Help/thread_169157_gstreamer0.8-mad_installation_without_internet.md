---
title: "gstreamer0.8-mad installation without internet?"
date: 2006-05-02
forum: General Help
---

### Post by 47.46.45 on 2006-05-02
Heya guys,
0 experience with ubuntu or pretty much any other linux distro. I've searched around and have a vague idea of how to install the gstreamer0.8-mad package to add MP3 support, but I don't have internet access on the computer in question. This means I can't add the other repositories, which means I can't seem to download the package.
I can transfer files between this computer and the ubuntu one using a USB drive.
Can anyone suggest a way to do this? Thanks very much for any help.
Cheers,
-Sam

---

### Post by Jason_25 on 2006-05-02
Sure, visit [this]("http://packages.ubuntu.com/") page and find the deb and it'd dependancies and download them.  To install a deb
```

sudo dpkg -i nameofdeb.deb

```

---

### Post by 47.46.45 on 2006-05-02
Great, I installed both the libaries and the package and my music player will now import and play MP3's. Thanks a lot!

---

