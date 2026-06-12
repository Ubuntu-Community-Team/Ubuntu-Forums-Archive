---
title: "lxdvdripOnBreezyHowto missing libdvdcss2 problem"
date: 2006-02-01
forum: General Help
---

### Post by rconway on 2006-02-01
Hi,

I am followiing the instructions on [https://wiki.ubuntu.com/lxdvdripOnBreezyHowto](https://wiki.ubuntu.com/lxdvdripOnBreezyHowto), but I am experiencing the following error at the first hurdle:

$ sudo apt-get install transcode dvdbackup dvdauthor mjpegtools mpgtx buffer mplayer-586 libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

Any ideas? Which repos does/did libdvdcss2 come from?
Do I need it?

Any help is much appreciated.

Thanks,
Richard.

---

### Post by Jason_25 on 2006-02-01
This information comes from [this]("https://wiki.ubuntu.com/RestrictedFormats") page.

```

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```

---

### Post by Perfect Storm on 2006-02-01
Add PLF to your sourcelist.

```
sudo gedit /etc/apt/sources.list
```

Add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install libdvdcss2

```

---

### Post by rconway on 2006-02-01
Thanks for the two (very prompt) suggestions.
Which is the 'correct' solution?
I have concerns over adding too many disparate repositories to my sources - What happens when the same package is provided by more than one repos and a conflict arises?
I shall proceed with the PLF repos.

---

