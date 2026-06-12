---
title: "Thank You!!! (Tizen SDK Install)"
date: 2012-09-06
forum: General Help
---

### Post by cfg83 on 2012-09-06
Hello -

(assuming I don't have URL privileges in my first post)

While following these instructions :

    https : // developer . tizen . org / sdk / installing - sdk - ubuntu

This command ...

```
$ sudo apt-get install qemu-kvm binutils-multiarch \
debhelper fakeroot realpath gettext procps xsltproc \
libdbus-1-3 liblua5.1-0 libexif12 libcurl3
```... was leading to "404 not found" errors : I was going to post a thread asking for your help, but I searched as follows : 

     "apt-get" 404 not found

The search led me to these threads :

    http : // ubuntuforums . org / showpost.php ? p=11877239&postcount=1
    http : // ubuntuforums . org / showthread.php ?t=1971932

Which led me to the simplest fix.  I ran an update first :

     ```
sudo apt-get update
```It turns out the Tizen SDK installation instructions assume(?) that the OS is up to date.  If the OS is NOT up to date then it makes mistakes when it pulls from places like this : 

    http : // security . ubuntu . com / ubuntu / pool / main / q /qemu-kvm/

Specifically it was asking for a version of this file that was not in the above folder : 

    qemu-common_0.14.0+noroms-0ubuntu4.6_all.deb

Hope that makes sense,

THANK YOU!!!

cfg83

---

