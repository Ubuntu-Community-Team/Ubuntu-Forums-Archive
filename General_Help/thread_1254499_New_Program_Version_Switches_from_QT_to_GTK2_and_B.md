---
title: "New Program Version Switches from QT to GTK2 and Breaks!"
date: 2009-08-31
forum: General Help
---

### Post by LaneLester on 2009-08-31
With my outdoor weather station I use a program, [WeatherDisplay]("http://www.weather-display.com"), to display station outputs on my monitor.

The previous version was written with the QT widget set and runs fine in Ubuntu Jaunty. The new version of Weather Display uses the GTK2 widget set and is broken. I hope you can help me get it running.

When I run the program from the terminal, I get this:
```
Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
[WARNING] Out of OEM specific VK codes, changing to unassigned
[WARNING] Out of unassigned VK codes, assigning $FF

Gtk-CRITICAL **: file gtkstyle.c: line 341 (gtk_style_copy): assertion `style != NULL' failed.
[HINT] TWinControl.CreateWnd creating Handle during loading MainForm:TMainForm csDesigning=False

Gtk-CRITICAL **: file gtkstyle.c: line 341 (gtk_style_copy): assertion `style != NULL' failed.

[many instances of the above line deleted]

[HINT] TWinControl.CreateWnd creating Handle during loading Formtempdials:TFormtempdials csDesigning=False

WARNING: [TGtkWidgetSet.CreateFontIndirectEx] NOT found XLFD: <> Fontname=""
[HINT] TWinControl.CreateWnd creating Handle during loading weatherdials:Tweatherdials csDesigning=False
[HINT] TWinControl.CreateWnd creating Handle during loading graphform:Tgraphform csDesigning=False
WARNING: [TGtkWidgetSet.CreateFontIndirectEx] NOT found XLFD: <> Fontname=""
WARNING: [TGtkWidgetSet.CreateFontIndirectEx] NOT found XLFD: <> Fontname=""
WARNING: [TGtkWidgetSet.CreateFontIndirectEx] NOT found XLFD: <> Fontname=""
WARNING: [TGtkWidgetSet.CreateFontIndirectEx] NOT found XLFD: <> Fontname=""
WARNING: [TGtkWidgetSet.CreateFontIndirectEx] NOT found XLFD: <> Fontname=""
WARNING: [TGtkWidgetSet.CreateFontIndirectEx] NOT found XLFD: <> Fontname=""
WARNING: [TGtkWidgetSet.CreateFontIndirectEx] NOT found XLFD: <> Fontname=""
[HINT] TWinControl.CreateWnd creating Handle during loading Formpercentdir:TFormpercentdir csDesigning=False
./WeatherD: symbol lookup error: ./WeatherD: undefined symbol: moonage
```

After executing:
export LD_LIBRARY_PATH="/usr/lib/gtk-2.0/modules/$LD_LIBRARY_PATH"
I get this:
```
GLib-CRITICAL **: file gmessages.c: line 293 (g_log_remove_handler): assertion `handler_id > 0' failed.
[FORMS.PP] ExceptionOccurred 
  Sender=EAccessViolation
  Exception=Access violation
  Stack trace:
  $B76F494C
  $B7B8463E
  $B7B84674
  $08AC1A6A  TGTKWIDGETSET__PASSCMDLINEOPTIONS,  line 293 of gtkwidgetset.inc
  $08AC192B  TGTKWIDGETSET__CREATE,  line 213 of gtkwidgetset.inc
  $0808D3AC  CREATEWIDGETSET,  line 1590 of forms.pp
  $0808CB1D  INTERFACES_init,  of gtk1int.pp
  $08C662C4
TApplication.HandleException Access violation
  Stack trace:
  $B76F494C
  $B7B8463E
  $B7B84674
  $08AC1A6A  TGTKWIDGETSET__PASSCMDLINEOPTIONS,  line 293 of gtkwidgetset.inc
  $08AC192B  TGTKWIDGETSET__CREATE,  line 213 of gtkwidgetset.inc
  $0808D3AC  CREATEWIDGETSET,  line 1590 of forms.pp
  $0808CB1D  INTERFACES_init,  of gtk1int.pp
  $08C662C4
[FORMS.PP] ExceptionOccurred
``` 

It seems I need to do something to load libcanberra-gtk-module.so at boot time. I've added the command to .bashrc, so hopefully that will take care of it.

Do you have an idea how I can avoid the above errors that occur when libcanberra-gtk-module.so is loaded?

Lane

---

