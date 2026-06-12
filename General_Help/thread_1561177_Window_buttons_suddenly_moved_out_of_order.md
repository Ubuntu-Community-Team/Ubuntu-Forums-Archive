---
title: "Window buttons suddenly moved out of order"
date: 2010-08-25
forum: General Help
---

### Post by afonteijn on 2010-08-25
Since a few days I have a strange problem on one of my Ubuntu machines. Before the change the window buttons on the left hand were ordered "close, minimize, maximize" but now the order has changed to "maximize, minimize, close". I don't have this problem on my other two ubuntu machines. 

Is there an easy way to change the order of the buttons. Note: For clarifications sake, I'm not trying to move the buttons to the right side of the screen, it is only about the order.

Thanks!

---

### Post by The Thunder Chimp on 2010-08-25
> **afonteijn said:**
> Since a few days I have a strange problem on one of my Ubuntu machines. Before the change the window buttons on the left hand were ordered "close, minimize, maximize" but now the order has changed to "maximize, minimize, close". I don't have this problem on my other two ubuntu machines. 

Is there an easy way to change the order of the buttons. Note: For clarifications sake, I'm not trying to move the buttons to the right side of the screen, it is only about the order.

Thanks!

Just punch in a terminal:

```

gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"

```

---

### Post by SoFl W on 2010-08-25
Yes there is!

Open up config editor "gconf-editor"

apps->metacity-> general-> button_layout

---

### Post by The Thunder Chimp on 2010-08-25
> **SoFl W said:**
> Yes there is!

Open up config editor "gconf-editor"

apps->metacity-> general-> button_layout

Try this if the terminal fails as it is much longer.

---

### Post by Maverick_Meerkat on 2010-08-25
Greetings,

If you know the name of the theme you are using, you can try something like this:

```
sudo gedit /usr/share/themes/Ambiance/index.theme
```

Substitute the name of the theme you are using for /Ambiance/

make certain that:

```
ButtonLayout=close,minimize,maximize:
```

That is the order they should be listed. Whatever order they are listed is the order they should appear in the GUI.

As an alternative, you can use Window Manager Settings in Ubuntu Tweak to set the location and order of the buttons.

---

### Post by afonteijn on 2010-08-25
Thanks everyone! I've never received so many excellent replies in such a short time! And, it worked like a charm!

---

### Post by The Thunder Chimp on 2010-08-26
Just out of curiosity, which one worked first? Did any of them fail?

---

### Post by Cavsfan on 2010-08-26
The solution to this is one the first page in the sticky under General Help -

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1469475_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1469475")

And it says this: [B]Using gconf-editor is not the right approach as this could bork  future themes. 
This change makes it easier for themes to do interesting  things with window borders.  
Unfortunately, if the wrong approach  spreads, they won't be able to do that.[/B]

---

### Post by The Thunder Chimp on 2010-09-02
> **Cavsfan said:**
> The solution to this is one the first page in the sticky under General Help -

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1469475_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1469475")

And it says this: [B]Using gconf-editor is not the right approach as this could bork  future themes. 
This change makes it easier for themes to do interesting  things with window borders.  
Unfortunately, if the wrong approach  spreads, they won't be able to do that.[/B]

Oh Come on, I'm sure you're able to realize that the only reason that made canonical decide to switch the buttons place is to attract Mac users, because people using Mac have switched platforms in the past, and might as well do it again. Canonical prefers to attract new people faster, and annoy 9 out of 10 people, rather than to let things be.

---

### Post by Cavsfan on 2010-09-03
> **The Thunder Chimp said:**
> Oh Come on, I'm sure you're able to realize that the only reason that made canonical decide to switch the buttons place is to attract Mac users, because people using Mac have switched platforms in the past, and might as well do it again. Canonical prefers to attract new people faster, and annoy 9 out of 10 people, rather than to let things be.

I am just the messenger... 
There have been hundreds of threads opened complaining about the button placement.
And your point has been brought up hundreds of times also...

---

