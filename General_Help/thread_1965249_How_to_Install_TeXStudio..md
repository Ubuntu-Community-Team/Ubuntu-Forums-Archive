---
title: "How to Install TeXStudio."
date: 2012-04-25
forum: General Help
---

### Post by Phugoid on 2012-04-25
I'm a relatively new user of Ubuntu, and I'm just trying to get all my favourite software packages up and running, just like I had on my old Windows 7 OS.

At the moment I'm having trouble trying to install TexStudio - my LaTeX editor of choice.

So, I basically need some idiot proof instructions which I can follow which will lead me to having TexStudio installed and ready to go.

I'm running 11.10.

---

### Post by Chris_82 on 2012-11-04
**As of Ubuntu 12.10** it is in the repository:
[https://apps.ubuntu.com/cat/applications/texstudio/](https://apps.ubuntu.com/cat/applications/texstudio/)

Install it with apt-get or the Software Center.
Or even using [this apt link]("apt://texstudio").

**For earlier Ubuntu versions** do the following:
Go to [http://texstudio.sourceforge.net/#download](http://texstudio.sourceforge.net/#download)
and download the deb package file for your Ubuntu version.

Then either double click the deb file or install it in a terminal with ```
sudo dpkg -i texstudio_2.5_amd64.deb
```

---

