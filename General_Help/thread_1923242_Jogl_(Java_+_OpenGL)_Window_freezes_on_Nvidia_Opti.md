---
title: "Jogl (Java + OpenGL) Window freezes on Nvidia Optimus Laptops, Ubuntu 11.10"
date: 2012-02-10
forum: General Help
---

### Post by SciePy on 2012-02-10
Hello,

we are experiencing some weird issues with a Java project using the Jogl library ([http://jogamp.org/jogl/www/](http://jogamp.org/jogl/www/)) on Ubuntu 11.10. Basically the AWT window completely freezes as soon as the canvas object is added to the frame, in source code ```

        frame        = new Frame("test");
        canvas       = new GLCanvas();
        animator     = new FPSAnimator(canvas, 60);
        
        renderer     = new Renderer();
        
        canvas.addGLEventListener(renderer);

        frame.setSize(dim.getWidth(), dim.getHeight());
        frame.add(canvas);   // here it freezes 
```The application can then only be terminated using SIGKILL. 
This problem seems to be somehow related to Nvidias optimus technology since the application works on 3 linux machines (2 x intel integrated graphics, 1 x ATI HD 5870; Ubuntu 11.10, Arch, Debian sid) and crashes on 2 different laptops with Nvidias optimus technology and Ubuntu 11.10.

On both those laptops the nvidia card is disabled at startup using the acpi_call module ([https://github.com/mkottman/acpi_call](https://github.com/mkottman/acpi_call)), basically the test_off.sh script is executed.
The glx extension is working and the intel integrated graphics driver is active. 
Here are some command outputs from one of the laptops, if you need more info just say so ;)

Glxinfo:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_polygon_offset, GL_EXT_subtexture, 
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, 
    GL_EXT_texture, GL_EXT_texture3D, GL_IBM_rasterpos_clip, 
    GL_ARB_point_parameters, GL_EXT_draw_range_elements, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_texture_edge_clamp, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, 
    GL_ARB_multitexture, GL_EXT_framebuffer_sRGB, 
    GL_IBM_multimode_draw_arrays, GL_IBM_texture_mirrored_repeat, 
    GL_3DFX_texture_compression_FXT1, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, GL_ATI_envmap_bumpmap, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_depth_clamp, 
    GL_NV_vertex_program1_1, GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_ARB_depth_clamp, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_point_sprite, GL_ARB_shading_language_100, GL_ARB_sync, 
    GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_rectangle, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_packed_depth_stencil, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_env_combine, 
    GL_EXT_texture_sRGB_decode, GL_EXT_timer_query, GL_OES_EGL_image, 
    GL_ARB_copy_buffer, GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, 
    GL_ARB_texture_rg, GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
    GL_ARB_ES2_compatibility, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x074 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x078  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

```Jogl test.sh script:
```

/usr/bin/java
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)
LIBXCB_ALLOW_SLOPPY_LOCK:
LIBGL_DRIVERS_PATH:
LIBGL_DEBUG:
java
-----------------------------------------------------------------------------------------------------
Platform: LINUX / Linux 3.0.0-15-generic (os), amd64 (arch) 4 cores
MachineDescription: runtimeValidated true, littleEndian true, 32Bit false, primitive size / alignment:
  int8    1 / 1, int16   2 / 2
  int     4 / 4, long    8 / 8
  int32   4 / 4, int64   8 / 8
  float   4 / 4, double  8 / 8, ldouble 16 / 16
  pointer 8 / 8, page    4096
Platform: Java Version: 1.6.0_23, VM: OpenJDK 64-Bit Server VM, Runtime: OpenJDK Runtime Environment
Platform: Java Vendor: Sun Microsystems Inc., http://java.sun.com/, is JavaSE: true
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: com.jogamp.common
Extension Name: com.jogamp.common
Specification Title: GlueGen Java Bindings Generator
Specification Vendor: JogAmp Community
Specification Version: 2.0
Implementation Title: GlueGen Run-Time
Implementation Vendor: JogAmp Community
Implementation Vendor ID: com.jogamp
Implementation URL: http://jogamp.org/
Implementation Version: 2.0-b33-20111219
Implementation Branch: rc
Implementation Commit: 013600318f24391cd6c8c541343c208736b5f4f4
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Platform: LINUX / Linux 3.0.0-15-generic (os), amd64 (arch) 4 cores
MachineDescription: runtimeValidated true, littleEndian true, 32Bit false, primitive size / alignment:
  int8    1 / 1, int16   2 / 2
  int     4 / 4, long    8 / 8
  int32   4 / 4, int64   8 / 8
  float   4 / 4, double  8 / 8, ldouble 16 / 16
  pointer 8 / 8, page    4096
Platform: Java Version: 1.6.0_23, VM: OpenJDK 64-Bit Server VM, Runtime: OpenJDK Runtime Environment
Platform: Java Vendor: Sun Microsystems Inc., http://java.sun.com/, is JavaSE: true
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: com.jogamp.common
Extension Name: com.jogamp.common
Specification Title: GlueGen Java Bindings Generator
Specification Vendor: JogAmp Community
Specification Version: 2.0
Implementation Title: GlueGen Run-Time
Implementation Vendor: JogAmp Community
Implementation Vendor ID: com.jogamp
Implementation URL: http://jogamp.org/
Implementation Version: 2.0-b33-20111219
Implementation Branch: rc
Implementation Commit: 013600318f24391cd6c8c541343c208736b5f4f4
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: javax.media.nativewindow
Extension Name: null
Specification Title: null
Specification Vendor: null
Specification Version: null
Implementation Title: null
Implementation Vendor: null
Implementation Vendor ID: null
Implementation URL: null
Implementation Version: null
Implementation Branch: null
Implementation Commit: null
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Platform: LINUX / Linux 3.0.0-15-generic (os), amd64 (arch) 4 cores
MachineDescription: runtimeValidated true, littleEndian true, 32Bit false, primitive size / alignment:
  int8    1 / 1, int16   2 / 2
  int     4 / 4, long    8 / 8
  int32   4 / 4, int64   8 / 8
  float   4 / 4, double  8 / 8, ldouble 16 / 16
  pointer 8 / 8, page    4096
Platform: Java Version: 1.6.0_23, VM: OpenJDK 64-Bit Server VM, Runtime: OpenJDK Runtime Environment
Platform: Java Vendor: Sun Microsystems Inc., http://java.sun.com/, is JavaSE: true
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: com.jogamp.common
Extension Name: com.jogamp.common
Specification Title: GlueGen Java Bindings Generator
Specification Vendor: JogAmp Community
Specification Version: 2.0
Implementation Title: GlueGen Run-Time
Implementation Vendor: JogAmp Community
Implementation Vendor ID: com.jogamp
Implementation URL: http://jogamp.org/
Implementation Version: 2.0-b33-20111219
Implementation Branch: rc
Implementation Commit: 013600318f24391cd6c8c541343c208736b5f4f4
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: javax.media.opengl
Extension Name: javax.media.opengl
Specification Title: Java Bindings for OpenGL API Specification
Specification Vendor: JogAmp Community
Specification Version: 2.0
Implementation Title: Java Bindings for OpenGL Runtime Environment
Implementation Vendor: JogAmp Community
Implementation Vendor ID: com.jogamp
Implementation URL: http://jogamp.org/
Implementation Version: 2.0-b45-20111219
Implementation Branch: rc
Implementation Commit: 2f2b071d60f5b630989140b1ade49d648ad78c20
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Platform: LINUX / Linux 3.0.0-15-generic (os), amd64 (arch) 4 cores
MachineDescription: runtimeValidated true, littleEndian true, 32Bit false, primitive size / alignment:
  int8    1 / 1, int16   2 / 2
  int     4 / 4, long    8 / 8
  int32   4 / 4, int64   8 / 8
  float   4 / 4, double  8 / 8, ldouble 16 / 16
  pointer 8 / 8, page    4096
Platform: Java Version: 1.6.0_23, VM: OpenJDK 64-Bit Server VM, Runtime: OpenJDK Runtime Environment
Platform: Java Vendor: Sun Microsystems Inc., http://java.sun.com/, is JavaSE: true
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: com.jogamp.common
Extension Name: com.jogamp.common
Specification Title: GlueGen Java Bindings Generator
Specification Vendor: JogAmp Community
Specification Version: 2.0
Implementation Title: GlueGen Run-Time
Implementation Vendor: JogAmp Community
Implementation Vendor ID: com.jogamp
Implementation URL: http://jogamp.org/
Implementation Version: 2.0-b33-20111219
Implementation Branch: rc
Implementation Commit: 013600318f24391cd6c8c541343c208736b5f4f4
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: javax.media.nativewindow
Extension Name: null
Specification Title: null
Specification Vendor: null
Specification Version: null
Implementation Title: null
Implementation Vendor: null
Implementation Vendor ID: null
Implementation URL: null
Implementation Version: null
Implementation Branch: null
Implementation Commit: null
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: com.jogamp.newt
Extension Name: null
Specification Title: null
Specification Vendor: null
Specification Version: null
Implementation Title: null
Implementation Vendor: null
Implementation Vendor ID: null
Implementation URL: null
Implementation Version: null
Implementation Branch: null
Implementation Commit: null
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Platform: LINUX / Linux 3.0.0-15-generic (os), amd64 (arch) 4 cores
MachineDescription: runtimeValidated true, littleEndian true, 32Bit false, primitive size / alignment:
  int8    1 / 1, int16   2 / 2
  int     4 / 4, long    8 / 8
  int32   4 / 4, int64   8 / 8
  float   4 / 4, double  8 / 8, ldouble 16 / 16
  pointer 8 / 8, page    4096
Platform: Java Version: 1.6.0_23, VM: OpenJDK 64-Bit Server VM, Runtime: OpenJDK Runtime Environment
Platform: Java Vendor: Sun Microsystems Inc., http://java.sun.com/, is JavaSE: true
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: com.jogamp.common
Extension Name: com.jogamp.common
Specification Title: GlueGen Java Bindings Generator
Specification Vendor: JogAmp Community
Specification Version: 2.0
Implementation Title: GlueGen Run-Time
Implementation Vendor: JogAmp Community
Implementation Vendor ID: com.jogamp
Implementation URL: http://jogamp.org/
Implementation Version: 2.0-b33-20111219
Implementation Branch: rc
Implementation Commit: 013600318f24391cd6c8c541343c208736b5f4f4
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: javax.media.opengl
Extension Name: javax.media.opengl
Specification Title: Java Bindings for OpenGL API Specification
Specification Vendor: JogAmp Community
Specification Version: 2.0
Implementation Title: Java Bindings for OpenGL Runtime Environment
Implementation Vendor: JogAmp Community
Implementation Vendor ID: com.jogamp
Implementation URL: http://jogamp.org/
Implementation Version: 2.0-b45-20111219
Implementation Branch: rc
Implementation Commit: 2f2b071d60f5b630989140b1ade49d648ad78c20
-----------------------------------------------------------------------------------------------------
Info: XInitThreads() called for concurrent Thread support
GLCaps[---- 0x60: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x60: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x61: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x61: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x62: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x62: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x63: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x63: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x64: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x64: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x65: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x65: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x72: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x72: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x73: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 16/0/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x73: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 16/0/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x78: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x78: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x79: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x79: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x7a: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x7a: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x7b: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x7b: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x7c: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x7c: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x7d: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x7d: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x8a: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x8a: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x8b: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 16/0/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x8b: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 16/0/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x21 0x70: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x21 0x70: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x21 0x70: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x22 0x88: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x22 0x88: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x22 0x88: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x5f 0x71: on-scr, rgba 0x8/8/8/8, trans-rgba 0xff/ff/ff/ff, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x5f 0x71: offscr, rgba 0x8/8/8/8, trans-rgba 0xff/ff/ff/ff, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x5f 0x71: offscr, rgba 0x8/8/8/8, trans-rgba 0xff/ff/ff/ff, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x90 0x66: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x90 0x66: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x90 0x66: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x91 0x67: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x91 0x67: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x91 0x67: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x92 0x68: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x92 0x68: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x92 0x68: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x93 0x69: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x93 0x69: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x93 0x69: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x94 0x6a: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x94 0x6a: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x94 0x6a: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x95 0x6b: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x95 0x6b: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x95 0x6b: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x96 0x6c: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x96 0x6c: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x96 0x6c: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x97 0x6d: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x97 0x6d: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x97 0x6d: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x98 0x6e: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x98 0x6e: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x98 0x6e: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x99 0x6f: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x99 0x6f: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x99 0x6f: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9a 0x74: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x9a 0x74: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9a 0x74: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9b 0x75: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2]]
GLCaps[0x9b 0x75: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9b 0x75: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9c 0x76: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x9c 0x76: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9c 0x76: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9d 0x77: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2]]
GLCaps[0x9d 0x77: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9d 0x77: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9e 0x7e: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x9e 0x7e: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9e 0x7e: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9f 0x7f: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x9f 0x7f: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9f 0x7f: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa0 0x80: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa0 0x80: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa0 0x80: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa1 0x81: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa1 0x81: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa1 0x81: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa2 0x82: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa2 0x82: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa2 0x82: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa3 0x83: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa3 0x83: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa3 0x83: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa4 0x84: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa4 0x84: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa4 0x84: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa5 0x85: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa5 0x85: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa5 0x85: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa6 0x86: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa6 0x86: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa6 0x86: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa7 0x87: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa7 0x87: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa7 0x87: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa8 0x89: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa8 0x89: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa8 0x89: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa9 0x8c: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa9 0x8c: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa9 0x8c: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xaa 0x8d: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2]]
GLCaps[0xaa 0x8d: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xaa 0x8d: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xab 0x8e: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xab 0x8e: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xab 0x8e: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xac 0x8f: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2]]
GLCaps[0xac 0x8f: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xac 0x8f: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
-----------------------------------------------------------------------------------------------------
Platform: LINUX / Linux 3.0.0-15-generic (os), amd64 (arch) 4 cores
MachineDescription: runtimeValidated true, littleEndian true, 32Bit false, primitive size / alignment:
  int8    1 / 1, int16   2 / 2
  int     4 / 4, long    8 / 8
  int32   4 / 4, int64   8 / 8
  float   4 / 4, double  8 / 8, ldouble 16 / 16
  pointer 8 / 8, page    4096
Platform: Java Version: 1.6.0_23, VM: OpenJDK 64-Bit Server VM, Runtime: OpenJDK Runtime Environment
Platform: Java Vendor: Sun Microsystems Inc., http://java.sun.com/, is JavaSE: true
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: com.jogamp.common
Extension Name: com.jogamp.common
Specification Title: GlueGen Java Bindings Generator
Specification Vendor: JogAmp Community
Specification Version: 2.0
Implementation Title: GlueGen Run-Time
Implementation Vendor: JogAmp Community
Implementation Vendor ID: com.jogamp
Implementation URL: http://jogamp.org/
Implementation Version: 2.0-b33-20111219
Implementation Branch: rc
Implementation Commit: 013600318f24391cd6c8c541343c208736b5f4f4
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
Package: javax.media.opengl
Extension Name: javax.media.opengl
Specification Title: Java Bindings for OpenGL API Specification
Specification Vendor: JogAmp Community
Specification Version: 2.0
Implementation Title: Java Bindings for OpenGL Runtime Environment
Implementation Vendor: JogAmp Community
Implementation Vendor ID: com.jogamp
Implementation URL: http://jogamp.org/
Implementation Version: 2.0-b45-20111219
Implementation Branch: rc
Implementation Commit: 2f2b071d60f5b630989140b1ade49d648ad78c20
-----------------------------------------------------------------------------------------------------
Info: XInitThreads() called for concurrent Thread support
GLCaps[---- 0x60: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x60: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x61: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x61: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x62: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x62: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x63: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x63: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x64: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x64: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x65: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x65: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x72: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x72: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x73: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 16/0/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x73: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 16/0/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x78: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x78: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x79: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x79: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x7a: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x7a: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x7b: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x7b: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x7c: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x7c: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x7d: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x7d: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x8a: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x8a: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[---- 0x8b: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 16/0/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[---- 0x8b: offscr, rgba 0x5/6/5/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 16/0/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x21 0x70: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x21 0x70: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x21 0x70: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x22 0x88: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x22 0x88: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x22 0x88: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x5f 0x71: on-scr, rgba 0x8/8/8/8, trans-rgba 0xff/ff/ff/ff, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x5f 0x71: offscr, rgba 0x8/8/8/8, trans-rgba 0xff/ff/ff/ff, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x5f 0x71: offscr, rgba 0x8/8/8/8, trans-rgba 0xff/ff/ff/ff, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x90 0x66: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x90 0x66: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x90 0x66: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x91 0x67: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x91 0x67: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x91 0x67: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x92 0x68: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x92 0x68: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x92 0x68: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x93 0x69: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x93 0x69: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x93 0x69: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x94 0x6a: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x94 0x6a: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x94 0x6a: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x95 0x6b: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x95 0x6b: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x95 0x6b: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x96 0x6c: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x96 0x6c: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x96 0x6c: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x97 0x6d: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x97 0x6d: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x97 0x6d: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x98 0x6e: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x98 0x6e: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x98 0x6e: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x99 0x6f: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x99 0x6f: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x99 0x6f: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9a 0x74: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x9a 0x74: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9a 0x74: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9b 0x75: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2]]
GLCaps[0x9b 0x75: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9b 0x75: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9c 0x76: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x9c 0x76: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9c 0x76: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9d 0x77: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2]]
GLCaps[0x9d 0x77: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9d 0x77: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9e 0x7e: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x9e 0x7e: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9e 0x7e: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0x9f 0x7f: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0x9f 0x7f: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0x9f 0x7f: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa0 0x80: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa0 0x80: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa0 0x80: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa1 0x81: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa1 0x81: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa1 0x81: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa2 0x82: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa2 0x82: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa2 0x82: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa3 0x83: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa3 0x83: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa3 0x83: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa4 0x84: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa4 0x84: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa4 0x84: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa5 0x85: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa5 0x85: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa5 0x85: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa6 0x86: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa6 0x86: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa6 0x86: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 0/0/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa7 0x87: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa7 0x87: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa7 0x87: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, one, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa8 0x89: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa8 0x89: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa8 0x89: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xa9 0x8c: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xa9 0x8c: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xa9 0x8c: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xaa 0x8d: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2]]
GLCaps[0xaa 0x8d: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xaa 0x8d: offscr, rgba 0x8/8/8/0, opaque, accum-rgba 16/16/16/0, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xab 0x8e: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
GLCaps[0xab 0x8e: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xab 0x8e: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2], pixmap]
GLCaps[0xac 0x8f: on-scr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2]]
GLCaps[0xac 0x8f: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pbuffer [r2t 0, r2tr 0, float 0]]
GLCaps[0xac 0x8f: offscr, rgba 0x8/8/8/8, opaque, accum-rgba 16/16/16/16, dp/st/ms: 24/8/0, dbl, mono  , sw, GLProfile[GL2/GL2], pixmap]
Detected screen size 1366x768
-----------------------------------------------------------------------------------------------------
X11GraphicsDevice[type X11, connection :0.0]: GLAvailability[Native[GL4bc false, GL4 false, GL3bc false, GL3 false, GL2 true[1.5 (compatibility profile, any, old)], GL2ES1 true, GLES1 false, GL2ES2 true, GLES2 false], Profiles[GLProfile[GL2ES2/GL2], GLProfile[GL2ES1/GL2], GLProfile[GL2/GL2], GLProfile[GL2/GL2], GLProfile[GL2GL3/GL2], , default GLProfile[GL2/GL2]]]
Swap Interval -1
GL Profile    GLProfile[GL2/GL2]
CTX VERSION   2.1 (compatibility profile, any, old) - 2.1 Mesa 7.11
GL            jogamp.opengl.gl4.GL4bcImpl@3fb6101e
GL_VENDOR     Tungsten Graphics, Inc
GL_VERSION    2.1 Mesa 7.11
GL_EXTENSIONS 
              GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_envmap_bumpmap GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_NV_vertex_program1_1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_compression_rgtc GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_draw_buffers2 GL_EXT_gpu_program_parameters GL_EXT_texture_env_combine GL_EXT_texture_sRGB_decode GL_EXT_timer_query GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_half_float_vertex GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_ARB_ES2_compatibility GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_texture_lod GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_robustness 
GLX_EXTENSIONS 
              GLX_SGI_swap_control GLX_SGIX_visual_select_group GLX_SGI_video_sync GLX_MESA_copy_sub_buffer GLX_EXT_texture_from_pixmap GLX_ARB_get_proc_address GLX_EXT_visual_rating GLX_INTEL_swap_event GLX_OML_sync_control GLX_EXT_framebuffer_sRGB GLX_EXT_visual_info GLX_MESA_multithread_makecurrent GLX_EXT_import_context GLX_OML_swap_method GLX_SGIX_pbuffer GLX_ARB_multisample GLX_SGI_make_current_read GLX_MESA_swap_control GLX_SGIS_multisample GLX_SGIX_fbconfig 
GLSL          true, shader-compiler: true
-----------------------------------------------------------------------------------------------------
Requested: GLCaps[on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 16/0/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
Chosen   : GLCaps[0x94 0x6a: on-scr, rgba 0x8/8/8/0, opaque, accum-rgba 0/0/0/0, dp/st/ms: 24/8/0, dbl, mono  , hw, GLProfile[GL2/GL2]]
```Note here the window that opens also freezes and the script must be terminated, so the output is probably not complete.


Thanks,
Sam

---

