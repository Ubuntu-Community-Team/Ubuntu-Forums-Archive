---
title: "increase shared video memory"
date: 2011-09-04
forum: General Help
---

### Post by dan0804smith on 2011-09-04
is the a command that you can use that would increase your shared video memory.  i have a dell mini 10v running hardy and it only has 8mb of shared video memory.  is there any way to increase this through a command or program?

---

### Post by arjunajith on 2011-09-04
This cannot be changed once an OS is loaded, because this will be like plugging in an extra RAM when the system is running.

But in bios you can change this memory...
probably upto something like 64 or 32.

If you're using intel,
press F2 when rebooting and select video configuration from advanced tab.
there you can change the memory.

---

### Post by dan0804smith on 2011-09-04
> **arjunajith said:**
> This cannot be changed once an OS is loaded, because this will be like plugging in an extra RAM when the system is running.

But in bios you can change this memory...
probably upto something like 64 or 32.

If you're using intel,
press F2 when rebooting and select video configuration from advanced tab.
there you can change the memory.


unfortunately, my bios doesnt have that option.  i will be switching to lubuntu soon.  how should i go about doing this when loading the new os?

---

### Post by 3rdalbum on 2011-09-04
The Intel driver automatically allocates shared memory as needed. I don't think it ever actually hits 8MiB of video memory, as that's very low. What are the symptoms of your problem that causes you to think you need to do some allocation of memory?

---

### Post by dan0804smith on 2011-09-04
> **3rdalbum said:**
> The Intel driver automatically allocates shared memory as needed. I don't think it ever actually hits 8MiB of video memory, as that's very low. What are the symptoms of your problem that causes you to think you need to do some allocation of memory?

it would be nice to run videos in 720p

i also feel that the video memory problem is a bottle neck in my net books performance.

my computer is really slow when it comes to scrolling down data heavy packages.

i would just like to allocate some more shard video memory.

perhaps allocating ram as v ram would be a good subsitute?

and thoughts?


PS ran cat /var/log/Xorg.0.log | grep mem -i



got 


(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf0080000/19
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): detected 7932 kB stolen memory.
(II) intel(0): I830CheckAvailableMemory: 954364 kB available
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x00800000 (pgoffset 2048)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x00c00000 (pgoffset 3072)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01800000 (pgoffset 6144)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01c00000 (pgoffset 7168)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x02000000 (pgoffset 8192)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x007bf000:            end of stolen memory


im pretty sure it says that i only have around 8mb

---

### Post by 3rdalbum on 2011-09-04
> **dan0804smith said:**
> it would be nice to run videos in 720p

On Intel graphics, that's mainly CPU-bound anyway. More video memory won't help.

> i also feel that the video memory problem is a bottle neck in my net books performance.

my computer is really slow when it comes to scrolling down data heavy packages.

i would just like to allocate some more shard video memory.

perhaps allocating ram as v ram would be a good subsitute?

That's essentially where your video memory comes from in these integrated graphics chips; your main system memory. Unfortunately, integrated graphics are slow and main system memory is slow to be used as video RAM.

I think what you're describing is pretty much "par for the course" and fairly normal. Unfortunately, Intel integrated graphics is about the slowest one out there.

I'm assuming you can run Compiz, right? (the Unity desktop environment or the desktop effects on the Ubuntu Classic desktop). If you can, then you've definitely got more than 8 MiB of VRAM in use.

---

