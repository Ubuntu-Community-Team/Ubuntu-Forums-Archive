---
title: "Gimp theme help"
date: 2009-10-04
forum: General Help
---

### Post by Aj1t1 on 2009-10-04
Hello people :)

My name is Jacob and I'm trying to get a simple theme for Gimp that simply fits the colors that I want.  I don't need any complicated coding or anything, just a color change... I am hoping that is nothing to you guys, and maybe you could help me out.

Here is the default code gtk theme for Gimp:

```
# pixmap_path "<dir 1>:<dir 2>:<dir 3>:..."
#
# include "rc-file"
#
# style <name> [= <name>]
# {
#   <option>
# }
#
# widget <widget_set> style <style_name>
# widget_class <widget_class_set> style <style_name>


# Don't define icons for the Default theme as they are compiled in
#
# include "imagerc"

# Do override some GTK stock icons however.

style "gimp-default-style"
{
  stock["gtk-dialog-error"] =
    {
      { "images/stock-error-64.png", *, *, "gtk-dialog" }
    }
  stock["gtk-dialog-info"] =
    {
      { "images/stock-info-64.png", *, *, "gtk-dialog" }
    }
  stock["gtk-dialog-question"] =
    {
      { "images/stock-question-64.png", *, *, "gtk-dialog" }
    }
  stock["gtk-dialog-warning"] =
    {
      { "images/stock-warning-64.png", *, *, "gtk-dialog" }
    }

  GtkPaned::handle-size             = 6
  GimpDock::default-height          = 300
  GimpDock::font-scale              = 0.8333
  GimpDockSeparator::height         = 6
  GimpMenuDock::minimal-width       = 200
  GimpMenuDock::menu-preview-size   = button
  GimpToolbox::tool-icon-size       = button
  GimpToolbox::button-relief        = none
  GimpDockbook::tab-border          = 0
  GimpDockbook::tab-icon-size       = button
  GimpColorNotebook::tab-border     = 0
  GimpColorNotebook::tab-icon-size  = button
  GimpDockable::content-border      = 2
  GimpEditor::content-spacing       = 2
  GimpEditor::button-spacing        = 2
  GimpEditor::button-icon-size      = menu
  GimpDataEditor::minimal-height    = 96
  GtkDialog::content-area-border    = 0
  GtkDialog::button-spacing         = 6
  GtkDialog::action-area-border     = 12
  GimpUnitComboBox::appears-as-list = 0
}

class "GtkWidget" style "gimp-default-style"


style "gimp-tool-dialog-style" = "gimp-default-style"
{
  GtkDialog::action-area-border = 6
}

class "GimpToolDialog" style "gimp-tool-dialog-style"


style "gimp-grid-view-style" = "gimp-default-style"
{
  bg[NORMAL] = { 1.0, 1.0, 1.0 }
}

widget "*GimpContainerGridView*GtkViewport*" style "gimp-grid-view-style"


style "gimp-dockable-style" = "gimp-default-style"
{
  GimpFrame::label-bold       = 0
  GimpFrame::label-spacing    = 2
  GtkButton::focus-line_width = 1
  GtkButton::focus-padding    = 0
}

widget "*GimpDockable.*" style "gimp-dockable-style"


style "gimp-display-style" = "gimp-default-style"
{
  GimpRuler::font-scale          = 0.8333
  GimpUnitComboBox::label-scale  = 0.8333
  GimpScaleComboBox::label-scale = 0.8333
  GtkComboBox::arrow-size        = 8
  GtkButton::inner-border        = { 0, 0, 0, 0 }
  GtkButton::focus-line_width    = 0
  GtkButton::focus-padding       = 0
}

widget "*GimpDisplayShell.*" style "gimp-display-style"
```Now I didn't see any area to simply change the color of like the background or something, but I was hoping that perhaps someone here could help me out.

This is just something I whipped up quickly just to give you an idea:

[http://i222.photobucket.com/albums/dd13/Aj1t1/sampletheme.png](http://i222.photobucket.com/albums/dd13/Aj1t1/sampletheme.png)

_________

So can someone help me out?  I just want to add something other than that boring gray.  The colors I want to incorporate are

bright yellow #fffbbf
yellow #fffe7f
golden yellow #ffe17f
green #77b819
light green #92c647

Maybe the yellow for background stuff and green for text?

__________

I conclude by saying, I'm horrible at this stuff, have no idea about coding, and so if what I am asking is unrealistic or impossible, only laugh a little :P

---

### Post by Aj1t1 on 2009-10-04
Could anyone please help me out?

---

### Post by VCoolio on 2009-10-04
no idea, isn't it defined by your gtk-theme? Try to find a theme that suits your needs and then launch gimp using that theme (while the rest of your apps uses the theme you've set in appearance):

GTK2_RC_FILES=$HOME/.themes/[yourtheme]/gtk-2.0/gtkrc gimp

---

### Post by StuartN on 2009-10-04
You can find a theme here [http://art.gnome.org/themes/gtk2](http://art.gnome.org/themes/gtk2) and rewrite it, then place it in ~/.gimp-2.6/themes

The two supplied themes in Gimp do not over-ride any default colours, so they are not helpful examples to start with.

---

### Post by fragos on 2009-10-04
If I'm not mistaken Gimp gets at least some of it's colors from the Gnome system theme. Changes to it are made through System-> Preferences-> Appearance.

---

### Post by Aj1t1 on 2009-10-05
Thank you guys for the response, but I'm currently on Windows (don't bite! I love open source, got a linux box but not currently using it)

Does anyone have any idea how to briefly change the colors of a/the theme?  I can't even look at the gtkrc file on Windows, so I can't edit it here...

---

### Post by StuartN on 2009-10-06
> **Aj1t1 said:**
> I can't even look at the gtkrc file on Windows, so I can't edit it here...

Just download any theme with some colour from the link given earlier. You will need a tar utility to unpack it, then place it wherever you place your existing themes.

---

