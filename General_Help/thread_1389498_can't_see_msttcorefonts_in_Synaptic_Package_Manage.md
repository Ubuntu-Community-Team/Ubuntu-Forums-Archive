---
title: "can't see msttcorefonts in Synaptic Package Manager"
date: 2010-01-24
forum: General Help
---

### Post by InMyHumbleOpinion on 2010-01-24
Hello,

Got Karmic Koala up on running on my main computer and have been going through Beginning Ubuntu Linux, Fourth Edition.  It was printed during Jaunty Jackalope, but it looks like its information applies to most areas.

However, it says I should be able to find msttcorefonts in the Synaptic Package Manage, and it's not there.  I double checked Writer and Times New Roman and the other true type staples are not there, so it's not that it was installed with the boot disk.

Has the name of the package changed?

---

### Post by OrangeCrate on 2010-01-24
Did you try this as an alternative?

```
sudo apt-get install msttcorefonts
```

I don't currently have 9.10 installed, but when I did, I don't recall any problems with the fonts not installing with the ubuntu restricted package.

---

### Post by OrangeCrate on 2010-01-24
> **InMyHumbleOpinion said:**
> Hello,

Got Karmic Koala up on running on my main computer and have been going through Beginning Ubuntu Linux, Fourth Edition.  It was printed during Jaunty Jackalope, but it looks like its information applies to most areas.

However, it says I should be able to find msttcorefonts in the Synaptic Package Manage, and it's not there.  I double checked Writer and Times New Roman and the other true type staples are not there, so it's not that it was installed with the boot disk.

Has the name of the package changed?

Just thought of a few things...

If the sudo apt-get install command worked, ignore the rest of this post. If not, read the rest of this post...

1. Did you install the Medibuntu repository?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

2. Did you edit your sources list?

```
sudo gedit /etc/apt/sources.list
```

Uncomment the "partner" repository. (Uncomment the "backports" at the same time.)

3. Go to System > Administration > Software Sources, and make sure all of the repositories are checked.

Then try to find the package in Synaptic, or use the apt-get install command again.

Good luck.

---

### Post by InMyHumbleOpinion on 2010-01-24
Thank you. Your original suggestion worked, but I will look into the rest as it seems strange to me that they didn't show up in the GUI app.

---

### Post by OrangeCrate on 2010-01-24
> **InMyHumbleOpinion said:**
> Thank you. Your original suggestion worked, but I will look into the rest as it seems strange to me that they didn't show up in the GUI app.

You're welcome, I'm glad I could help.

:)

---

