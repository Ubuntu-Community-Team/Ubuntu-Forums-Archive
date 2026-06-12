---
title: "Remove XGL/Compiz?"
date: 2006-06-20
forum: General Help
---

### Post by Cable on 2006-06-20
I felt like seeing what it was all about...and I don't really want to continue using XGL/Compiz.  How do I revert my setup back to what I was using before?  I was sure to make backups of the few files I edited during the XGL/Compiz installation process, so I have those.  But, I know I also had to install "updated" packages to get this running.  How do I revert back to the old ones?  I saw someone posted a list (of a Dapper base install) for someone else that was very long saying filter out the packages that shouldn't be there...but I haven't the first clue what to do with that.  Help please?

That list I'm talking about is [here]("http://packages.ubuntu.com/dapper/allpackages.en.txt.gz").

---

### Post by mindwarp on 2006-06-21
You can keep the packages you installed without interfereing with your old setup, but you can use synaptic and search for xgl and remove it from there, along with compiz if you just want to make sure they are off of your system.  You probably need to revert your gdm.conf to the old version, and edit your gnome session properties and remove the compiz lines also.

---

