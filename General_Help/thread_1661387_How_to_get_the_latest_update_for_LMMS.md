---
title: "How to get the latest update for LMMS?"
date: 2011-01-06
forum: General Help
---

### Post by pc999 on 2011-01-06
Hi,

I did installed LMMS ([http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)) in Ubuntu 10.10, but it did installed the 0.4.5 version which is not very stable, I wanted to install the latest 0.4.9 (which in the Windows version is much better than the 0.4.5).

Anyone knows how can I do it? (if it is a method that work with other apps it would be even nicier :-D)

Thanks in advance.

---

### Post by Joe of loath on 2011-01-06
You will have to:

A. Build it from source.
B. Install it from a PPA, assuming one exists.

Personally I'd go for source, but a PPA might be easier, assuming you can find one.

---

### Post by marl30 on 2011-01-06
Here is the link to the PPA: [https://launchpad.net/~tobydox/+archive/lmms](https://launchpad.net/~tobydox/+archive/lmms). This is version 0.4.8. It seems quite stable to me. I've been playing around with it for the past month.

---

### Post by pc999 on 2011-01-07
> **marl30 said:**
> Here is the link to the PPA: [https://launchpad.net/~tobydox/+archive/lmms]("https://launchpad.net/%7Etobydox/+archive/lmms"). This is version 0.4.8. It seems quite stable to me. I've been playing around with it for the past month.


Thanks, I dont know how to build from source and I dont really know what to do with that PPA.

There is somethings like Opera that you click it and it take you to SoftwareCenter, you try to add that PPA link to the repositories, but it didnt worked...

---

### Post by HolyPhoenix on 2011-03-09
copy these commands into your terminal

```

sudo add-apt-repository ppa:tobydox/lmms
sudo apt-get update
sudo apt-get install lmms
```

That should do it.  :p  It was updated this month to 4.10, so enjoy.

---

