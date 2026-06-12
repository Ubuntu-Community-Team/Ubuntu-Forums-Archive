---
title: "Ubuntu permission denied"
date: 2011-02-28
forum: General Help
---

### Post by melodyflow on 2011-02-28
I am installing ubuntu to amazon EC2 by following the steps at [http://www.youtube.com/watch?v=eZI6URU-Jak](http://www.youtube.com/watch?v=eZI6URU-Jak)   The installation works fine.

Then I want to gain Remote Desktop Access to Ubuntu, so I follow 

[http://aws-musings.com/4-easy-steps-to-enable-remote-desktop-on-your-ubuntu-ec2-instance/](http://aws-musings.com/4-easy-steps-to-enable-remote-desktop-on-your-ubuntu-ec2-instance/)

However, fail at sudo /usr/lib/nx/nxsetup --install   due to this file is missing.

I then use putty, navigate into /usr/lib/nx to run command below.
wget [https://bugs.launchpad.net/freenx-server/+bug/576359/+attachment/1378450/+files/nxsetup.tar.gz](https://bugs.launchpad.net/freenx-server/+bug/576359/+attachment/1378450/+files/nxsetup.tar.gz)

But, it always come out with permission denied issue

I also try to upload the .tar.gz file via winscp to any of the possible directories.

All fail with permission denied issue.

-----------

Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 3

----------

Wondering how to fix this issue?

---

### Post by melodyflow on 2011-02-28
ok, it think problem fixed for wget with permission issue.

Useful thread: [http://ubuntuforums.org/showthread.php?t=922360](http://ubuntuforums.org/showthread.php?t=922360)

---

