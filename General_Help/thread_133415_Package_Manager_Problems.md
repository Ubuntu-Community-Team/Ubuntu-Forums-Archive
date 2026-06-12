---
title: "Package Manager Problems"
date: 2006-02-20
forum: General Help
---

### Post by Karail on 2006-02-20
Hi,

I have just installed amd64 ubunto 5.10 on one of the servers in our offices and am trying to finalize the installation by installing the kernel-headers and kernel-image for em64t smp, as the machine is a two cpu intel machine with HT. Unfortunatly when i try to install the packages i keep getting errors from the package manager. 

When i try to install the "kernel-headers-2.6.11-9-em64t-p4-smp" i get the error:

```

kernel-headers-2.6.11-9-em64t-p4-smp:
 Depends: kernel-headers-2.6.11-9 but it is not going to be installed

```

And when i try to get around this by install the headers manually i get the error:

```

kernel-headers-2.6.11-9:
 Depends: kernel-kbuild-2.6-3  but it is not installable

```

As far as i can see there is no package called kernel-kbuild.

I have had these errors before when trying to install the AMD versions of the packages on my X2 Dual Core machine at home, however i had to reinstall before i got the bottom of the problem and after the reinstall they just went away.

Does anyone know what is causing this or how i can find out more information about the error?

Regards
Karail

---

### Post by Karail on 2006-02-21
*shameless bump*

---

