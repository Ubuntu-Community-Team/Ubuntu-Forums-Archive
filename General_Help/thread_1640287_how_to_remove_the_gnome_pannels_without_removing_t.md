---
title: "how to remove the gnome pannels without removing them?"
date: 2010-12-07
forum: General Help
---

### Post by Lancro on 2010-12-07
This needs a brief explanation...

As you know pannels can be hidden, thats how I have them now, but when I put the cursos at the very top, or bottom, of the screen, they pop up, I want them out of my screen, BUT, I want a way to return them if someday I want them to return, so I want to remove the pannels, with the option of restoring them if I want to.

Thanks.

---

### Post by argedion on 2010-12-07
Right click the panel in question choose properties on the General tab choose Show Hide Buttons (Place a check in the box) click close now display panel and click the new arrow this will hide the panel to the side and now when you move your mouse to the top the panel wont show (HINT: Choose the arrow opposite of how you click the X at the top either left or right)

---

### Post by Lancro on 2010-12-07
> **argedion said:**
> Right click the panel in question choose properties on the General tab choose Show Hide Buttons (Place a check in the box) click close now display panel and click the new arrow this will hide the panel to the side and now when you move your mouse to the top the panel wont show (HINT: Choose the arrow opposite of how you click the X at the top either left or right)

I have left the upper pannel, I can restore the bottom one from it, but the button solution does not convince me, I would rather prefer something that wipes it, without leaving any graphics on the screen.

Thanks.

---

### Post by Lancro on 2010-12-09
Bump.

---

### Post by tredegar on 2010-12-09
If you use [panelrestore]("http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/") to back up your panel you can delete it completely, and then restore it later.

---

### Post by tylerannosaurus on 2010-12-09
Do you have some sort of dock? I used Ubuntu Tweak to change the settings so that my default panel is Docky.

You can also go through gconf-editor to change this yourself Alt+F2, type gconf-editor, then go to desktop/gnome/session/required_components. Where it says panel, you can change it to whatever command you want. I'm not sure that you can just delete it entirely though. Seems the ability to use Alt+F2 disappears after removing your panel, too, so you'll need some other way to edit gconf if you do this.

Hope that helps!

---

### Post by Lancro on 2010-12-09
> **tylerannosaurus said:**
> Do you have some sort of dock? I used Ubuntu Tweak to change the settings so that my default panel is Docky.

You can also go through gconf-editor to change this yourself Alt+F2, type gconf-editor, then go to desktop/gnome/session/required_components. Where it says panel, you can change it to whatever command you want. I'm not sure that you can just delete it entirely though. Seems the ability to use Alt+F2 disappears after removing your panel, too, so you'll need some other way to edit gconf if you do this.

Hope that helps!

I use AWN dock, with ubuntu tweak I made a backup of my desktop, but I didnt saw an option for changing the pannels to awn or deleting them, how do you do that?.

Thanks.

---

### Post by tylerannosaurus on 2010-12-09
> **Lancro said:**
> I use AWN dock, with ubuntu tweak I made a backup of my desktop, but I didnt saw an option for changing the pannels to awn or deleting them, how do you do that?.

Thanks.

It's under the heading "Session Control". The default is gnome-panel, not sure what the command to bring up awn is (maybe just awn?) for me I just typed "docky"...same command you'd use in terminal. You'll have to log out/in for the effect to take place.

---

### Post by tredegar on 2010-12-09
> **Lancro said:**
> Bump.
You bump your own post. I reply. You ignore.

If my post at #5 wasn't helpful, please say why. That way I can offer better (or less) advice in the future :)

Best wishes.

---

### Post by Lancro on 2010-12-09
> **tredegar said:**
> You bump your own post. I reply. You ignore.

If my post at #5 wasn't helpful, please say why. That way I can offer better (or less) advice in the future :)

Best wishes.

Sorry, I forgot, I have downloaded the program, a script to restore the default pannels might become usefull, but I cant delete the top pannel, I have deleted the lower pannel, but now I have the top pannel, and I dont know how to delete it, I need a script to delete it as well?, I dont know how to get rid of that pannel, with your shell script I dont need to keep one pannel more, but I need the option to delete it.

Thanks.

---

### Post by Lancro on 2010-12-09
> **tylerannosaurus said:**
> It's under the heading "Session Control". The default is gnome-panel, not sure what the command to bring up awn is (maybe just awn?) for me I just typed "docky"...same command you'd use in terminal. You'll have to log out/in for the effect to take place.

The executable is avant-window-navigator I put that one, I will relog to see if I can delete the pannel left.

Edit: It worked, no pannels, thanks to all that have posted.

Thanks.

---

