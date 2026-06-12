---
title: "sources.list syntax"
date: 2011-02-20
forum: General Help
---

### Post by Mariane on 2011-02-20
I got libdvdcss2 via lenny (Debian) packages, because I wanted to watch a DVD and it didn't play in vlc (the introductory part played, displaying the movie company logo, and then vlc stopped). 

To do this I added to my source.list:
```

deb http://unofficial.debian-maintainers.org/ lenny main contrib non-free restricted
deb-src http://unofficial.debian-maintainers.org/ lenny main contrib non-free restricted

```

The only packages I got this way were libdvdcss2 and dmo-archive-keyring because I needed this package to get the key to the repository (why make things simple when you can make them complicated?). 

What is the correct syntax for Kubuntu? As an example the first two lines in my sources.list are: 

```

deb http://is.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://is.archive.ubuntu.com/ubuntu/ lucid main restricted

```

What will happen the next time I update if I have packages which source has gone from sources.list? 

What are the risks of adding packages from a Debian distribution? 

Last but not least, why are there legal problems to watching a DVD on a computer when it's perfectly legal to watch it on a DVD player? 

Mariane

---

### Post by snowpine on 2011-02-20
Never mix Debian and Ubuntu packages. They are not compatible.

Follow these instructions for DVD playback:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Mariane on 2011-02-20
Perfect :popcorn: 
Thankx a lot

Mariane

---

