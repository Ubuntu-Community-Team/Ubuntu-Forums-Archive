---
title: "Experience MapsGL"
date: 2012-06-29
forum: General Help
---

### Post by AlanR8 on 2012-06-29
Afternoon, wonder is someone can shed some light on this for me.

Hardware is an Aspire 5742 i5-480M with Intel HD graphics, 3 gigs of RAM. 12.04 installed.

If I run Google maps in Google Chrome and try to experience MapsGL I get the following message:

"We detected that your computer does not meet the system performance requirements for MapsGL. Learn more about the system requirements for MapsGL."

However, if I try in Firefox, all is well!

Anyone got any ideas?

---

### Post by idoitprone on 2012-06-29
> **AlanR8 said:**
> Afternoon, wonder is someone can shed some light on this for me.

Hardware is an Aspire 5742 i5-480M with Intel HD graphics, 3 gigs of RAM. 12.04 installed.

If I run Google maps in Google Chrome and try to experience MapsGL I get the following message:

"We detected that your computer does not meet the system performance requirements for MapsGL. Learn more about the system requirements for MapsGL."

However, if I try in Firefox, all is well!

Anyone got any ideas?

If it works in firefox, then it is a google chrome problem. Go report it to google

---

### Post by Zvlwab on 2012-06-29
Please post the information you get on the following page
chrome://gpu/

---

### Post by AlanR8 on 2012-08-30
Sorry for the long delay. I got Maps GL working but then did a rebuild and now it won't work in Chrome again, but will in FF.

Here's the output you asked for:

> Graphics Feature Status
Canvas: Software only, hardware acceleration unavailable
Compositing: Hardware accelerated
3D CSS: Hardware accelerated
CSS Animation: Accelerated
WebGL: Hardware accelerated
WebGL multisampling: Hardware accelerated
Flash 3D: Hardware accelerated
Flash Stage3D: Unavailable. Hardware acceleration unavailable
Problems Detected
Accelerated 2d canvas is unstable in Linux at the moment.
Stage3D is not supported on Linux.: 129848
Version Information
Data exported	Thu Aug 30 2012 18:51:57 GMT+0100 (BST)
Chrome version	21.0.1180.81 (Official Build 151980)
Operating system	Linux 3.2.0-30-generic
Software rendering list version	1.45
ANGLE revision	1046
2D graphics backend	Skia
Driver Information
Initialization time	175
GPU0	VENDOR = 0x8086 [Intel Corporation], DEVICE= 0x0046 [Core Processor Integrated Graphics Controller]
Optimus	false
AMD switchable	false
Driver vendor	Mesa
Driver version	8.0.2
Driver date	
Pixel shader version	1.20
Vertex shader version	1.20
GL version	2.1
GL_VENDOR	Tungsten Graphics, Inc
GL_RENDERER	Mesa DRI Intel(R) Ironlake Mobile
GL_VERSION	2.1 Mesa 8.0.2
GL_EXTENSIONS	GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_envmap_bumpmap GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_NV_vertex_program1_1 GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_rgtc GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_draw_buffers2 GL_EXT_gpu_program_parameters GL_EXT_texture_array GL_EXT_texture_integer GL_EXT_texture_sRGB_decode GL_EXT_timer_query GL_OES_EGL_image GL_MESA_texture_array GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_half_float_vertex GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_ARB_ES2_compatibility GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_texture_lod GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_robustness

---

### Post by AlanR8 on 2012-09-01
Bump?

---

### Post by AlanR8 on 2012-09-05
And again BUMP!!!!!!! :-) ;) :p) :P

---

### Post by idoitprone on 2012-09-09
> **AlanR8 said:**
> And again BUMP!!!!!!! :-) ;) :p) :P

then check if webgl is disabled

enter 
```
about:flags
``` in url

and enable webgl

---

### Post by AlanR8 on 2012-09-10
thanks idoitprone but it would appear that webgl IS enabled....

---

### Post by AlanR8 on 2012-09-25
Bump...anyone?

---

### Post by Barhilton on 2012-11-09
1) Enter the following URL in your Chrome: chrome://flags 
2) Enable "Override software rendering list" 
3) Click the "Relaunch now" button on the bottom of the page.

[http://productforums.google.com/forum/#!topic/maps/dVlW-voD9dI](http://productforums.google.com/forum/#!topic/maps/dVlW-voD9dI)

It worked for me! :)

---

### Post by AlanR8 on 2012-11-10
Barhilton

That seems to have done the trick thank you!

I'll mark the thread solved in a couple of days following some testing!

---

