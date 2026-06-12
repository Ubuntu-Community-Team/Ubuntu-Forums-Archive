---
title: "General graphics problem?"
date: 2010-09-23
forum: General Help
---

### Post by Shakkol on 2010-09-23
I think this might go for gaming, but maybe a general graphics problem could be taken into consideration for anything else that might display this error:

```
fixme:d3d:state_wrap (WINED3DRS_WRAP0) Texture wrapping not yet  supported.
```

That was spammed in my terminal after I logged into my character. This was spamming itself before logging into my character:

```
err:d3d_surface:surface_allocate_surface  >>>>>>>>>>>>>>>>>  GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862 
err:d3d_surface:surface_allocate_surface  >>>>>>>>>>>>>>>>>  GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862 
err:d3d_surface:surface_allocate_surface  >>>>>>>>>>>>>>>>>  GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862 
err:d3d_surface:surface_allocate_surface  >>>>>>>>>>>>>>>>>  GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862 
err:d3d_surface:surface_allocate_surface  >>>>>>>>>>>>>>>>>  GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862 
err:d3d_surface:surface_allocate_surface  >>>>>>>>>>>>>>>>>  GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862 
err:d3d_surface:surface_allocate_surface  >>>>>>>>>>>>>>>>>  GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862 
err:d3d_surface:surface_upload_data  >>>>>>>>>>>>>>>>>  GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c /  763 
err:d3d_surface:surface_upload_data  >>>>>>>>>>>>>>>>>  GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c /  763 
err:d3d_surface:surface_upload_data  >>>>>>>>>>>>>>>>>  GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c /  763 
err:d3d_surface:surface_upload_data  >>>>>>>>>>>>>>>>>  GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c /  763 
err:d3d_surface:surface_upload_data  >>>>>>>>>>>>>>>>>  GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c /  763 
err:d3d_surface:surface_upload_data  >>>>>>>>>>>>>>>>>  GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c /  763 
err:d3d_surface:surface_upload_data  >>>>>>>>>>>>>>>>>  GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c /  763 
```

Any idea what it might be? The game is a Windows game called Cloud Nine. Here's a screenshot of the problem in action:
[IMG]http://i52.tinypic.com/27ytn9h.jpg[/IMG]

Any and all help is appreciated. Just to let you all know, I'm not all that advanced in Ubuntu or Linux knowledge, this game is just the only thing keeping me from going completely Ubuntu. I only have Windows installed to play this game, and I've gotten as far as to get this game playing this far, which WAY earlier in the forums people swore it couldn't be done. Well, with the help my myself I got it this far. Now I need help. Thanks.

---

### Post by searchfgold6789 on 2010-09-23
I don't understand... Are you playing this in Ubuntu, or Windows? I'm not familiar with Cloud 9... is it a software game? browser game? downloaded game? What type of grpahics card do you have, and do you recall ever installing drivers for it?
Does it use other software such as Java or Flash?

---

### Post by Shakkol on 2010-09-23
It's a game you download and it's made for Windows, but I have it running in Wine. As far as I know, my drivers installed when I installed Ubuntu. There's no icons requesting restricted drivers, and I have no onboard video, so I'm using a graphics card at it's full resolution. I believe it uses Flash for the options menu, which makes the game crash in Ubuntu. If you have any other questions, feel free to ask.

---

### Post by pedro_orange on 2010-09-23
Presumably you're playing this in WINE? 
I've seen D3D in WINE not render some textures correctly, and switching to OpenGL generally fixes most of the "blackout" issues.

EDIT:
Have you installed Flash?
Have you installed drivers for your graphics card? Generally using the default driver isn't the best.
Does WINE's AppDB have anything to say about this game, it's compatibility etc?

---

### Post by Shakkol on 2010-09-23
> **pedro_orange said:**
> Presumably you're playing this in WINE? 
I've seen D3D in WINE not render some textures correctly, and switching to OpenGL generally fixes most of the "blackout" issues.

EDIT:
Have you installed Flash?
Have you installed drivers for your graphics card? Generally using the default driver isn't the best.
Does WINE's AppDB have anything to say about this game, it's compatibility etc?

APPDB has nothing on this, which is why I want to make this game run so I can confirm that it works.

How do I switch to OpenGL? I know there's no option in the game for that, so there's one in Wine? I don't think installing Flash will make it any better. I think the browser in-game is Internet Explorer, and that has Flash already. You use the browser when you go to buy cash shop items and change options.

I think I'll get those drivers now.

---

### Post by dino99 on 2010-09-23
fixme are not errors

this might be due to game design (bad) or unimplemented libs/fonctions into wine

report your issues on winehq (bugzilla) and google around about this game+linux/ubuntu

as most of complaints are about d3d, you might need to install related lib from winetricks (into a console run: sh winetricks, and look about : d3dx9_28, d3dx9_36, ... Of courseyour game and wine might be closed when you add these files, then load it again.

---

### Post by Shakkol on 2010-09-23
I have googled around. I am the only person to get this far into getting this game to run in Linux.

---

### Post by pedro_orange on 2010-09-23
I'm not sure if you can tell wine to always use OpenGL. If you can, I don't know how. 
I'm more familiar with telling a particular application to run in OpenGL mode (if supported ofc), this can be done usually within the application configuration files. I've never played the game you're referring to, so I'm afraid you'll just have to do some research and some trial and error. 

You've installed Internet Explorer in wine? Flash doesn't generally come bundled with I.E - you have to install it.

---

### Post by searchfgold6789 on 2010-09-23
Have you looked into PlayOnLinux?

---

### Post by dino99 on 2010-09-23
> **Shakkol said:**
> I have googled around. I am the only person to get this far into getting this game to run in Linux.

have added more info in my previous post, this might help a little  ):P

---

### Post by Shakkol on 2010-09-23
When you said to set it to use OpenGL, I thought you meant Wine. It's okay though. And I believe that Flash did come bundled. Let me chack, because when you go to the main site (which is how you log in so it can tell the external app your login info (I don't know why, it's a Korean MMORPG)) the site uses a lot of Flash stuff. The Game Start button on the site is Flash.

---

### Post by Shakkol on 2010-09-23
> **dino99 said:**
> have added more info in my previous post, this might help a little  ):P

Thanks. Installing the Direct X stuff now. Let's hope it works out.
Aww, I got nothing. Well, I'm going to bed and I'll see what happens on my days off.

---

### Post by Shakkol on 2010-09-25
Y'think if I add everything from the "New Overrides for Lirbrary" something might change? Or do those do nothing?

Here are some of the problems the terminal was showing me. Sorry if it seems spammed, this is coming directly from the terminal:

[QUOTE=Terminal]err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 862
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:d3d:state_cullmode Unrecognized/Unhandled WINED3DCULL value 0.
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAPLUMINANCE
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
[/QUOTE]

---

