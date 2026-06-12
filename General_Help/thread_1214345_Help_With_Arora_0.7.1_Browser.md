---
title: "Help With Arora 0.7.1 Browser"
date: 2009-07-15
forum: General Help
---

### Post by izizzle on 2009-07-15
Hello! Today I installed the Arora 0.7.1 amd64 build on my Kubuntu 9.04 64-bit system, and I am having issues. When I start it up, it freezes and then I have to kill it. I can't even navigate to a different webpage. Here is the terminal output: ```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
server bind: Address already in use
*** NSPlugin Viewer  *** ERROR: failed to initialize plugin-side RPC server connection
Killed
imran@eVga:~$ arora
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
server bind: Address already in use
*** NSPlugin Viewer  *** ERROR: failed to initialize plugin-side RPC server connection
Killed
```

Please help!

Thanks.

---

### Post by izizzle on 2009-07-16
Bump!

---

### Post by izizzle on 2009-07-17
Bump.

---

### Post by nikhilk on 2009-07-17
I found a few launchpad bug reports [369498]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/369498") and [362939]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/362939") but they all seem to arise when running a 32 bit on 64 bit 9.04 system.
Are you absolutely sure that use have the 32 bit build for Arora?

---

### Post by izizzle on 2009-07-17
I have the 64-bit build for my 64-bit system.

---

