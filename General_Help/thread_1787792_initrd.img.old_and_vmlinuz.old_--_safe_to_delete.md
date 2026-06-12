---
title: "initrd.img.old and vmlinuz.old -- safe to delete?"
date: 2011-06-21
forum: General Help
---

### Post by Brushstroke on 2011-06-21
Can I delete initrd.img.old and vmlinuz.old? Are they, as the file names state, old and not used anymore?

---

### Post by terrykiwi83 on 2011-06-21
I would think that you could delete them, but to be safe I would put them onto a pen drive first then delete. Once deleted reboot and see if you have any problems, if you do simply put them back :) if not then 'High Five!'

---

### Post by Brushstroke on 2011-06-21
I tried that, but it won't let me move the two files to a pen drive. It gives an error that says this: 

"File system does not support symbolic links."

What does that mean?

---

### Post by oldfred on 2011-06-21
Why do you want to delete? 

They just are links to the previous kernel that you used to boot. 

Some use the current links to boot the most current kernel in another partition without having to boot the main install and running sudo update grub. If new kernel does not work it gives you an option to boot the next oldest kernel. 

There also are instructions to use the links to manually boot if grub has issues. 

Links to not take any real space.

---

