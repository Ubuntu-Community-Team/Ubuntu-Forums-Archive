---
title: "Installing WOW?"
date: 2011-04-06
forum: General Help
---

### Post by branko.savic on 2011-04-06
Have seen a lot of videos on youtube that you can play WOW on ubuntu, but could anyone tell me how to install it in ubuntu?

---

### Post by techunit on 2011-04-06
I can point you in the right direction. Look into WINE and PlaysOnLinux. Doesn't seem to work well with 64bit computers.

---

### Post by branko.savic on 2011-04-06
> **techunit said:**
> I can point you in the right direction. Look into WINE and PlaysOnLinux. Doesn't seem to work well with 64bit computers.

ok, and a 64-bit pc is what I have!

---

### Post by gerowen on 2011-04-06
If you run into graphical issues with wine, try executing WoW with OpenGL instead of DirectX.  Wine's DirectX support is touch-and-go since it's all reverse engineered, but OpenGL is natively supported by Linux and OSX.  To run WoW with OpenGL just add this line to the config.wtf file after you've got it installed:
```

SET gxApi "opengl"

```

Using these options I've succefully ran WoW on a 64 bit Linux PC.  The only downside is that, since I was running it with Wine, the framerate was a bit lower than in Windows, but it was perfectly playable.

---

### Post by branko.savic on 2011-04-06
> **gerowen said:**
> If you run into graphical issues with wine, try executing WoW with OpenGL instead of DirectX.  Wine's DirectX support is touch-and-go since it's all reverse engineered, but OpenGL is natively supported by Linux and OSX.  To run WoW with OpenGL just add this line to the config.wtf file after you've got it installed:
```

SET gxApi "opengl"

```

Using these options I've succefully ran WoW on a 64 bit Linux PC.  The only downside is that, since I was running it with Wine, the framerate was a bit lower than in Windows, but it was perfectly playable.

Ok, thank you for the information, I will try that out!

I have now managed to get the installation for WOW going, but do you know how I can get the latest update WOW cataclysm installed?

---

### Post by IHeequ5i on 2011-04-06
The first time you run WoW after the install, it will try to patch to current level. My advice is to let the patch completely finish before trying to sign in at all.

---

### Post by branko.savic on 2011-04-06
> **branko.savic said:**
> Ok, thank you for the information, I will try that out!

I have now managed to get the installation for WOW going, but do you know how I can get the latest update WOW cataclysm installed?

umm, where do I find the config.wtf file?

Have looked all over!

---

### Post by Zorgoth on 2011-04-06
...\World of Warcraft\WTF\Config.wtf

It might not exist if you've never run WoW or changed any settings before.  If not, you can copy one from many places on the internet.

What graphics card do you have?  If it is an Intel card it could be hard to get WoW going.  nVidia is best for wine and ATI is pretty decent too.

---

### Post by branko.savic on 2011-04-07
> **Zorgoth said:**
> ...\World of Warcraft\WTF\Config.wtf

It might not exist if you've never run WoW or changed any settings before.  If not, you can copy one from many places on the internet.

What graphics card do you have?  If it is an Intel card it could be hard to get WoW going.  nVidia is best for wine and ATI is pretty decent too.

I have Nvidia!

I got it working just fine now... thank you everyone for your help!

Just one more question, in windows I had a program in wow that changed the look of the game icons! Does anyone know what that program is called, and where I can find it again?

And if that works in ubuntu?

Thanks!

---

### Post by mendhak on 2011-04-07
> **branko.savic said:**
> I have Nvidia!

I got it working just fine now... thank you everyone for your help!

Just one more question, in windows I had a program in wow that changed the look of the game icons! Does anyone know what that program is called, and where I can find it again?

And if that works in ubuntu?

Thanks!
If anything, that would be an add-on.  If you go to [wow.curse.com]("http://wow.curse.com/downloads/wow-addons/default.aspx"), you should be able to find the add-on you're looking for. When you find it, choose manual install.  

You'll get a zip file.
Unzip that zip file, then copy it over to the Interfaces > Addons directory in your WoW directory.  
Start WoW, and it should be there.

---

