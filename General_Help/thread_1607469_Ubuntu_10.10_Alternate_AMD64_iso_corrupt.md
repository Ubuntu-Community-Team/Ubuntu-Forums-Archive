---
title: "Ubuntu 10.10 Alternate AMD64 iso corrupt?"
date: 2010-10-27
forum: General Help
---

### Post by Captain Chirac on 2010-10-27
Hello.

I'm trying to install 10.10 Alternate AMD64 on a laptop (eMachines e510) in order to then install a minimal desktop.
I haven't found anything about this issue outside of this page, which describes the problem I encounter well: [https://bugs.launchpad.net/ubuntu/+bug/635613](https://bugs.launchpad.net/ubuntu/+bug/635613)
It basically happens right when the base system installation starts.
The link shows screenshots of it.
I tried burning a CD at minimum speed, and the CD check indeed says the files are corrupt.

Is it a know issue, or am I the only one having this problem?

Thanks.

---

### Post by mister_playboy on 2010-10-27
You might try installing from USB rather than CD.  If a bad burn is the issue, this would eliminate the problem.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Captain Chirac on 2010-10-28
Yeah, I did that at first, and it stopped when trying to mount the CD-Rom. It REQUIRED a CD for some reason. Absurd.
I also tried with two CDs, one burnt at full speed, and then the other one at minimum speed.
Didn't help.

---

### Post by theozzlives on 2010-10-28
I'd say run an md5sum on the ISO. Line noise or EMI could've corrupted your download.

---

### Post by Captain Chirac on 2010-10-28
I can try that, but I'll still have to burn a third CD, as the installation will not accept to just run from the USB stick.
Anyway, I'll check and redownload the ISO, thanks.

---

### Post by gmargo on 2010-10-28
You don't need to redownload the iso.  If it's corrupted you can fix it in place.

First check the md5 sum of the iso, here's the file:  [http://releases.ubuntu.com/10.10/MD5SUMS](http://releases.ubuntu.com/10.10/MD5SUMS)
Run "md5sum -c MD5SUMS" to check the iso.  Ignore the messages for the missing ones.

Now, if the md5 check fails for your iso, you can either use the bittorrent file, and let your bittorrent client fix it up, or use **zsync** to update that iso (install the **zsync** package first).  zsync "chunks" the file similar to bittorrent and downloads only the bad blocks, keeping all the good blocks.
```

zsync http://releases.ubuntu.com/10.10/ubuntu-10.10-alternate-amd64.iso.zsync

```

---

### Post by Captain Chirac on 2010-10-31
The ISO was effectively corrupted, probably due to a problem that occured during the download.
Thanks for your help!

---

