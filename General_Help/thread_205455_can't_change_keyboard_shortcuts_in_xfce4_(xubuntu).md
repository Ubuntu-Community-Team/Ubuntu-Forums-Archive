---
title: "can't change keyboard shortcuts in xfce4 (xubuntu)"
date: 2006-06-28
forum: General Help
---

### Post by redcharlie on 2006-06-28
I'm trying to use alt-space instead of alt-tab to cycle windows for ease of use with vnc

I've got two keythemerc files
~/.themes/vnc/xfwm4/keythemerc
/usr/share/themes/Default/xfwm4/keythemerc

I've edited both to have the line
"cycle_windows_key=Alt+space"

and tried to switch using the settings manager->window manager->keyboard
(I see my both my themes, and can even edit the vnc theme)
also logging out and back in, and rebooting

nothing has an effect.  xfwm still uses alt-tab to cycle windows, conflicting with the host window in vnc

I've seen another posting with this problem
[http://www.ubuntuforums.org/showthread.php?t=177734&highlight=keythemerc](http://www.ubuntuforums.org/showthread.php?t=177734&highlight=keythemerc)
but the thread is closed :(

This has worked for me for xfce4 on Fedora...don't know what's wrong now...

---

### Post by redcharlie on 2006-06-28
additional info:
when I use Settings->Window Manager Settings->Keyboard 
and edit the cycle_windows_key
after I close the window and examine ~/.themes/vnc/xfwm4/keythemerc
I find that the cycle_windows_key entry has been mangled into
> (null)=Alt+space

---

### Post by redcharlie on 2006-06-28
Well, this is a (ahem) "feature" of xfce4.4 Beta 1, evidently:
[http://foo-projects.org/pipermail/xfce/2006-May/017518.html](http://foo-projects.org/pipermail/xfce/2006-May/017518.html)

Oliver Fourdan says it's been put back in.
[http://bugzilla.xfce.org/show_bug.cgi?id=1964](http://bugzilla.xfce.org/show_bug.cgi?id=1964)

Anyone have any idea when we'll have another supported release?

---

### Post by redcharlie on 2007-07-17
AHA!  FINALLY!!  I can change it in Feisty!!!
Settings->Window Manager->Keyboard tab
added a profile named "vnc" and dbl clicked on "Cycle window action" and changed it to "ctl-alt-space"

It works!!

---

