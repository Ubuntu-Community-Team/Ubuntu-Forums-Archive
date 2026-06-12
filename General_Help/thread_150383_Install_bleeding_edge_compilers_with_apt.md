---
title: "Install bleeding edge compilers with apt"
date: 2006-03-25
forum: General Help
---

### Post by bigqueso on 2006-03-25
Hi.  I really like how I'm able to install GCC 3.3, 3.4, and 4.0.2 all at the same time.

Is there a way to pull in newer versions like 4.0.3 and 4.1.0 and have them live along side the others using the apt tools (i.e. not download, untar, configure, make, install)?

Thanks,
James

---

### Post by Sutekh on 2006-03-27
The latest version of the GNU C compiler in the Breezy repositories is 4.0.2.

The Dapper repositories have the 4.0.3 version, you *could* get it from there using apt-get if you wished.  Just make sure you don't install *too* much from the dapper repositories or things could get nasty.

But as for any later versions, you would need to either find a compatible .deb package from the internet and install it manually or compile it from source.

---

