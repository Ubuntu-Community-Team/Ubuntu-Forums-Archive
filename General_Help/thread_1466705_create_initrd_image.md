---
title: "create initrd image"
date: 2010-04-30
forum: General Help
---

### Post by sbailey85 on 2010-04-30
Hello I have just compiled my new kernel after installing lucid. Because I have to use a patch to get the acpi to work properly. The problem is it did no generate a initrd file. Even thought --initrd was added to the make-kpg command. I am basicly wondering how i could create an initrd image to add to the bootlader. Because i think thats the reason my newest kernel is not booting

Thank you in advance

Sean

---

### Post by psusi on 2010-04-30
It should be generated automatically when you install the package by update-initramfs.

---

### Post by nanog on 2010-04-30
man update-initramfs will tell you what you need to do (specifically the -k flag).

---

### Post by sbailey85 on 2010-04-30
thank you very much got my initrd image working fine and i boot ok! Now all i have to do is fix my wireless which shouldnt be a problem. Thank you again

---

