---
title: "Please help with failed instalation of vegastrike."
date: 2009-11-03
forum: General Help
---

### Post by szaemon on 2009-11-03
Hi Folks,
I started asking for help initially here:

[http://ubuntuforums.org/showthread.php?p=8212731#post8212731](http://ubuntuforums.org/showthread.php?p=8212731#post8212731)

with a request to help just installing, before it became an issue. Now that it has become an actual problem I thought it proper to post a new thread.

I have also posted to the vegastrike forums to see what they have to say.

My first installation of vegastrike was through the Ubuntu Repositories. It ran for a while before problems showed up and I decided to look around and find out if there were issues reported...

I did a complete removal through Ubuntu's Synaptic Manager, then downloaded the .rar file from this sites homepage and installed it through the GUI. No go. I couldn't figure out how to unistall it, so I just downloaded and installed the .tar.bz2 file also through the GUI. I don't use the Terminal much, not really a computer knowledgeable type person, but I'm learning. Again though, it was a no go for starting the game up.

When I try the screen blinks out for a moment and then comes back with an incorrect screen resolution.  I think the problem is that the the startup command is activating some broken files from the initial setup, as the new settings I chose in vssetup have not been applied. It is still loading according to the original setting where I accidentally chose the wrong screen resolution.

Any suggestions on how I can fix this?

When I run it in Terminal I get this:

me@mycomputer:~$ vegastrike
 In path /home/me/Games/vegastrike/vegastrike-0.5.0/bin
Vega Strike  
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for license details.

GOT SUBDIR ARG = 
Found data in /home/me
Using /home/me as data directory
Found MODDIR = /home/me/mods
USING HOMEDIR : /home/me/.vegastrike As the home directory 
CONFIGFILE - No config found in home : /home/me/.vegastrike/vegastrike.config
CONFIGFILE - No home config file found, using datadir config file : /home/me/vegastrike.config
DATADIR - No datadir specified in config file, using ; /home/me
SIMULATION_ATOM: 0.07
MISSION_NAME is empty using : main_menu.mission
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
running import sys
print sys.path
sys.path = [r"/home/me/modules/builtin",r"/home/me/modules",r"/home/me/bases"]
['/usr/local/lib/python24.zip', '/usr/local/lib/python2.4/', '/usr/local/lib/python2.4/plat-linux2', '/usr/local/lib/python2.4/lib-tk', '/usr/lib/python2.4/lib-dynload']
testing VS randomrunning import sys
print sys.path
['/home/me/modules/builtin', '/home/me/modules', '/home/me/bases']
Setting Screen to w 1024 h 768 and pitch of 4096 and 32 bpp 4 bytes per pix mode
OpenGL Extensions supported: GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
OpenGL::GL_EXT_compiled_vertex_array unsupported
OpenGL::Accurate Fog Distance unsupported
OpenGL::Generic Texture Compression supported
OpenGL::S3TC Texture Compression unsupported
OpenGL::Multitexture supported (8 units)
OpenGL::TextureCubeMapExt supported
OpenGL::S3TC Texture Clamp-to-Edge supported
OpenGL::S3TC Texture Clamp-to-Border supported
OpenGL::EXTColorTable unsupported
0 joysticks were found.

The names of the joysticks are:
Warning, galaxy contains no overarching planet info
FactionXML:LoadXML factions.xml
Failed to open 'factions.xml' this probably means it can't find the data directory
vegastrike: ../src/cmd/faction_xml.cpp:334: static void Faction::LoadXML(const char*, char*, int): Assertion `0' failed.
Aborted

Any help would be appreciated.
Thanks,
szaemon

---

### Post by Jesdisciple on 2009-12-31
Hi, Szaemon.  Did you ever see this problem solved?  I can't find an answer anywhere, except possibly [here]("http://translate.google.com/translate?hl=en&sl=it&tl=en&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%3Ftopic%3D326879.msg2503258").

---

### Post by rCXer on 2009-12-31
He posted [this]("http://vegastrike.sourceforge.net/forums/viewtopic.php?f=1&t=15060") at the vegastrike forums.

---

### Post by Jesdisciple on 2009-12-31
Yeah, that's the same solution I found at ubuntu-it, and for some reason it doesn't solve the problem.  I still get the error about factions.xml.  Any further help would be great.

---

### Post by rCXer on 2009-12-31
It may be that vegastrike can't find your data directory.  When I installed it from SVN I had to create symbolic links to the executable in the data folder as described [here](http://vegastrike.sourceforge.net/mediawiki/index.php?title=HowTo:Checkout_SVN_(Ubuntu_Linux)#Setup). I then just run vegastrike through the those links.

---

### Post by Jesdisciple on 2009-12-31
Just for the record, I've tried using the rar, deb, and I think tar.bz2 archives so far.  I've symlinked to the data directory from ~, installed it there in the first place (just now), and installed from Synaptic.  I'm not sure whether the 0.4.x in the repos works because I abandoned it after seeing it wasn't up to date and didn't have my screen size (1280x800).  Sometimes it doesn't crash while reading factions.xml but segfaults after printing the contents (I think this only happened while I used the symlink).

I don't have a 'data' directory, so I thought I'd see where my vssetup is:```
$ whereis vssetup
vssetup: /usr/local/bin/vssetup
$ readlink /usr/local/bin/vssetup
/home/USER/vegastrike-0.5.0/bin/vssetup-32
```

EDIT: I just got one of the segfaults:```
The names of the joysticks are:
FactionXML:LoadXML factions.xml
Contents of star system:
<system name="Empty" background="backgrounds/black" nearstars="0" stars="0" starspread="0"  y="0" z="0" x="0">
</system>

Segmentation fault
```

---

### Post by rCXer on 2009-12-31
> **Jesdisciple said:**
> I'm not sure whether the 0.4.x in the repos works because I abandoned it after seeing it wasn't up to date and didn't have my screen size (1280x800).
Yeah the one in the repos is broken :(  See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/vegastrike-data/+bug/403698").
> **Jesdisciple said:**
> I don't have a 'data' directory

If you are using the tar.bz2, rar or SVN version the data directory should be exactly where you unpacked the archive.  For example on my system I unpacked the archive to...
```

/home/username/vegastrike/

```
This folder contains 2 subfolders...
```

/home/username/vegastrike/data
/home/username/vegastrike/vegastrike

```
... The first being my data directory.  Consider posting at the [vegastrike forums]("http://vegastrike.sourceforge.net/forums/").  They know far more about this than me.

---

### Post by Jesdisciple on 2010-01-04
As I recall, only the .deb archives were split into 'vegastrike' and 'data' folders - and that was because they were archived separately.

Anyway, sorry I took so long to reply.  But now that I got back on this the vegastrike forums are down.  I guess I'll try the IRC as suggested.

---

