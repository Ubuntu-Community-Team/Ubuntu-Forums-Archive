---
title: "How to remove these lines in Nautilus?"
date: 2010-08-22
forum: General Help
---

### Post by dxxvi on 2010-08-22
I'm using Ubuntu 10.04.1.

Thank you.

---

### Post by inameiname on 2010-08-23
I believe those aren't a nautilus issue, but an issue with your current theme you are using. I've had great success in removing lines such as those by editing the gtkrc file in your /usr/share/themes folder (or, it might be in your theme's /home/(your username)/.themes folder). It'd be in the gtk2.0 subfolder. My guess is it's in one of the first lines of it. There's usually a bunch of lines with numbers at the top, and one of them should be the culprit. Unfortunately, all gtkrc theme files are different, so not knowing yours I can't be sure where or what.

Personally, I don't have them on mine. My Moomex theme automatically removes them.

---

### Post by Ginsu543 on 2010-08-23
I use the Dyne theme and I don't have them either.

---

### Post by dxxvi on 2010-08-24
> **inameiname said:**
> I believe those aren't a nautilus issue, but an issue with your current theme you are using. I've had great success in removing lines such as those by editing the gtkrc file in your /usr/share/themes folder (or, it might be in your theme's /home/(your username)/.themes folder). It'd be in the gtk2.0 subfolder. My guess is it's in one of the first lines of it. There's usually a bunch of lines with numbers at the top, and one of them should be the culprit. Unfortunately, all gtkrc theme files are different, so not knowing yours I can't be sure where or what.

Personally, I don't have them on mine. My Moomex theme automatically removes them.
If you have experience with it already, could you please take a glance at my gtkrc file (in the attachment; by the way I use Ambiance)? Could you post your gtkrc file?

Thank you.

---

### Post by inameiname on 2010-08-24
Sure, I'll attach it here. Or I tell you what, I'll attach my whole theme instead. In the meantime, I'll look through your gtkrc file, but as how I've tweaked them in the past, I'd need the whole theme so I can plug n' play numbers and then set the theme to see if it fixed/changed anything. That's pretty much all I can do I'm afraid. It is Ambiance, though, so perhaps I'll just look at why it maintains the dark lines as separators, just as your version of Ambiance does.

In the meantime, feel free to check out my theme. I'll just attach it here. It's pretty much the same Moomex as you can get from gnome-look.org, but I've tweaked the gtkrc file a little to my liking. (Boy did that take some time!) Maybe you'll like it better than yours. Alternate solution! Ha. Just remember to change the icon set as mine is set to one I called Windows-Like, which is pretty much Win7 Pack's icon set, also from gnome-look.org.

Also, I just found a cool thread on tweaking gtkrc files. Sweet! Hopefully it'll help us both. So far, I've figured out how to tweak Ambiance to remove the horizontal shading that separates each item in Nautilus, just as it is in my Moomex theme. All I did was copy and paste this line somewhere near the top with the rest: 

      > 
GtkTreeView::odd_row_color = @base_color


So if you want that tweaked, it should work with your theme. Sadly, haven't figured out your issue just yet. Oh, and here is that link:

[http://ubuntuforums.org/showthread.php?t=377397](http://ubuntuforums.org/showthread.php?t=377397)

---

### Post by inameiname on 2010-08-24
I found it. It's this line, line 124:

        listviewstyle       = 2     # 0 = nothing, 1 = dotted 2 = solid

change it to:

        listviewstyle       = 0     # 0 = nothing, 1 = dotted 2 = solid

---

### Post by dxxvi on 2010-08-26
> **inameiname said:**
> I found it. It's this line, line 124:

        listviewstyle       = 2     # 0 = nothing, 1 = dotted 2 = solid

change it to:

        listviewstyle       = 0     # 0 = nothing, 1 = dotted 2 = solid

Thanks a lot. It works.

---

### Post by inameiname on 2010-08-26
Sure. 

Oh, and don't forget to mark this thread as solved so others may benefit.

---

