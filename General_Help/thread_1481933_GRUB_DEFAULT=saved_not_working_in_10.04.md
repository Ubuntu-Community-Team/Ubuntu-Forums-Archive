---
title: "GRUB_DEFAULT=saved not working in 10.04"
date: 2010-05-13
forum: General Help
---

### Post by lmarmisa on 2010-05-13
I used to define in Ubuntu 9.10 the option

**GRUB_DEFAULT=saved**

in the **/etc/default/grub** configuration file.

So, the system started with the last system that I had selected in the GRUB menu. It worked fine and I loved this feature.

But, it seems than this option does not run anymore in Ubuntu 10.04. Is it a bug of Lucid Lynx or is it a problem that affects only my installation?. 

Thanks in advance for the answers,

Luis

---

### Post by nikhilbhardwaj on 2010-05-13
try
```

sudo update-grub

```

---

### Post by lmarmisa on 2010-05-13
> **nikhilbhardwaj said:**
> try
```

sudo update-grub

```

Yes, of course, I have typed this command several times with no success.

---

### Post by lmarmisa on 2010-05-16
Bump.

---

### Post by john newbuntu on 2010-05-16
In this post on grub2 ( [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) ), drs305 mentions adding 
GRUB_SAVEDEFAULT=true
and
GRUB_DEFAULT=saved
in order for this functionality to work in the newer grub (1.98)

---

### Post by lmarmisa on 2010-05-16
Thanks for the reference, John. 

I have added the new line **GRUB_SAVEDEFAULT=true** to the file **/etc/default/grub** and I have typed the command **sudo update-grub.**  Everything is correct now.

Best regards,

Luis

---

