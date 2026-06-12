---
title: "SAMBA network mount charset issues"
date: 2010-02-07
forum: General Help
---

### Post by biofoder on 2010-02-07
I have problem with samba and my network harddrives. My server have Ubuntu Server installed, and my desktop has Karmic Koala. I use cifs when mounting the harddrives from my server to my desktop. But my charsets seem to be messed up.
Everything seems fine when I check files on my server using smb:// from desktop computer or directly from the server using ls. But when it is mounted with cifs, all chars are not correctly displayed. My both machines have UTF8 when I check $LANG, and my files contain characters with  ISO-8859-1. When I create files using the mounted drive, there is invalid encoding when viewing with ssh or smb://.

Where is the problem? Is it the mounting that is incorrect as everything is working fine with smb and on server? How do I fix it so that I can mount a hdd and still create and view characters with charset ISO-8859-1?

Also, when checking the file names with a windows system, they seem alright. Not with my media streamer (Popcorn Hour A-100).

Oh, and is there any danger that viewing or editing the files with my mounted drive will corrupt my files?

Thanks!

---

