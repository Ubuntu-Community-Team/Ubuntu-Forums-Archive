---
title: "How do I change the window movement key in 11.10?"
date: 2011-11-10
forum: General Help
---

### Post by iisdev on 2011-11-10
I'm using Unity-2D under Metacity on a fresh install of 11.10 and I need to change the window movement key (to avoid conflicts with applications that I use daily). 

This used to be a simple setting change in 11.04. ('Window Preferences' under 'System Settings') In 11.10 this was completely removed!

Any ideas?

---

### Post by vinay_wagh on 2011-11-10
It is simple in 11.10 as well. Go to **System Settings**, click on **Keyboard** then click on **Shortcuts** tab and then jump to **Navigation**. 

HTH...

-- VInay
P.S.
See the attached screenshot.

---

### Post by iisdev on 2011-11-10
> **vinay_wagh said:**
> It is simple in 11.10 as well. Go to **System Settings**, click on **Keyboard** then click on **Shortcuts** tab and then jump to **Navigation**. 

HTH...

-- VInay
P.S.
See the attached screenshot.

No, that's not the one I want. I need to change the 'Movement Key' which was previously changeable under 'Window Preferences':
 
[IMG]http://i.stack.imgur.com/7VISB.png[/IMG]

---

### Post by Antron89 on 2011-11-10
You can change this with the gconf-editor.

The Value of "/apps/metacity/general/mouse_button_modifier" is "Alt" by default, I changed "Alt" to "Control" and now it works with the control key for me.

---

