---
title: "Compiz goof"
date: 2010-12-30
forum: General Help
---

### Post by Chasey on 2010-12-30
I'm breaking down! Any help would be great! 

Installed 10.10 on a older Toshiba Satellite, worked great! I wanted the "cube" effect for my desktops. Installed Compiz it worked but not great... Kinda buggy (old toshiba) so I uninstalled via synaptic. After that I loose every basic effect that I guess would be what metacity/compiz/emerald offers: True transparency (Terminal), wobbly windows, ect. (I like these effects and they worked fine before) So then I installed Emerald and it brings all that back. **1st problem** it gives me an ugly "Windows style" theme with the buttons on the right side. I could compromise but I really really don't like it. **2nd problem **I can use ```
metacity --replace
```and it goes back to the original but then again I loose the wobbly windows and true transparency. After that adjusting visual effects in Appearance Preferences brings all the Emerald "Windows looking frame theme" back. I've even```
 rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```. this also really brought it back to square one but still changing the setting still gives me ugly windows.

I never really post because I can usually find answers to my questions. I've learned a lot from this problem except the solution. Thanks again everybody!

---

### Post by daqron on 2010-12-30
Maybe I am misunderstanding your question, but can you simply change the theme in the Emerald Theme Manager (System > Preferences or emerald-theme-manager from terminal)?

---

### Post by Chasey on 2010-12-30
That's the problem I cannot find the default in Emerald... It's set as vrunner but all the other themes in there still have the windows style buttons on the right.

---

### Post by daqron on 2010-12-30
So it sounds like you need Emerald in order for your compiz effects to work (which doesn't seem right to me), but you want to keep your regular Ubuntu clearlooks/humanity theme? If that is correct, maybe try this: [http://ubuntuforums.org/showthread.php?t=609082](http://ubuntuforums.org/showthread.php?t=609082)

---

### Post by Chasey on 2010-12-30
Thanks for your response and you are correct. I tried editing that but seemed to do nothing.

Is vrunner the default? I don't remember really messing with emerald I just happened to notice it after installing ccsm.

---

### Post by Chasey on 2010-12-30
Some screen shots might be helpful:

The first one is with Emerald and or the visual effects set to Normal but it evokes the MS Windows buttons on the top right of the frame.

The second one is after the metacity --replace and you can notice that the process is still running even as I'm typing this. (Weird right?) it looks like it's keeping the "true transparency" (this time)  and the nice ("Clearview/human?") look, but no wobbly windows.

  
[IMG]file:///home/chasey/Desktop/withemeraled.png[/IMG][IMG]file:///home/chasey/Desktop/withemeraled.png[/IMG]

---

### Post by daqron on 2010-12-30
> **Chasey said:**
> I tried editing that but seemed to do nothing.
Define "nothing" :) Does that mean it ignored you and continued applying the Emerald theme? Did that persist after a logout/login?

---

### Post by Chasey on 2010-12-30
No noticeable change... I did restart.

---

### Post by Chasey on 2011-01-04
Anybody else feel like taking a whack at this?

---

### Post by stinkeye on 2011-01-04
Can you explain what exactly you want?

Run compiz with emerald decorator?
Run compiz with gtk-window-decorator?
or 
Run Metacity?

If you want to run compiz with metacity style borders and titlebar run...
```
gtk-window-decorator --replace
```


Install fusion-icon...
```
sudo apt-get install fusion-icon
```
Find in the System tools menu and loads in the tray with a right click menu.

---

### Post by Chasey on 2011-01-04
Stinkeye good on ya mate thank you! I guess I did not have compiz-gnome installed (Kinda weird). Once installed I got the metacity look I wanted and fusion-icon with GTK Window Decorator did the rest.\\:D/

---

