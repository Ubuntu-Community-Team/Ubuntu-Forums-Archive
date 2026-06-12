---
title: "nm-applet control doesn't transition upon switch user"
date: 2009-10-29
forum: General Help
---

### Post by marawuti on 2009-10-29
Just discovered in Jaunty on my laptop that the first user to bring up the machine retains the nm-applet GUI icon and thus control of the settings.

After I switch user I get the following:
   502 > nm-applet --help

   ** (nm-applet:4779): WARNING **: <WARN> applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

I surmise that the NetworkManagerUserSettings service should be amenable being disconnected from the first user and reconnected by the current Gnome desktop user.

If this is possible now I'd love to hear how to set up the policy or configuration to allow this.
Else, I'd like to see this as a new feature.

---

