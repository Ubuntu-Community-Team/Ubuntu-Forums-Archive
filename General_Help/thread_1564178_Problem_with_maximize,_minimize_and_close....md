---
title: "Problem with maximize, minimize and close..."
date: 2010-08-30
forum: General Help
---

### Post by fahd1951 on 2010-08-30
Hello there,

For a week now I have a problem with my buttons that the are on the left side of the Ubuntu 10.04....

Every time I restart my computer or switch it off and start it again I get this issue...

I solve it temperately every time by pressing left click on the desktop and go the the "Change the background" and then I go to the visual effects  and choose the second one and every time I have to do this to show them and to be honest I am sick of it....

Is there any other way to do it or something?

thanks

fahd1951

---

### Post by inameiname on 2010-08-30
From what I gather, it sounds as though you want the buttons on the right, and they keep staying over on the left. Is that what you are saying? If so, just copy and paste this into the terminal:

gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"

---

### Post by fahd1951 on 2010-08-30
Oh no.....

Now the buttons on the right and that I do not want....

I copied your code and it made the problem can you tell me how to change it...

and the real issue here not that it is on the right or left....

It's just keep disappearing when I restart the computer that is the issue?

---

### Post by inameiname on 2010-08-30
Oh, I'm sorry. I couldn't understand just what you meant. Anyway, to change it back, it's one of these (I can't remember which button was by the 'X' or "close" button, "minimize" or "maximize", so just pick the right one):

gconftool-2 --set /apps/metacity/general/button_layout --type string "close,maximize,minimize:menu"

gconftool-2 --set /apps/metacity/general/button_layout --type string "close,minimize,maximize:menu"

As for your problem, so you're saying the entire panel on the top disappears? I'm not sure why going to the Visual Effects menu or changing the background would have anything to do with it though. But if it fixes it, even temporarily, cool.

---

### Post by fahd1951 on 2010-08-30
I go there because when the computer tries to look for the drivers it gives me back the whole panel and I do not know why it does that....

anyway if you have any idea share it with me....

thanks lot

---

### Post by inameiname on 2010-08-30
Looks for drivers? Strange. Well then, I understand why you go there. 

Uhm, I'm afraid I can't think of any good explanation as to what is causing a total panel loss. Certainly not in regards to some sort of drivers not working/installing correctly. 

It's strange how it's only that panel, as if it was some gnome error, it'd probably effect more than just that. So I bet you can rule gnome as the culprit. Seeing as how you are messing around with the desktop effects, ie, I believe, which has to do with Compiz, it might be something with it. Have you received a recent Compiz update? Or graphic card one? 

IDK really, sorry. Hopefully somebody will be better at shedding some like on your troubles.

---

### Post by inameiname on 2010-08-30
Here is another user's thread that may help you:

[http://ubuntuforums.org/showthread.php?t=1558812](http://ubuntuforums.org/showthread.php?t=1558812)

---

