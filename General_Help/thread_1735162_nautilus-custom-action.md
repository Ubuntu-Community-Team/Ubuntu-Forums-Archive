---
title: "nautilus-custom-action"
date: 2011-04-21
forum: General Help
---

### Post by LewRockwellFAN on 2011-04-21
I installed nautilus-custom-action and it works great. I've added maybe a dozen entries and they all work. I recommend it to all as a useful tool and fun toy. But my context menus are getting kind of crowded. So I would love to group items into submenus. I figured that was what "File/New Menu" was for but I can't seem to get anywhere with that. There is nothing in the help menu but an "about" and I can't find anything like an online manual that goes into either how to do this if it is possible or what the  "File/New Menu" dialogue is for. I've sifted the grumz.net site that seems to be the focal point for this program and looked at a lot of google results that just seem to be about the "File/New Action" stuff which is pretty intuitive anyway. So, I have 2 questions:

1-Can this be done, and if so how?
2-What am I SUPPOSED to be able to do with  "File/New Menu" anyway? Is there an explicit walk through somewhere on it?

Any insight or suggestions on either point would be appreciated.

---

### Post by An Sanct on 2011-04-21
In the menu (in nautilus-custom-action), click "File"->"New menu", name the menu and then drag&drop the existing actions into that submenu

May I ask where you got the actions from? I cant find any online (khm ... I didn't even try ... tho)

---

### Post by LewRockwellFAN on 2011-04-21
> **An Sanct said:**
> In the menu (in nautilus-custom-action), click "File"->"New menu", name the menu and then drag&drop the existing actions into that submenu

May I ask where you got the actions from? I cant find any online (khm ... I didn't even try ... tho)

Thanks, An Sanct! That works great!

As for actions, I've just been composing them in the add action dialogue. Here are some examples:
Thunar HERE
   thunar
   %d
Thunar in selected directory
   thunar
   %M
Thunar-root HERE
  sudo thunar
   %d
Thunar-root in selected directory
   sudo thunar
   %M

I think you can adapt pretty much any commands you could issue from the command line. You could probably adapt pretty much any of the thunar custom actions also and google will show a LOT of published thunar custom actions.

---

