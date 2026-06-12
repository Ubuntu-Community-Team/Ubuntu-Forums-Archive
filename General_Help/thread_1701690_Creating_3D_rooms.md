---
title: "Creating 3D rooms?"
date: 2011-03-06
forum: General Help
---

### Post by savaan on 2011-03-06
I have no clue what forum section this would go under. I'm looking for a renderer that will allow me to create a 3D room. I don't want a CAD program. I want a program that will allow me at some point to render the project, then using my mouse or arrow keys, "walk" through the room seeing such details as patterned walls, carpeting and any ambient sounds that it will allow me to put in.

---

### Post by Habitual on 2011-03-06
Description: Very fast and versatile 3D modeller/renderer
 Blender is an integrated 3d suite for modelling, animation, rendering,
 post-production, interactive creation and playback (games). Blender has its
 own particular user interface, which is implemented entirely in OpenGL and
 designed with speed in mind. Python bindings are available for scripting;
 import/export features for popular file formats like 3D Studio and Wavefront
 Obj are implemented as scripts by the community. Stills, animations, models
 for games or other third party engines and interactive content in the form of
 a standalone binary and/or a web plug-in are common products of Blender use.

```
sudo apt-get install -y blender
```
[http://www.blender.org/](http://www.blender.org/)

---

### Post by |{urse on 2011-03-06
+1 @ blender. I've used it for small renderings (logos and such) but it's a full featured engine with an easy to use gui.

---

### Post by savaan on 2011-03-06
really? I was told blender was good for model rendering, but 3d walkthrough architecture?

---

### Post by Habitual on 2011-03-07
> **savaan said:**
> really? I was told blender was good for model rendering, but 3d walkthrough architecture?

This sure looks 3D with architecture to me. :)
[http://www.blender.org/features-gallery/feature-videos/?video=game_engine_one](http://www.blender.org/features-gallery/feature-videos/?video=game_engine_one)
And don't believe everything you hear!

---

### Post by savaan on 2011-03-07
wow...looks like that's my program then :) I was merely going for a single room, single light, some designs. That's an amazing clip. Thanks!

---

### Post by rubylaser on 2011-03-07
You might want to spend some time in Blender modeling first.  Because, if you're planning on doing an interactive walkthrough with the Game Engine, you're going to be spending alot of time writing logic (in Python) for your objects.  I use Blender daily to model commercial buildings and interiors, and it works great for this (not in the Game Engine).  With Blender 2.5, the UI has been greatly improved and plugins have been developed for most 3rd party renderers as well.  You might try use Luxrender if you're going for a photo realistic look.

If you're trying to do an animation sequence the Blender internal engine works very well too.  I find that doing it this way, I have a reproducible result to show a client rather than sporadically moving around in my scene, like you would in the Game Engine.

---

### Post by grahammechanical on 2011-03-07
No ducks were harmed in the making of that video.

---

### Post by rubylaser on 2011-03-07
This is martinsupitis's latest video (the person that made the bathroom demo), if you're interested.
[http://www.youtube.com/watch?v=xsV9Ln_TLa8&feature=player_embedded]("http://www.youtube.com/watch?v=xsV9Ln_TLa8&feature=player_embedded")

---

### Post by savaan on 2011-03-09
i'm learning from scratch lol so i'll be using the guides heavily. my goal is to upload this to a website accessible via a link so that visitors can walk through the room and maybe interact with a few items


my flash player crashes on a lot of Youtube vids these days :/ I can't view that last link

---

