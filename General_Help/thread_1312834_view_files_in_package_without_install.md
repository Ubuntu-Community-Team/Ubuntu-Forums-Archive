---
title: "view files in package without install"
date: 2009-11-03
forum: General Help
---

### Post by alphaniner on 2009-11-03
Is there a way to see what files are included in a package (from the repos) without installing it?

---

### Post by klemes on 2009-11-03
I think 'apt-cache showpkg <name of the packet>' does that.

---

### Post by klemes on 2009-11-03
No sorry I was wrong I dont think there is one.One solution is to install it and then use 'dpkg -L <name of the packet>.
The other is to download the package and open it using gdebi-gtk which in turn you willl show you the files included in the deb package.


Edit: Wait a minute i FOUND IT:

```
dpkg -c <name of the packet>.deb
```

---

### Post by alphaniner on 2009-11-03
Thanks, that does the trick.  I just wish there was a way to do it without downloading the package.  It's a very handy feature.

---

### Post by QLee on 2009-11-03
> **alphaniner said:**
> Is there a way to see what files are included in a package (from the repos) without installing it?

Looking at this it seemed to me that you might be asking to look into the actual package (.deb) itself.

Yes, it is an archive, you'll probably find three files, two tar.gz's and a binary.

Is that what you wanted?

Edit: Ah, I see that it is not, what you wanted, sorry for the noise.

---

### Post by QLee on 2009-11-03
> **alphaniner said:**
> Thanks, that does the trick.  I just wish there was a way to do it without downloading the package.  It's a very handy feature.

I'm sorry I have just realised that you want to look at the list of installed files when you say "what files are included".

You could open the archive from the repository and look at the data.tar.gz file in it but I'm not sure if that is any faster than actual download, it just means you don't have the .deb on your system.

---

### Post by michy99 on 2009-11-03
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and find the package you are interested in. At the bottom of the page, next to the download link, is a link to a list of the files included in the package.

You can also search to find what packages contain a given file.

---

### Post by alphaniner on 2009-11-05
> **michy99 said:**
> Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and find the package you are interested in. At the bottom of the page, next to the download link, is a link to a list of the files included in the package.

You can also search to find what packages contain a given file.

Stupendous!  Thanks.

---

