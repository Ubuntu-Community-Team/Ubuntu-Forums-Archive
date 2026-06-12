---
title: "Gnome-Do problem"
date: 2011-11-28
forum: General Help
---

### Post by grimslider75 on 2011-11-28
I'm using Xubuntu (Xfce), and I have gnome-do installed. It used to work before I upgraded from 11.04 to 11.10. Now, it immediately closes after I attempt to open it. 

here is the output in terminal:

```
kurt@kurtstechnologicaldevice:~$ gnome-do

(Do:13461): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

[Error 16:38:09.158] [AbstractKeyBindingService] Failed to bind "Summon in Text Mode" to ""

Unhandled Exception: System.Exception: Message body length mismatch: 16128 of expected 42851
at NDesk.DBus.Connection.ReadMessage () <0x00703>
at NDesk.DBus.Connection.Iterate () <0x0001b>
at NDesk.DBus.BusG/<Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x00033>
at (wrapper native-to-managed) NDesk.DBus.BusG/<Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x0005b>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00003>
at Gtk.Application.Run () <0x0000b>
at Do.Do.Main (string[]) <0x001f3>

[ERROR] FATAL UNHANDLED EXCEPTION: System.Exception: Message body length mismatch: 16128 of expected 42851
at NDesk.DBus.Connection.ReadMessage () <0x00703>
at NDesk.DBus.Connection.Iterate () <0x0001b>
at NDesk.DBus.BusG/<Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x00033>
at (wrapper native-to-managed) NDesk.DBus.BusG/<Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x0005b>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00003>
at Gtk.Application.Run () <0x0000b>
at Do.Do.Main (string[]) <0x001f3>

```


What seems to be the problem?:confused::confused::confused:

---

### Post by holycow131415 on 2011-11-28
I went to there website, and it appears there hasnt been an official stable update for 2.5 years.

There is a daily ppa for it though: [https://launchpad.net/~do-testers/+archive/ppa](https://launchpad.net/~do-testers/+archive/ppa)

I see v 0.8.5 for oneric and it was updated 11/5/11

---

### Post by Bonster on 2011-11-28
Try Kupfer

Gnome-do is outdated

---

### Post by papibe on 2011-11-28
> **Bonster said:**
> Try Kupfer

Gnome-do is outdated

+1

Also you can try Synapse.

In my experience, Synapse is very fast and responsive, but with less functionality than Kupfer. Kupfer has great features and add ons, however it is a little more laggy.

Regards.

---

### Post by grimslider75 on 2011-11-28
> **papibe said:**
> +1

Also you can try Synapse.

In my experience, Synapse is very fast and responsive, but with less functionality than Kupfer. Kupfer has great features and add ons, however it is a little more laggy.

Regards.


Wow, great suggestions guys! Thanks a bunch, I've become so dependent on gnome-do that without something like it I feel like my computer is less functional. Thanks again!

:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by batharoy on 2011-11-28
> **papibe said:**
> +1

Also you can try Synapse.

In my experience, Synapse is very fast and responsive, but with less functionality than Kupfer. Kupfer has great features and add ons, however it is a little more laggy.

Regards.

Thanks for this.

---

