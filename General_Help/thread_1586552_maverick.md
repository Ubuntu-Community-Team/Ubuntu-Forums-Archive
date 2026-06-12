---
title: "maverick"
date: 2010-10-02
forum: General Help
---

### Post by Noorani on 2010-10-02
Hi,
I have decided to install the new ubuntu maverick meerkat which I downloaded (the beta release, I know the rc has also been put available). So my question is that if I install this beta release will it be updated to the new rc and later on to the main release when it is made available or will I have to download the main release again on the tenth? 
The other thing is I have some applications that I have installed on my computer that runs Lucid( This is the computer where I want to install maverick) so I want to be able to automatically download and install those applications when I install maverick.
Will using these commands do this for me:
sudo dpkg --get-selections > app-backup-list.txt

[FONT=Book Antiqua]after installing maverick:[/FONT]
sudo dpkg --get-selections < app-backup-list.txt sudo apt-get -y update sudo apt-get dselect-upgrade

---

### Post by Rubi1200 on 2010-10-02
Personally, I recommend you wait a few more days until the distribution release on the 10th of October.

The release candidate still has some major bugs which need to be worked out and is not recommended for a stable production machine.

In the meantime, backup any data you need and get ready for a fresh installation.

---

