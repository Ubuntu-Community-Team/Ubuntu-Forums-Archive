---
title: "HTPC with concatenated drives"
date: 2012-08-15
forum: General Help
---

### Post by netsense on 2012-08-15
G'day.

I built a HTPC from a mITX mobo and a couple of 2.5" Hard Drives of 200 and 250GB capacity respectively, which I concatenated during the install. Worked really well, except I could never get the USB DVB card to work.

And of course didn't back up.:(

So of course now we have some sort of file-system problem that picks up an error on boot (can't mount /temp, which I'm assuming is bad), and when it does boot (after ignoring the error) I can't write to the drive across samba, and it won't open any of the media files on it - and there's a reasonable number. It will open up media files on a remote shared drive. 

So I thought OK, let's boot it from an Ubuntu CD, mount the concatenated file-system (CFS for now), back up the file, then try to repair. Except for one little problem - I have no clue as to how to mount the CFS. Live Ubuntu's file-manager sees the 105MB boot partition, but nothing else.

I'd love if if someone smart could solve this problem.

---

