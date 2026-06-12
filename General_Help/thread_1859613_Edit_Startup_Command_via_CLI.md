---
title: "Edit Startup Command via CLI ?"
date: 2011-10-14
forum: General Help
---

### Post by Jose Catre-Vandis on 2011-10-14
Hi

I have entered a command into the Autostart section of Startup and Session which has several parameters for the program.

This machine is a standalone PC which I can access via ssh.

Is there a way I can edit the parameters of the command via ssh? I have searched through the hidden directories in ~/home and in /etc but cannot find the files that hold this information.

Yes, as the machine is running X I can VNC, but as the machine's primary function is to display a public slideshow I would prefer to do things in the background.

Thanks

---

### Post by sisco311 on 2011-10-14
Yes, you can edit the application's .desktop file in ~/.config/autostart/ or /etc/xdg/autostart/

For details, check out the freedesktop specs:
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

---

### Post by Jose Catre-Vandis on 2011-10-14
Aha - yes I see it now - thanks sisco

and I see I can find panel launchers in **~/.config/xfce4/panel** and **/usr/share/applications** too. :)

---

