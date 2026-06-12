---
title: "Assistance in applying ppa"
date: 2011-03-11
forum: General Help
---

### Post by Scunnered on 2011-03-11
I had been experiencing some difficulty with PhotoPrint and requested assistance. Part of the advice suggested that I should update to the latest version by using their ppa.  This I did but somehow or other it still remained as version 0.4.2-pre2 which is that in Synaptic.

I advised of the problem and was informed that I should in Synaptic reload and then mark for update.  Having followed this I still appear to be stuck with 0.4.2.

Checking software sources > other I can see clearly the ppa information and on checking authentication see that the key is noted there.

As this is my first attempt at using ppa I suspect that I have missed something important in the process.  

As this could be the final part of converting my partner to Ubuntu I am keen to have PhotoPrint fully working. Your assistance in resolving this problem will be appreciated.

---

### Post by nothingspecial on 2011-03-11
I can't see a later version than 0.4.2-pre2 on their web page.

---

### Post by Scunnered on 2011-03-11
Thanks for your reply.

I have advised PhotoPrint regarding the old information.

The ppa is available from :

[https://launchpad.net/~amr/+archive/blackfiveimaging](https://launchpad.net/~amr/+archive/blackfiveimaging)

Hope this assists you in assisting me.

---

### Post by mcduck on 2011-03-11
> **Scunnered said:**
> Thanks for your reply.

I have advised PhotoPrint regarding the old information.

The ppa is available from :

[https://launchpad.net/~amr/+archive/blackfiveimaging](https://launchpad.net/~amr/+archive/blackfiveimaging)

Hope this assists you in assisting me.

0.4.2-pre2 *is* the latest version available from that repository, so if you are running 0.4.2 then you already have it. Actually 0.4.2-pre2 is the latest version that even exists. You are as up-to-date as you possibly can be. :D

If you want, you can run "apt-cache show photoprint" to check the exact version and status of the package.

edit: Just to make sure you aren't expecting to have a different version from what you see in Synaptic, adding a PPA (or any other repository) will add the software to Ubuntu's package Management, so Synaptic will show you the Photoprint version from that PPA. The version available in Ubuntu 10.10's own repositories is 0.4.1-3...

---

### Post by nothingspecial on 2011-03-11
I have added the repository and I get 0.4.2-pre2-1

This is what I did

```
sudo add-apt-repository ppa:amr/blackfiveimaging
sudo apt-get update
sudo apt-get install photoprint
```

When I open it, it says 0.4.2-pre2 in the title bar. From what I can tell the latest version in the ppa is still 0.4.2-pre2 but with a patch applied to improve performance. This patch is not included in the Ubuntu repository version.

I suspect you have done everything correctly and have 0.4.2-pre2-1. Maybe the title bar is misleading you.

---

### Post by Scunnered on 2011-03-12
Sorry folks to waste your time.  I totally misread a detail provided and screwed up.  Please put it down to frustration as everything that appeared to be for me was against me.

Again my thanks for your kind assistance

---

