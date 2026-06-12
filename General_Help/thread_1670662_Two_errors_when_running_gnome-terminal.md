---
title: "Two errors when running gnome-terminal"
date: 2011-01-19
forum: General Help
---

### Post by MrNatewood on 2011-01-19
```
bash: /dev/cgroup/cpu/user/8841/tasks: No such file or directory
bash: /dev/cgroup/cpu/user/8841/notify_on_release: No such file or directory

```

After these two lines I get a normal working bash prompt.

Could be related: Installed Xubuntu, then installed ubuntu-desktop and removed xubuntu-desktop&all xfce stuff.

Any ideas on how to fix this?

---

### Post by wojox on 2011-01-19
What does .bashrc look like?

```
cat .bashrc
```

---

### Post by Joeb454 on 2011-01-19
It looks like you've tried the alternative to the kernel patch, but missed a step :) I know, I did the same thing.

I followed [http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html) to get mine working again.

---

### Post by MrNatewood on 2011-01-20
> **Joeb454 said:**
> It looks like you've tried the alternative to the kernel patch, but missed a step :) I know, I did the same thing.

I followed [http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html) to get mine working again.

Oh wow thanks I forget I even did that.

What happened was that I applied the patch back when I had Mint installed. I formatted the / partition and installed *buntu, saving my home partition.

The bashrc file remained while all the system settings reverted to stock, that's where the errors came from.

So thanks again for the reminder!

---

