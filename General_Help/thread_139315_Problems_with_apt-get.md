---
title: "Problems with apt-get"
date: 2006-03-03
forum: General Help
---

### Post by jeftang on 2006-03-03
I have an Acer TM 3002 working great with ubuntu 5.10. However, earlier today I was going to install the figure-making tool Xfix using apt-get. I didn't really know what I needed, so I just typed in "sudo apt-get install xfig*". Xfig installed fine, but for some reason I also got the finger-tool xfingerd. I tried to remove this using apt-get remove. Now, whenever I try using apt-get (for installing, uninstalling etc...) I get something like (this is when trying to remove xfingerd):

dpkg: error processing xfingerd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid


(Yes, I've tried reinstalling, but it just wont do)

I don't think that this does any harm to my system, I can still install other packages, but it's a bit annoying that apt-get is no longer as smooth as it used to be.

Any ideas?

I've

---

### Post by Mez on 2006-03-03
try what it tells you to do

```
sudo apt-get update
sudo apt-get install --reinstall xfingerd
sudo apt-get remove --purge xfingerd
```

---

### Post by jeftang on 2006-03-04
I've tried your suggestions, but it doesn't help. Update goes fine, install returns this (showing only the errors):

Unpacking replacement xfingerd ...
/var/lib/dpkg/info/xfingerd.postrm: line 5: /etc/init.d/inetd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 5: /etc/init.d/inetd: No such file or directory
dpkg: error processing /var/cache/apt/archives/xfingerd_0.6-4_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 5: /etc/init.d/inetd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/xfingerd_0.6-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


while remove returns this:

 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
eftang@JensMate:~$ Errors were encountered while processing:
 xfingerd

---

### Post by linstring on 2006-08-14
I have encountered the same problem. Have you found any solution for that?

---

