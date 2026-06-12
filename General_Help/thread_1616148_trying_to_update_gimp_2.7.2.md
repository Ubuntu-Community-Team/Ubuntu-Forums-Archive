---
title: "trying to update gimp 2.7.2"
date: 2010-11-07
forum: General Help
---

### Post by eddarl on 2010-11-07
I am not sure what forum to post this to.
I have ubuntu 10.10 installed.

Trying to update running update manager. update package is 2.7.3-2010072701~mm 
previous gimp package was 2.7.3-2010072701~ll

update proceeds until package operation failed!

Details
installArchives() failed: 
... 350027 files and directories currently installed.)

Preparing to replace gimp 2.7.3-2010072701~ll (using .../gimp_2.7.3-2010072701~mm_amd64.deb) ...

Unpacking replacement gimp ...


dpkg: error processing /var/cache/apt/archives/gimp_2.7.3-2010072701~mm_amd64.deb (--unpack):

 trying to overwrite '/usr/lib/gimp/2.0/plug-ins/file-xmc', which is also in package gimp-plugin-registry 3.2-1

dpkg-deb: subprocess paste killed by signal (Broken pipe)

Processing triggers for menu ...

Errors were encountered while processing:

 /var/cache/apt/archives/gimp_2.7.3-2010072701~mm_amd64.deb


I am at a loss at what I can do.

---

### Post by jcolyn on 2010-11-07
Gimp 2.7 does not show up in the repos for me. Did you download the .deb file elsewhere?

If so you may have to un-install before re-installing..

---

### Post by LepeKaname on 2011-08-21
You could force it to install it this way:

```
dpkg -i --force-overwrite /var/cache/apt/archives/gimp_2.7.3-2010072701~mm_amd64.deb
```

In my case was the other way around, while trying to install gimp-plugin-registry, but
it worked for me so far... however I'm not sure if this may break something...

---

