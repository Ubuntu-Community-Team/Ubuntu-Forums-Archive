---
title: "How to recover encrypted files from old ubuntu partiton"
date: 2011-05-18
forum: General Help
---

### Post by death__machine on 2011-05-18
Hi,
I recently changed my laptop and wanted to access the files I had on my old notebook harddisk so I got an enclosure. Right now I only have windows installed, so I had to install Diskinternals linux reader to view the linux partition. Now the problem is the folder inside of my username folder (downloads,etc.) I think they're encrypted. All of them start with ecrpyt_fnek_encrypted. Is there a way to recover these from windows?

---

### Post by death__machine on 2011-05-19
I followed this guide [http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)
and always end up with the error 
| Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs> |

and on using this command | ecryptfs-mount-private|
i get
|ERROR: Encrypted private directory is not setup properly|

any suggestions?

edit: Yes I installed ubuntu, I figured it cant be done from windoze whatsoever.

---

### Post by death__machine on 2011-05-19
bump

---

### Post by Megaptera on 2011-05-20
Is this any help?
[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

---

### Post by linuxinstalledfromhdd on 2011-05-20
You got some time?

[http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/](http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/)

---

### Post by death__machine on 2011-05-20
@megaptera I have tried the command sudo ecryptfs-mount-private, didnt work

@linuxinstalledfromhdd That recovery program can actually recover encrypted files? Anyways gonna give it a shot...

---

