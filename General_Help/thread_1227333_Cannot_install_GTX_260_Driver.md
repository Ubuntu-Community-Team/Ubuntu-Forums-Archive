---
title: "Cannot install GTX 260 Driver"
date: 2009-07-30
forum: General Help
---

### Post by doggie504 on 2009-07-30
whenever i go to execute it, it says it cannot acess the file.

when i tried chmod +x i get the same thing.

I've also tried sudo, but to no avail.

---

### Post by doggie504 on 2009-07-30
anyone?

---

### Post by realzippy on 2009-07-30
so you tried:
sudo sh yournvidialinuxdriver ?
Why not using the GUI via System/Administration/Hardwaredrivers ?

---

### Post by doggie504 on 2009-07-30
> **realzippy said:**
> so you tried:
sudo sh yournvidialinuxdriver ?
Why not using the GUI via System/Administration/Hardwaredrivers ?

ok i guess it installed then w/o me knowing, but i still cant enable desktop effects(the reason for me wanting to install the drivers).

---

### Post by realzippy on 2009-07-30
type in terminal:

glxinfo

 mind that "direct rendering : yes"

---

### Post by doggie504 on 2009-07-30
post output? or what do i do when it comes up?

---

### Post by realzippy on 2009-07-30
those lines should be there:

direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

---

### Post by doggie504 on 2009-07-30
Just a little of it but, name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_ARB_create_context, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_multisample_coverage
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.4)

---

### Post by realzippy on 2009-07-30
your driver seems not to be installed.Please check if the
restricted nvidia driver is enabled in the panel: System/Administration/hardwaredrivers !

---

### Post by doggie504 on 2009-07-30
i have version 180 installed.

---

### Post by realzippy on 2009-07-30
did you restart?Your "glxinfo" shows:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer

If your nvidiadriver would work it would be something like:

direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 260 GTX/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 180......

Again:
Please check if the
restricted nvidia driver is enabled in the panel: System/Administration/hardwaredrivers !

If so,restart your computer,then try again.

---

### Post by doggie504 on 2009-07-30
now it wants to work, thanks for your patience.

---

