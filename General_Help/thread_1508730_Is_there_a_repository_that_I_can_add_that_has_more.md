---
title: "Is there a repository that I can add that has more recent kernels?"
date: 2010-06-13
forum: General Help
---

### Post by josephellengar on 2010-06-13
I'd like to get the 6.33 kernel for trim support.  However, I do not want to add it manually for fear that I will not get important security patches and the like.  Does anybody know of a trustworthy repository that I can add that has this or a higher version kernel?  Thanks.

---

### Post by quixote on 2010-06-15
You could add the kernel repository and install the new kernel that way.  I'm not sure how it handles updates.  I had to do it once because the default kernel caused filesystem corruption, but I don't remember how it handled security updates for the kernel.  (Which is a good sign, right? I didn't have any problems. :biggrin:)

The kernel list is here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) 
and the one for 2.6.33 is here:[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/)

So, for instance, just getting and installing the kernel, if you wanted the 32-bit 2.6.33 kernel, you'd use:

```

 wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/linux-headers-2.6.33-020633rc1-generic_2.6.33-020633rc1_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/linux-headers-2.6.33-020633rc1_2.6.33-020633rc1_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/linux-image-2.6.33-020633rc1-generic_2.6.33-020633rc1_i386.deb

$ sudo dpkg -i linux-headers-2.6.33-020633rc1-generic_2.6.33-020633rc1_i386.deb linux-headers-2.6.33-020633rc1_2.6.33-020633rc1_all.deb linux-image-2.6.33-020633rc1-generic_2.6.33-020633rc1_i386.deb

```

---

### Post by sidzen on 2010-06-15
Hello, quixote, been following you around this forum lately -- how's Rocinante?

[http://forums.debian.net/viewtopic.php?f=5&t=41437](http://forums.debian.net/viewtopic.php?f=5&t=41437)  is a pertinent site,  [rossholley]("http://ubuntuforums.org/member.php?u=650923").
Liquorix is the keyword.

---

### Post by quixote on 2010-06-15
Hi sidzen.  Rocinante is fine, thanks for asking.  Sancho Panza on the other hand....

---

