---
title: "multiple kernels listed in grub"
date: 2010-01-02
forum: General Help
---

### Post by rdh61 on 2010-01-02
Hi,

I recently installed ubuntu 9.10 and a day later updated with all the suggested security and recommended updates. Now I notice that in my Grub there are two different kernel versions listed. Are they both necessary? Can I / should I get rid of the older one, and if so, how?

I ask because after all these updates I notice my computer runs much slower, so I don't want it overloaded with unnecessary software.

Thanks.

---

### Post by smerral on 2010-01-02
As far as I know having another kernel available shouldn't slow down your computer - I would keep it - if anything goes wrong with the latest kernel you can boot from the older one.

---

### Post by nothingspecial on 2010-01-02
Sometimes a new kernel can unwittingly break something on some peoples machines. For this reason your old kernel is not removed so you can boot into it if you need to.

You can remove them through synaptic package manager if you like.

---

### Post by slakkie on 2010-01-02
The additional kernels do not have a performance penalty (although grub-update may run a bit longer). The biggest issue with having too many kernels is diskspace, each kernel is about 100 Mb, so having 10 will consume a GB of diskspace.

```

_rmkernel () {
        local kernel=$1
        local kernel_pkg=$2
        local meta_pkg=$3
        sudo aptitude remove $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
}

rmkernel () {
        local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
        local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
        local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"
        _rmkernel $cur_kernel $kernel_pkg $meta_pkg
}

```

If you add this code segment to your .bashrc and you source your .bashrc (*source $HOME/.bashrc*) you can then run *rmkernel* and it will remove the kernels you don't use anymore. You can also do this via synaptic via pointing and clicking. You can find out what your current kernel is by running *uname -r*.

A word of wisdom, when you install a new kernel, don't remove the old ones to soon, you might need to previous kernel to boot your machine in case the new kernel doesn't behave like expected. Keep it for a week or so if you have no problems with the newer kernel, feel free to remove the old ones.

---

