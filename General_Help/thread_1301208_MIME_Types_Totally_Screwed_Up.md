---
title: "MIME Types Totally Screwed Up"
date: 2009-10-25
forum: General Help
---

### Post by abyrne on 2009-10-25
Hi,

  I recently did a minimal install of Karmic and then installed lxde. Everything was fine... mostly. When I go to pop open PCManFM, everything, whether it was a PDF, MP3, Python script, or RTF, all showed with the application/octet-stream MIME type (which PCManFM classifies as "unknown"). I've used PCManFM before, so I know that there's usually a "Use selected application as default..." option if you right-click a file and click "Open with another application". It wasn't there this time (which I'm guessing is because it is classified as unknown). So I've done everything Google has told me to do. Re-install the file package, update-mime-database, delete MIME cache file, log-in, log-out.... It never ends. 

Right now, I don't know whether the problem is with PCManFM, MIME itself, or some nameless package or config file. If anyone has any ideas, please speak up. 
Thanks in Advanced!

---

### Post by abyrne on 2009-10-26
bump

---

### Post by abyrne on 2009-10-26
BUMP Again

---

### Post by abyrne on 2009-10-27
BUMP

Anyone? Please?

---

### Post by lazarev on 2009-11-03
I have exactly the same problem.

Stripped-down command line karmic -> LXDE-> Screwed MIME types in pcmanfm.

---

### Post by lazarev on 2009-11-03
It seems that I have found the solution:

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344)

Download the .deb file from:

[http://www.2shared.com/file/8810097/8692f477/pcmanfm_052-1_i386.html](http://www.2shared.com/file/8810097/8692f477/pcmanfm_052-1_i386.html)

and reinstall (sudo dpkg -i pcmanfm_0.5.2-1_i386.deb) pcmanfm from that package.

---

