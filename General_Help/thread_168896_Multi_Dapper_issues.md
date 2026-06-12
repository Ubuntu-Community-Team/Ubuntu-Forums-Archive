---
title: "Multi Dapper issues"
date: 2006-05-01
forum: General Help
---

### Post by ubuntubrian on 2006-05-01
Dapper is great and I have Ubuntu with Kubuntu and Xubuntu desktops also. I prefer to use XFCE but:
I have no window management capabilities and get an error message that I "cannot use these settings with my window manager (unknown)".
I have no multiple desktops in KDE or XFCE
My sound in Gnome is reversed (lower setting increases volume)
I can't print from anything even though I can choose my printer. The CUPS management page shows all my printers but the one here at home (CanonS750) is shown as "rejecting jobs" and I can't change the setting to accept. I get an error message-unknown.
I'm on a powerbook.

---

### Post by Drag0n on 2006-05-18
Yup, I'm having the same problems with the window manager. I can start xfwm4 manually and the borders appear, but the system control manager doesn't detect it running. Any ideas? Also there's no taskbar, only a panel at the top that has nothing on it. (My mate was trying to show me how great it is!!)

---

### Post by dejitarob on 2006-05-18
[QUOTE=ubuntubrian]My sound in Gnome is reversed (lower setting increases volume)... I'm on a powerbook.[/QUOTE]I have the same issue on an Asus Z70V laptop. When I lower the volume in Gnome's Volume Control it actual gets louder and vice-versa. I have an "Azalia" Realtek ALC880 sound card using the hda_intel driver. This did not happen in Breezy or Kubuntu Dapper.

---

### Post by ubuntubrian on 2006-05-29
I created another user and when I log in to XFCE with that name everything is great. There is some file in my home directory that is creating the problem. I thought it wa a gtk issue but was not as I renamed all the gtk files and the problem persists. I no longer have the volume control issue after updating to the release candidate version.

---

### Post by frying_fish on 2006-05-29
it might be an idea to delete ~/.gnome ~/.kde and such, (the ones that control your settings for each environment) then try loading either one again, ok you will have lost your settings, but if it makes everything work then you can just go about setting them up again without any issues.

---

### Post by ubuntubrian on 2006-05-30
I may do that, thanks.

---

### Post by dejitarob on 2006-05-30
There is a [bug]("https://launchpad.net/distros/ubuntu/+source/gnome-media/+bug/41999") in the package gtk2-engines-gtk-qt that inverts the Gnome volume control. Removing ~/.gtkrc-2.0 and restarting X solved the issue for me.

---

