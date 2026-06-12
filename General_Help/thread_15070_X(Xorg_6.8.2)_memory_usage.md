---
title: "X(Xorg 6.8.2) memory usage"
date: 2005-02-11
forum: General Help
---

### Post by fenix03 on 2005-02-11
Is X memory usage normal?? It seems to use about 75MB. 

Just curious, since I compiled 6.8.2 myself and maybe there are makefile options that I haven't set?



--
Tasks:  87 total,   1 running,  86 sleeping,   0 stopped,   0 zombie
Cpu0  :  1.4% us,  0.0% sy,  0.0% ni, 98.6% id,  0.0% wa,  0.0% hi,  0.0% si
Cpu1  :  2.8% us,  0.7% sy,  0.0% ni, 96.5% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1036684k total,   784700k used,   251984k free,    62644k buffers
Swap:   128512k total,        0k used,   128512k free,   435864k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7152 root      15   0  333m  75m  14m S  3.5  7.4  39:47.20 X
11641 fen      16   0  145m  68m  22m S  0.0  6.8   4:02.74 firefox-bin
12845 root      15   0 35264  25m  15m S  0.0  2.5   0:18.41 synaptic
11550 fen      16   0 60208  24m  11m S  0.0  2.5   0:11.39 nautilus
11977 fen      15   0  269m  24m  10m S  0.0  2.4   0:02.39 java_vm
11548 fen      16   0 36696  21m  12m S  0.0  2.1   0:12.93 gnome-panel
11586 fen      16   0 41896  17m  10m S  1.4  1.7   0:23.06 gnome-terminal
11639 fen      16   0 19780  12m 9664 S  0.0  1.3   0:02.44 stickynotes_app
12895 fen      15   0 43856  12m 5644 S  0.0  1.2   0:01.83 xmms
11572 fen      15   0 20036  11m 8756 S  0.0  1.2   0:10.39 wnck-applet
11503 fen      16   0 22248  11m 9000 S  0.0  1.1   0:01.74 gnome-settings-
12707 root      15   0 22240  11m 8724 S  0.0  1.1   0:00.77 firestarter

---

### Post by daniels on 2005-02-12
I'll take a stab in the dark and say that you've got a 64MB graphics card.

X's memory usage will always be (total memory use reported) - (graphics card memory) ~= (actual memory use).

---

### Post by fenix03 on 2005-02-12
[QUOTE=daniels]I'll take a stab in the dark and say that you've got a 64MB graphics card.

X's memory usage will always be (total memory use reported) - (graphics card memory) ~= (actual memory use).[/QUOTE]

No, I have a Geforce 6800GT with 256MB video memory. Using glxinfo, I have direct rendering on and using Nvidia's drivers. Glxgears gives me around 11000fps and
and agpgart printouts that am using AGP with a bus of 8x.

Total memory use is that virtual memory? In that case it seems to be correct, 333MB-256MB = 77MB resident mem?

---

### Post by daniels on 2005-02-12
Oh, right, you already subtracted that, sorry.  The other thing to bear in mind is that when you start Firefox, for example, it will allocate all its images server-side, as the server has to store and display them.  xrestop is an excellent program to see which X clients are using your resources.

---

