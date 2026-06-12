---
title: "&quot;Kernel not found&quot;"
date: 2009-11-07
forum: General Help
---

### Post by Jacroe on 2009-11-07
After upgrading GRUB to version 1.97 beta 4 (at least that's the version listed on the Grub error screen) I have found that I cannot boot into ubuntu. All that I get is a command line interface with the prompt: "sh:grub>". How do I get into Ubuntu?

---

### Post by kaelonlloyd on 2009-11-07
Luckily for you i just managed to fix this problem.

 First off you type 'ls'
this will bring up devices such as (loop0) (hd0,1) (hd0,2)

You most probebly need (hd0,1) becuase it's a wubi installation, which uses the windwos partition

2. Type 'linux /boot/vml' then press TAB don't press enter

3. on the same line put a space and type 'root=/dev/sda1'(The 'a1' at the end could be different)

4. on the same line put a space and type 'loop=/ubuntu/disks/root.disk'
5. Press enter

6. Type 'initrd /boot/ini' then press TAB, the the enter button'
7 type boot and press enter


If your in to ubuntu, go to terminal and type 'sudo update-grub'

All this worked for me

---

### Post by Jacroe on 2009-11-07
Okay I did all that but some error was thrown up saying that it gave up trying to mount(?) or read(?) the root file system. Then it gave me a prompt for 'initramfs'. Anything there?

---

### Post by kaelonlloyd on 2009-11-07
What devices come up when you type 'ls'

---

