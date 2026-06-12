---
title: "VMware 3.1.3 On Ubuntu - Install"
date: 2011-01-09
forum: General Help
---

### Post by Zer0- on 2011-01-09
So, I am currently running Ubuntu 10.10,  and decided to run VMware from Ubuntu to use another OS (BackTrack4).

Now, I downloaded the bundle and everytime I try and run it I get this error:

"*root access is required for the operations you have chosen.*"


Any ideas/Help will be greatly appreciated :D:D

Zer0-

---

### Post by CharlesA on 2011-01-09
What did you download and from where?

---

### Post by Zer0- on 2011-01-09
I downloaded VMware Player (A virtual machine) from this site:
[https://www.vmware.com/](https://www.vmware.com/)

(The Ubuntu bundle)

---

### Post by Zer0- on 2011-01-09
Bumping this up a bit, I'm still looking for a reply :(

---

### Post by CharlesA on 2011-01-09
Did you already install it or get the error when you were trrying to install it?

---

### Post by hokiejp on 2011-01-09
In the terminal, cd to the directory where the .bundle file is and type

sudo sh <file_name>

For me <file_name> is VMware-Player-3.1.3-324285.x86_64.bundle, but it might be different for you depending on your version of Ubuntu.  You will be prompted to enyer your password.

---

### Post by CharlesA on 2011-01-09
You can just install it by using this:

```
sudo ./VMware-Player-3.1.3-324285.x86_64.bundle
```

No need for sh, as long as it has execute permission.

---

