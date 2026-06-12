---
title: "Strange problems with upgrade..."
date: 2010-10-02
forum: General Help
---

### Post by toxic9813 on 2010-10-02
Hey, after successfully upgrading my PC to Ubuntu 10.10, I told my friend about it and he said he wanted to do that. Not being linux-savvy enough to use update-manager -d, I went over and did it. With this low bandwidth internet the download took a few hours, and the install went without a hitch. It asked to reboot, and I did. Instead of booting into the Ubuntu GUI, it went into the command line mode (for lack of a better word in my vocab :P).

I looked it up and there were commands to get back into GUI, and I tried them. It tells me it's missing "display". Upon further research and putting in more commands after more reboots, I basically learned that it was missing everything needed for a GUI. *It did not even have root* I had to get a command to download that as well.

Seeing that was a waste of time and energy, I decided to burn a disk of 10.10, and it would not get past the Ubuntu Logo after selecting "Install Ubuntu 10.10"

Burned a disk of 10.04.1 (whatever the lastest 10.04 is) it did the same.

I finally found my original free shipped Ubuntu 10.04 LTS disk and it finally installed.


Can anyone explain to me what was going on? (expecting a tl;dr or two)

---

### Post by Old_Grey_Wolf on 2010-10-02
Did you use md5sum to check the downloaded iso file for errors? Did you use md5sum to check the CD for errors? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

