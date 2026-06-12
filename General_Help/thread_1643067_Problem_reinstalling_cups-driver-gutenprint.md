---
title: "Problem reinstalling cups-driver-gutenprint"
date: 2010-12-11
forum: General Help
---

### Post by Extreedoc on 2010-12-11
I think my printer driver is corrupted as pictures are not printing right but print fine in Windows. I tried to reinstall cups-driver-gutenprint but a warning tells me that I am trying to install unauthorised software. What gives? I don't remember the same warning when I installed it. Any thoughts?

---

### Post by Extreedoc on 2010-12-11
Anybody?? You sure do disappear off the first page quickly on this forum don't you?

---

### Post by sikander3786 on 2010-12-11
Hi.

Regarding the issue with unauthorized software, post the output of this command.

Applications > Accessories > Terminal:

```
sudo apt-get update
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by Extreedoc on 2010-12-11
Thanks Sikander, I pasted the output into the reply ok but nothing happened when I clicked the # icon, I tried with the text selected and not selected and nothing... What should I be seeing?

---

### Post by sikander3786 on 2010-12-11
Highlight the text in your terminal, copy it then come to the forums, click new reply, paste your text, highlight it once more and click the # icon.

Or click the # icon and then paste your text.

Or if you are confused about that, just leave it. Paste your text and post it ;-)

Never mind.

---

### Post by Extreedoc on 2010-12-11
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages
  404 Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
  404 Not Found [IP: 91.189.88.37 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

How is this? Lots of issues here I think, I am getting the old amber hazard icon: "The update information is outdated..."

---

### Post by sikander3786 on 2010-12-11
And no wonder why there are that much errors. Ubuntu Intrepid 8.10 is no longer supported. Better consider upgrading to a newer version.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Or even better to do a clean install with any of the newer versions i.e, 10.04 or 10.10.

---

### Post by Extreedoc on 2010-12-11
I was wondering if that might be the problem... Was hoping to avoid it though, I suppose I'll just have to get the latest version.

Thanks for your help.
John.

---

### Post by sikander3786 on 2010-12-11
> **Extreedoc said:**
> I was wondering if that might be the problem... Was hoping to avoid it though, I suppose I'll just have to get the latest version.

Thanks for your help.
John.
You are Welcome :-)

Feel free to post if you've got any further queries regarding the upgrade/new install.

Or if satisfied, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

---

### Post by Extreedoc on 2010-12-11
Thanks again, I have posted to the general forum on which version would be best to choose and no doubt I will need help if I decide to do the install myself. I will mark this thread solved though.
John.

---

