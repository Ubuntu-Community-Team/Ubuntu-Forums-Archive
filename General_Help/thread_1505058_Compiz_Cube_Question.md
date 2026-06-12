---
title: "Compiz Cube Question"
date: 2010-06-08
forum: General Help
---

### Post by colddepression on 2010-06-08
How do you get images on the top and bottom of the cylinder on the compiz cube/cylinder? Me and my friend has been trying to figure it out on his ubuntu to machine.

---

### Post by WorMzy on 2010-06-08
Install compiz-fusion-plugins-extra, then you'll have the Cube Reflection and Deformation plugin in CompizConfig Settings Manager (ccsm), the caps an be configured in there.

---

### Post by blchinezu on 2010-06-08
there is another thread like this somewhere around here

---

### Post by colddepression on 2010-06-08
We have that and changed the they pic on there but the dang thing isn't changing it.

---

### Post by paparozoumis on 2010-06-08
> **colddepression said:**
> We have that and changed the they pic on there but the dang thing isn't changing it.

Let's hope this attachment can help you a bit so you are sure of where to change the picture for the caps.
I suppose the pictures are saved somewhere on your local partitions, right?

---

### Post by WorMzy on 2010-06-08
Can you take a screenshot of the settings you're using, and post it here?

---

### Post by colddepression on 2010-06-08
Here is the screen shot as you can see its the same

---

### Post by WorMzy on 2010-06-08
When you look at the caps, do you still have the default images, or are they transparent?

---

### Post by colddepression on 2010-06-08
> **WorMzy said:**
> When you look at the caps, do you still have the default images, or are they transparent?

Well I have it transparent for the gears effect but the image for the bottom is a blue box with a arrow and the top is a black and red box

---

### Post by WorMzy on 2010-06-08
Strange. It might be fixed by restarting, but if that doesn't help, then could you:
[LIST][*]install compizconfig-backend-gconf (sudo apt-get install compizconfig-backend-gconf) [*]then open gconf-editor (Alt+F2, gconf-editor, run) [*]then browse to /apps/compiz/plugins/cubeaddon/screen0/options/
[*]Finally, check the values of "bottom_images" and "top_images".
[/LIST]

If they just say fusion-cap-bottom.png, or whatever the default is, then edit them so they're correct.

---

### Post by colddepression on 2010-06-08
> **WorMzy said:**
> Strange. It might be fixed by restarting, but if that doesn't help, then could you:
[LIST][*]install compizconfig-backend-gconf (sudo apt-get install compizconfig-backend-gconf) [*]then open gconf-editor (Alt+F2, gconf-editor, run) [*]then browse to /apps/compiz/plugins/cubeaddon/screen0/options/
[*]Finally, check the values of "bottom_images" and "top_images".
[/LIST]

If they just say fusion-cap-bottom.png, or whatever the default is, then edit them so they're correct.

I did all that and it is showing that my images are the images selected but when I go to the cube it just shows white as my top and bottom not my images

---

### Post by WorMzy on 2010-06-08
Okay, since the image changed (or at least isn't showing the defaults) I think that the plugin is working, but there might be a problem with the path to the image that you're using. Can you double check that the image is where you think it is? Try another image and see if that works.

---

### Post by Manuwash on 2010-06-08
This is my secret LOL instant gratification hidden from the view of the profane:lolflag:

(did it as was explained here, the ubuntu  bum is for fun but Id like to get some proper symbols or something cool later on)

---

