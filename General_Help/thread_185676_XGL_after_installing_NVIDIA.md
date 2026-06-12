---
title: "XGL after installing NVIDIA"
date: 2006-06-01
forum: General Help
---

### Post by maka on 2006-06-01
Hi all,

I was able to install my graphics drivers for my GEFORCE 5200FX using:
  [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
Then I was able to install XGL/COmpiz using:
[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Xgl.2FCompiz_.28Nvidia.29)
[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

XGL/Compiz works now but for some reason, under Applications->System Tools->NVIDIA Settings... it doesnt seem to detect my graphics card anymore but it showed the settings there before I installed XGL.  I was wondering if that meant NVIDIA is broken or no longer installed? because when I try:
```
sudo apt-get install nvidia-glx
```
it says NVIDIA is sitll installed and inside my xorg.conf file, nvidia is still supposedly  detected in there.

anyone share this problem or know whats wrong?

Thanks!

---

### Post by RAOF on 2006-06-01
The nvidia-settings tool requires an extension to the X server, provided by the nvidia drivers.  The XGL server is built on top of the X server which uses the nvidia drivers, but it **doesn't** provide this extension, so nvidia-settings **won't** work in XGL.  This is normal, and does not indicate that you've lost your nvidia drivers.

---

### Post by maka on 2006-06-01
[QUOTE=RAOF]The nvidia-settings tool requires an extension to the X server, provided by the nvidia drivers.  The XGL server is built on top of the X server which uses the nvidia drivers, but it **doesn't** provide this extension, so nvidia-settings **won't** work in XGL.  This is normal, and does not indicate that you've lost your nvidia drivers.[/QUOTE]

thanks for the quick reply!

After installing XGL, I am unable to play CounterStrike 1.6 in OpenGL, and requires me to run in software mode that doesnt work too well...   basically unplayable.

Before installing XGL, i was able to play in OpenGL with no problems.  I don't think this is normal... :-|

---

### Post by RAOF on 2006-06-01
[QUOTE=maka]thanks for the quick reply!

After installing XGL, I am unable to play CounterStrike 1.6 in OpenGL, and requires me to run in software mode that doesnt work too well...   basically unplayable.

Before installing XGL, i was able to play in OpenGL with no problems.  I don't think this is normal... :-|[/QUOTE]
Nope, that's totally normal.  XGL doesn't work very well with other things that want fast OpenGL use.  There's a script, somewhere on the forums, which starts up a **new**, non-XGL X-server and runs the game in that.  That way, you get OpenGL acceleration.  I'll look for it, if you want.  [Here's a link to a thread related, at least ;)]("http://www.ubuntuforums.org/showthread.php?t=163625&highlight=game+XGL+script")

---

### Post by maka on 2006-06-01
> **RAOF]Nope, that's totally normal.  XGL doesn't work very well with other things that want fast OpenGL use.  There's a script, somewhere on the forums, which starts up a **new**, non-XGL X-server and runs the game in that.  That way, you get OpenGL acceleration.  I'll look for it, if you want.  [URL="http://www.ubuntuforums.org/showthread.php?t=163625&highlight=game+XGL+script"]Here's a link to a thread related, at least  said:**
> 

hmm, yeah I'd like to get that OpenGL acceleration... if you can find it that'd be great.  Thanks a lot. :-D

---

### Post by grendelkhan on 2006-06-01
I couldn't get Xgame to work, but these scripts work for me like a charm - no issues at all:

[http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

---

### Post by maka on 2006-06-01
[QUOTE=grendelkhan]I couldn't get Xgame to work, but these scripts work for me like a charm - no issues at all:

[http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)[/QUOTE]

wow thanks! cuoldnt figure out how to get xgame working, but this worked like a charm. :cool:

---

### Post by Mr.Auer on 2006-06-01
Yes, that works for me too..I got two boxes with FX 5200 .. Just sold my Radeon 2 days ago and bought a second FX 5200 just to get XGL+Compiz working, theyre sooo great :) and now all my games work flwlessly too. Also FX 5200 is so very cheap but can still run all Linux games..And is quiet as its fanless usually..

---

### Post by maka on 2006-06-02
[QUOTE=Mr.Auer]Yes, that works for me too..I got two boxes with FX 5200 .. Just sold my Radeon 2 days ago and bought a second FX 5200 just to get XGL+Compiz working, theyre sooo great :) and now all my games work flwlessly too. Also FX 5200 is so very cheap but can still run all Linux games..And is quiet as its fanless usually..[/QUOTE]

yea, i love my fx 5200 also :)

---

