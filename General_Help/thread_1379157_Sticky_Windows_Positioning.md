---
title: "Sticky Windows Positioning"
date: 2010-01-12
forum: General Help
---

### Post by richwein on 2010-01-12
There is an interesting feature in Ubuntu.  When you move a window near another window or the edge of a screen, within a certain range the window snaps to the other window.

Is there a way to turn this characteristic off ?

thank you,

rich

---

### Post by richwein on 2010-01-18
One answer is to  install compiz fusion : 
sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins emerald

After that you will find the new tool in the menus: system-preferences-CompizConfig 

This offers a ways to set all kinds of crazy behaviours in your display that I didn't know about..

---

### Post by mcduck on 2010-01-18
Compiz is already installed by default, so the above commands do nothing. However installing the Compizconfig settigs Manager is the key, as that's what allows you to configure Compiz plugins in more detail than the two presets available in the Appearance-dialog.

So just install that, and turn off the "Snappy windows"-plugin.

Also holding down Shift while moving windows should disable snapping.

---

### Post by richwein on 2010-01-20
Thanks, little by little I'll learn what's available in ubuntu.

You are right, the CompizConfig Settings Manager was all that I needed and I did get it installed as the first item on the apt-get install line, and the Ubuntu was smart enough to not screw up what was already there even though I didn't realize it was already there. 

And, there are 1 million options in the CompizConfig Settings Manager, if you click windows snapping icon, it takes you to two detailed pages bindings and behaviour which get to every possible parameter.  And, even your mention of the Shift Key  to Avoid Snap Modifier can be changed to another key. 

Another thing that I'd like to modify is the range at which the window resize icon appears, and I'll possibly find it in compiz.

There is a forum, wiki and other useful help at compiz.org.

---

### Post by epictetus on 2010-05-31
> **mcduck said:**
> Compiz is already installed by default, so the above commands do nothing. However installing the Compizconfig settigs Manager is the key, as that's what allows you to configure Compiz plugins in more detail than the two presets available in the Appearance-dialog.

So just install that, and turn off the "Snappy windows"-plugin.

Also holding down Shift while moving windows should disable snapping.

I'm having trouble with my sticky windows. The behavior is the opposite of what it should be. They're turned on, but I only get sticky windows when I press the shift key. I'd *like* to have them on without having to press a modifier.

---

### Post by primetime34 on 2010-05-31
> **epictetus said:**
> I'm having trouble with my sticky windows. The behavior is the opposite of what it should be. They're turned on, but I only get sticky windows when I press the shift key. I'd *like* to have them on without having to press a modifier.


+1.....same issue

---

### Post by epictetus on 2010-05-31
> **primetime34 said:**
> +1.....same issue

I feel dumb.

Open "CompizConfig Settings"
Click on "Wobbly Windows" (I assume you have that turned on.)
Click on the checkbox for "Snap Inverted" (to turn it on)

Back to cool snappin for me!

---

### Post by primetime34 on 2010-06-01
> **epictetus said:**
> I feel dumb.

Open "CompizConfig Settings"
Click on "Wobbly Windows" (I assume you have that turned on.)
Click on the checkbox for "Snap Inverted" (to turn it on)

Back to cool snappin for me!


Thanks for the help..I never would have figured that out on my own.

---

