---
title: "[HELP] Eternal Lands Crash"
date: 2011-02-28
forum: General Help
---

### Post by chambersmt on 2011-02-28
I have installed and updated Eternal Lands. The game crashes on startup, I followed a few of the suggestion on how to correct the issue, but it still crashes to the desktop.

Q1: Eternal Lands crashes on game start up, how do I get the game to work?

-------------------------------------------

This information about your graphic hardware and software may help.
Output from "lspci | grep -i vga":
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
Output from "glxinfo | head -5":
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4

The following is your error log contents.  Note it is overwritten each time you run the game.

Log started at 2011-02-28 08:31:08 localtime (EST)

[08:31:08] Using the server profile: main
[08:31:08] Window size adjusted to 1014x713
[08:31:08] GL_ARB_multitexture extension found, using it.
[08:31:08] GL_EXT_compiled_vertex_array extension found, using it.
[08:31:08] GL_ARB_point_sprite extension found, using it.
[08:31:08] GL_ARB_texture_compression extension found, using it.
[08:31:08] Couldn't find the GL_EXT_texture_compression_s3tc extension, not using it...
[08:31:08] GL_SGIS_generate_mipmap extension found, using it.
[08:31:08] GL_ARB_shadow extension found, using it.
[08:31:08] GL_ARB_vertex_buffer_object extension found, using it.
[08:31:08] GL_EXT_framebuffer_object extension found, using it.
[08:31:08] GL_EXT_draw_range_elements extension found, using it.
[08:31:08] GL_ARB_texture_non_power_of_two extension found, using it.
[08:31:08] GL_ARB_fragment_program extension found, using it.
[08:31:08] GL_ARB_vertex_program extension found, using it.
[08:31:08] GL_ARB_fragment_shader extension found, using it.
[08:31:08] GL_ARB_vertex_shader extension found, using it.
[08:31:08] GL_ARB_shader_objects extension found, using it.
[08:31:08] GL_ARB_shading_language_100 extension found, using it.
[08:31:08] GL_ARB_texture_mirrored_repeat extension found, NOT using it...
[08:31:08] GL_ARB_texture_rectangle extension found, NOT using it...
[08:31:08] GL_EXT_fog_coord extension found, NOT using it...
[08:31:08] Couldn't find the GL_ATI_texture_compression_3dc extension, not using it...
[08:31:08] Couldn't find the GL_EXT_texture_compression_latc extension, not using it...

This was the program output:  Note it is overwritten each time you run the game.

---

### Post by dddnw on 2011-04-21
I am getting a similar crash message.  Have you received any replies or fixes:


Oh my, Eternal Lands Crashed - Don't Panic!

A few of things you can try:
1) Make sure your system is up to date, especially your video drivers.
2) If the client crashes repeatedly, try changing some settings.  Either by directly modifying the configuration file (e.g. gedit ~/.elc/main/el.ini). Or clicking the settings button window at the login screen.
	i) Enable the "Poor Man" option in the "Details" tab of the setting window.  Or edit the configuration file and set "#poor_man=1".
	ii) Disable the "Use animation program" option in the "Adv Video" tab of the setting window.  Or edit the configuration file and set "#use_animation_program=0".
	iii) Disable the "Custom Looks Updates" option in the "Server" tab of the setting windows.  Or edit the configuration file and set "#customupdate=0".

If you continue to have problems check the Eternal Lands forums, especially the "Help Me" and "Bug Report" sections.  If you post a message make sure you include information about your system; i.e video driver and version, operating system and version.  Make sure you check your error log for clues too and include the contents in any forum report.

This information about your graphic hardware and software may help.
Output from "lspci | grep -i vga":
01:00.0 VGA compatible controller: nVidia Corporation G84M [Quadro NVS 140M] (rev a1)
Output from "glxinfo | head -5":
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4

The following is your error log contents.  Note it is overwritten each time you run the game.



Log started at 2011-04-21 20:56:30 localtime (EDT)

[20:56:30] Using the server profile: main
[20:56:30] Window size adjusted to 1014x713
[20:56:30] GL_ARB_multitexture extension found, using it.
[20:56:30] GL_EXT_compiled_vertex_array extension found, using it.
[20:56:30] GL_ARB_point_sprite extension found, using it.
[20:56:30] GL_ARB_texture_compression extension found, using it.
[20:56:30] Couldn't find the GL_EXT_texture_compression_s3tc extension, not using it...
[20:56:30] GL_SGIS_generate_mipmap extension found, using it.
[20:56:30] GL_ARB_shadow extension found, using it.
[20:56:30] GL_ARB_vertex_buffer_object extension found, using it.
[20:56:30] GL_EXT_framebuffer_object extension found, using it.
[20:56:30] GL_EXT_draw_range_elements extension found, using it.
[20:56:30] GL_ARB_texture_non_power_of_two extension found, using it.
[20:56:30] GL_ARB_fragment_program extension found, using it.
[20:56:30] GL_ARB_vertex_program extension found, using it.
[20:56:30] GL_ARB_fragment_shader extension found, using it.
[20:56:30] GL_ARB_vertex_shader extension found, using it.
[20:56:30] GL_ARB_shader_objects extension found, using it.
[20:56:30] GL_ARB_shading_language_100 extension found, using it.
[20:56:30] GL_ARB_texture_mirrored_repeat extension found, NOT using it...
[20:56:30] GL_ARB_texture_rectangle extension found, NOT using it...
[20:56:30] GL_EXT_fog_coord extension found, NOT using it...
[20:56:30] Couldn't find the GL_ATI_texture_compression_3dc extension, not using it...
[20:56:30] Couldn't find the GL_EXT_texture_compression_latc extension, not using it...

This was the program output:  Note it is overwritten each time you run the game.

---

