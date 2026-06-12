---
title: "Can anyone help with compizconfig manager animations installations"
date: 2010-11-23
forum: General Help
---

### Post by ubunewbi on 2010-11-23
Hello everyone, I am installing the cube interface and all went well and i have the cube, I then started to play with the animations and I only have a few. On the tutorials screen shot [ [http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy](http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy) ] he had a bunch of animations , I want to do the air plane and the fire effect when closing windows but I cannot find any downloads for the animations just themes. 

Also is there a way to put a workspace on the top and bottom of the cube?

Thanks in advance for helping this struggling noob

I can't believe I didn't mention this but the main effect I want is the exploding windows like on knoppix.

---

### Post by flipper T on 2010-11-23
try here:

[http://www.youtube.com/watch?v=gfwt-2MuMMw](http://www.youtube.com/watch?v=gfwt-2MuMMw)

to be honest, any google search would quickly answer this question,

as to having workspace on bottom face? neat idea. no idea.

---

### Post by ubunewbi on 2010-11-23
I have tried this already and it says I am running the newest version ( Of course I ran some searches before asking here I am not a total dolt and I wouldn't want to waste anyone's time if I could find the answer so easily) 

Maybe I didn't explain well enough, inside my compizconfig settings manager I do not have the choices that are shown on the video like the animations add ons or the 3d windows. Attached is a screen shot of the compizconfig manager on my pc compare it with the vid and you will see what i am talking about. (1:30 seconds into the vid on youtube )

are those options not available in 10.10?

here is also a screen shot of vid

---

### Post by nl4m on 2010-11-23
You are missing the package. I *THINK* the code to get it is:
```
sudo apt-get install compiz-fusion-plugins-extra
```Once installed, launch Compiz. Near the lamp icon look for a paper airplane icon with the caption "Animations Add-on". If the code does not work I'm sending you a picture of all the packages I have installed. Go to your "Ubuntu Software Center" and type in "Compiz" in the search menu and make sure the you install all the packages that I have. Once you get the airplane icon go ahead and check the box to activate it. Then back out and click on the golden lamp. It looks like Aldines genie lamp.  On top click the "Closing Animation" tab. In the drop down menu of "Animation Selection: " click on the first one that says "fade   80    ((type=normal....))" then click on the "Edit" button below. Under the "Close Effect: " change "Fade" to "Fire". 

There is an easier way of doing this. First make sure that you have the paper airplane checked. Then go to your desktop and right click. Choose "Change Desktop Background", choose the "Visual Effects" tab, and if "Extra" is checked you'll have the option to add fire to the windows that you close.

---

### Post by flipper T on 2010-11-23
refer you back to same video, 1:01 minutes in approx

---

### Post by ubunewbi on 2010-11-23
That did it I now have all the  choices. 

Thank you very much for the code

Have a happy turkey day ( well I guess it's not very happy for the Turkey ) 

Thanks again

I cannot find the fire option when changing fade when i click on fade it just gives me the choices in the random section.

Is there something else i am missing?

Thanks

---

### Post by nl4m on 2010-11-23
Hee hee... With me the Turkey will be happy. I'm a vegetarian :) 

Anyway... You're welcome.

---

