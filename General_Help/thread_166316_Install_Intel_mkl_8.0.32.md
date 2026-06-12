---
title: "Install Intel mkl 8.0.32"
date: 2006-04-26
forum: General Help
---

### Post by baleine on 2006-04-26
Hello, 

I am not able to install mkl 8.0.32 library for the intel ifort compiler (Dapper beta release). I run the "install.sh" script (provided by intel) but it failed.

I did encounter the same trouble when trying to install the ifort compiler 9.0 : the "install.sh" script did not work.

 However, I used succesfully the steps descibed by Gappy in the HOW TO
"[http://ubuntuforums.org/showthread.php?t=89571]("http://ubuntuforums.org/showthread.php?t=89571")
(many thanks to Gappy).

I wonder if someone has modified the csh script called make9 provided by Gappy so that it works also for the mkl installation (I do not masterize script at all!)...

Thanks, Baleine

---

### Post by wyxsdu on 2006-08-21
I paste a new thread on this subject.

In fact, you only need install it without sudo.
after install it, you can "sudo copy -r mkl/8  /opt/intel/."

For intel compiler, we can also install it like this method.

---

