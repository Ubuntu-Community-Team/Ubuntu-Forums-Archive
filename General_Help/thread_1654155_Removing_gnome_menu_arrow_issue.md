---
title: "Removing gnome menu arrow issue"
date: 2010-12-27
forum: General Help
---

### Post by KaFive on 2010-12-27
I read this thread: [http://ubuntuforums.org/showthread.php?t=1010435](http://ubuntuforums.org/showthread.php?t=1010435)
And it works perfectly, but it replaces Window List and Notification Area separators with an ugly dotted separator. Any solution for that? 
Thanks.

Here's the code I've used from the thread to remove the arrow:

```
style "panel-arrow-remove"

#the following removes the arrows from the panel
{
engine "pixmap"
    {
    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = ".arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = UP
    }

    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = ".arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = DOWN
    }
    }
}

widget_class "*PanelToplevel*"             style "panel-arrow-remove"
```

---

### Post by hhh on 2010-12-28
koffeejv at the end of the thread you linked says changing to another theme and back fixed it for him.

If that doesn't work, I've removed it in the past using the instructions in the first post here, and can't remember having any ugly separators (I curently use Xfce)...
[http://ubuntuforums.org/showthread.php?t=733808](http://ubuntuforums.org/showthread.php?t=733808)

It takes about 10 minutes to recompile the panel, but his instructions are spot on. Don't forget to delete or comment out your current markup from your .gtkrc file first.

-edit- I last tried that method using Lucid, but it looks like there are instructions for Maverick at the end of the thread.

---

### Post by KaFive on 2010-12-30
Thanks for the answer, I tried that method but it killed my gnome-panel, don't know why...

---

