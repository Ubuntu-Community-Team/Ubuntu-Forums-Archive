---
title: "Can't run executable after fresh installation..."
date: 2009-12-12
forum: General Help
---

### Post by Falkor on 2009-12-12
Hi, anyone here has bash issue with fresh installation of 9.04 x86_64?

After the fresh installation, when I try to run an executable (even as root), I get the following:

------------------------
-bash: ./< some executable >: No such file or directory
------------------------

How should I fix it the correct way? (I read some pointers about making symlink)

Thanks.

---

### Post by SlugSlug on 2009-12-12
is it executable?

sudo chmod +x [file]

---

### Post by Falkor on 2009-12-12
Thanks for the reply.

Anyway, I fixed it. Needed to install "ia32-libs". ](*,)

I have just started using x86_64, and before with the 32 bit version, I didn't need that.

---

### Post by ibuclaw on 2009-12-12
> **Falkor said:**
> Thanks for the reply.

Anyway, I fixed it. Needed to install "ia32-libs". ](*,)

I have just started using x86_64, and before with the 32 bit version, I didn't need that.

Try GetLibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Regards
Iain

---

### Post by dcstar on 2009-12-12
> **Falkor said:**
> Thanks for the reply.

Anyway, I fixed it. Needed to install "ia32-libs". ](*,)

I have just started using x86_64, and before with the 32 bit version, I didn't need that.

And you should only need it when trying to run old 32-bit apps, you should really be trying to use native 64-bit versions.

---

