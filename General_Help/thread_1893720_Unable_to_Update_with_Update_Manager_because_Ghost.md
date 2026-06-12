---
title: "Unable to Update with Update Manager because Ghostscript Update is unable to be found"
date: 2011-12-10
forum: General Help
---

### Post by blitzenflitzen on 2011-12-10
I'm trying to use the Update Manager to update my computer as usual. But I'm getting the following error message:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.04~dfsg-0ubuntu11.2_all.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.04%7Edfsg-0ubuntu11.2_all.deb") 404  Not Found [IP: 91.189.92.181 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_9.04~dfsg-0ubuntu11.2_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_9.04%7Edfsg-0ubuntu11.2_amd64.deb") 404  Not Found [IP: 91.189.92.181 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.04~dfsg-0ubuntu11.2_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.04%7Edfsg-0ubuntu11.2_amd64.deb") 404  Not Found [IP: 91.189.92.181 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.04~dfsg-0ubuntu11.2_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.04%7Edfsg-0ubuntu11.2_amd64.deb") 404  Not Found [IP: 91.189.92.181 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.04~dfsg-0ubuntu11.2_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.04%7Edfsg-0ubuntu11.2_amd64.deb") 404  Not Found [IP: 91.189.92.181 80]

---

### Post by Krytarik on 2011-12-11
Apparently, your package database is outdated. Either update it by clicking on "Check" in Update Manager, then choose "Install Updates" again; or use the command line equivalents:
```
sudo apt-get update
sudo apt-get upgrade
```Regards.

---

### Post by oldtimer7777 on 2011-12-11
You are running an Ubuntu OS that is at EOL. (End of Life) and the repos are gone.

Try using a version of Ubuntu that isn't EOL like:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **blitzenflitzen said:**
> I'm trying to use the Update Manager to update my computer as usual. But I'm getting the following error message:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.04~dfsg-0ubuntu11.2_all.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.04%7Edfsg-0ubuntu11.2_all.deb") 404  Not Found [IP: 91.189.92.181 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_9.04~dfsg-0ubuntu11.2_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_9.04%7Edfsg-0ubuntu11.2_amd64.deb") 404  Not Found [IP: 91.189.92.181 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.04~dfsg-0ubuntu11.2_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.04%7Edfsg-0ubuntu11.2_amd64.deb") 404  Not Found [IP: 91.189.92.181 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.04~dfsg-0ubuntu11.2_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.04%7Edfsg-0ubuntu11.2_amd64.deb") 404  Not Found [IP: 91.189.92.181 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.04~dfsg-0ubuntu11.2_amd64.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.04%7Edfsg-0ubuntu11.2_amd64.deb") 404  Not Found [IP: 91.189.92.181 80]

---

### Post by Krytarik on 2011-12-11
> **oldtimer7777 said:**
> You are running an Ubuntu OS that is at EOL. (End of Life) and the repos are gone.[]("https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")
Ah, damn, right! Didn't notice the "9.04" stuff in the file names. :-P

End of Life of Jaunty 9.04 was already October last year:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by oldtimer7777 on 2011-12-11
> **Krytarik said:**
> Ah, damn, right! Didn't notice the "9.04" stuff in the file names. :-P

End of Life of Jaunty 9.04 was already October last year:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I didn't either when I first read it, to tell you the truth. After looking at it a couple of times, as tired as I feel right now...  But then I saw the 9.04.  EOL = S.O.L

:lolflag:

---

### Post by Krytarik on 2011-12-11
> **oldtimer7777 said:**
> ... as tired as I feel right now...Tell *me* about tired, it's 6:34 in the morning here. :D
> **oldtimer7777 said:**
> EOL = S.O.L
Needed to lookup "S.O.L.", great! :popcorn::D

---

