---
title: "WebGL stopped working"
date: 2011-09-17
forum: General Help
---

### Post by nonproffessional on 2011-09-17
WebGL was previously working a few weeks ago in both Chromium and Firefox but now it is mysteriously broken in both.

The "libgl" packages all appear installed still. OpenGL must be working since the hardware accelerated desktop effects are ok. Following [these tips]("http://learningwebgl.com/blog/?p=11#troubleshooting") I typed "glxinfo" and found the relevant version was not less than 2.0. In fact I got this:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GT/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 260.19.06
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler

```

From the above you can see I have a GeForce 9800 GT which is not excluded according to [this information]("http://www.google.com/support/chrome/bin/answer.py?answer=1220892"). Just to be sure I tried running chromium with various permutations of the switches "--enable-webgl", "--inprocess-webgl" and "-&#8211;ignore-gpu-blacklist" but with no effect.

I am using Ubuntu 10.10 and the only thing I can think of installing since WebGL last worked is Wine. I have tried removing that and even tried rebooting which I hardly ever have to do! Are any packages known to conflict? What more can I try? Please help.

---

### Post by nonproffessional on 2011-09-19
Firefox was a bit old so I updated and that now works which only serves to prove that it's possible. All other browsers continue to be broken despite being up-to-date.

I'll make do with Firefox for now...

---

