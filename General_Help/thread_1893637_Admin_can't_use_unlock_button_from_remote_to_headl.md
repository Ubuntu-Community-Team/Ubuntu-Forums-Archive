---
title: "Admin can't use unlock button from remote to headless 10.04?"
date: 2011-12-10
forum: General Help
---

### Post by brec on 2011-12-10
Overview:  When directly logged in to a 10.04 system, as an administrator I can open, for example,  System::Administration::Login Screen, click the Unlock button, and make changes.  But when no one is logged in to the system and I am accessing it remotely via its XRDP server, the Unlock button is unresponsive.  (I can still sudo, or satisfy any GUI password requests, by entering my password.)  I'd like to (a) understand what's happening, and (b) "fix" this so that my remote access is more like direct access.

Details:  10.04 is running on a MacBook Pro via Parallels virtualization pending completion of the hardware system that is intended to be the 10.04 system's real home.  (Virtually) remote access is via the CoRD RDP client on the Mac.  To simulate a headless system I leave the 10.04 system at its (Gnome) login screen, so no one is logged into it.  Its XRDP server uses vncserver for session administration, and I have estabished a vncserver password which I provide when establishing the remote connection.  The remote shows me the same desktop as a direct connection with all my customizations, bash shows me my username in the prompt, etc.; this "Unlock button" issue is the only difference I have seen thus far between direct and remote access.

As a *nix/Ubuntu newbie my suspicion is that with remote access I'm not logged in as "fully" as I would be with direct access; if that's true, how can I be a full-fledged logged-in user when accessing remotely?

---

