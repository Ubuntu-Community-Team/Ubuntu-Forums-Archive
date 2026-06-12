---
title: "Are you happy with nVidia 195.36.15 driver?"
date: 2010-04-10
forum: General Help
---

### Post by cdufour on 2010-04-10
Is it just me, or is this driver - nVidia 195.36.15 - just a piece of buggy software?

On a Lucid (64-bit) system equipped with a nVidia GTX260 (VDPAU feature set A) and using the 'nvidia-current' package, I bumped into:

[LIST]
[*]  mplayer not being able to play H.264 file though the VDPAU interface (using 'mplayer -vo vdpau -vc ffh264vdpau'); reverting to nVidia 190.53 (binary installer) solved the problem with NO further changes
[/LIST]

[LIST]
[*]X-Plane failing to launch (with a non-descript OpenGL-related error); reverting to nVidia 190.53 (binary installer) solved the problem with  NO further changes
[/LIST]
 
On a Debian Lenny (64-bit) system equipped with a nVidia ION (VDPAU feature set B1) and using the nVidia 195.36.15 binary installer, I bumped into:

[LIST]
[*](custom-built) mplayer not being able to play H.264 file though the VDPAU interface  (using 'mplayer -vo vdpau -vc ffh264vdpau'); reverting to nVidia 190.53  (binary installer) solved the problem with NO further changes
[/LIST]
  So? What are you experiences?

---

### Post by 3rdalbum on 2010-04-10
I haven't tried VDPAU yet on this system, but everything else appears to be fine. Oh, except that now that I've manually installed the Nvidia driver, I can't use the Ubuntu method to install it; I have to keep using Nvidia's own driver installer or it doesn't work. That's a real pain because I have to keep running Nvidia's installer every time I get a kernel update.

---

### Post by patchwork on 2010-04-10
Identical experience to 3rdalbum.

---

