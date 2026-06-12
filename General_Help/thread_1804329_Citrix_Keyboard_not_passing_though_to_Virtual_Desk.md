---
title: "Citrix: Keyboard not passing though to Virtual Desktop"
date: 2011-07-14
forum: General Help
---

### Post by bewarellamas on 2011-07-14
This is kind of a crazy question, but I'm hoping someone may have some insight on this. I'll repost what my coworker posted on the Citrix forums about this issue. I'm hoping someone out there can point us in the right direction. Thanks.

> I'm having a weird problem with keyboard passing through from a ubuntu 10.04 client to an XP virtual desktop. The problem is not consistent, but it has happend to multiple users, on different PCs, but the ones it's happening on are using the flavor of linux above. I have not had the report from any users that are using windows based systems to connect to their virtual desktops. The host machines are using firefox 3.6.18, and citrix receiver for linux version 11.0.

Here is the process:

1. The user navigates to the URL and logs in with their network username/password. The keyboard is working at this point.
2. Once the desktop comes up the mouse is still working, but the keyboard no longer is (usb keyboard)
3. The call support and we connect with desktop director. Once desktop director connects the keyboard starts working again.

Any ideas?

We have HP Linux based thin clients and they have never had any problems... The linux boxes it's happening on are repourposed PCs that used to run windows OS.
> I have some additional information. In the Virtual Desktop in event viewer got these two errors:

Event ID 266: The Citrix USB Service failed to establish communication channel with client plug-in
Event ID 267: The Citrix USB Service Handshake failed with client plug-in

Again the clients are repourposed desktops running Ubuntu with Citrix Receiver for Linux version: 11.100.158406.

---

