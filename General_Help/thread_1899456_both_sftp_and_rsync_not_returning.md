---
title: "both sftp and rsync not returning"
date: 2011-12-23
forum: General Help
---

### Post by 317070 on 2011-12-23
Hello,

I am trying to upload my code to a server through a tunneled SSH (SSH after SSH)
So first I run this line:
```
sudo ssh jdgrave@ssh.gent.be -L 22:clsnn007:22
```and then in a seperate terminal I run this bash script:
```
sftp jdgrave@localhost <<EOF
cd /mnt/snn_gluster/usr/jdgrave/src/
put -R /media/Matlab/Thesis/Software/SVN/QuadrupedSim
quit
EOF

```The problem is that sftp doesn't return the console after executing the quit command, it just hangs. When using ctrI-C It shows "interrupt", but still doesn't return to the console.
```
sftp> quit
Interrupt  
Interrupt  
Interrupt  
Interrupt 
```I have the same problem when using rsync (eg. not returning after running succesfully), so I presume this is something more fundamental? This is ubuntu 10.10 btw.

---

### Post by Lars Noodén on 2011-12-23
Would it help sftp if you used the [-b](http://manpages.ubuntu.com/manpages/oneiric/en/man1/sftp.1.html) batch option?

---

### Post by 317070 on 2011-12-23
> **Lars Noodén said:**
> Would it help sftp if you used the [-b]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/sftp.1.html") batch option?
No, I have the same problem if I use sftp manually, or the -b option. Apperently scp has the same problem. And ssh too :confused:.

Probably that last one is the main issue. Is there something that could prevent ssh from closing properly?

---

