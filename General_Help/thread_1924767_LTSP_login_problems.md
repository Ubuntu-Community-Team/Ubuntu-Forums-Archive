---
title: "LTSP login problems"
date: 2012-02-13
forum: General Help
---

### Post by cisco101 on 2012-02-13
History:

I have setup an Ubuntu server with 5 thin clients using ltsp and nbd. 3 out of 5 workstations boots up fine and log's in.

2, however gives me trouble. As far as I can tell they are identical machines.

On the client side I get an invalid user ID.  

On the server I see the following in the Auth. logs

________________________________________________________________
Feb 13 13:39:27 media-centre gnome-keyring-daemon[7278]: dbus failure unregistering from session: Connection is closed

Feb 13 13:39:27 media-centre sshd[7108]: pam_unix(sshd:session): session closed for user user001

Feb 13 13:39:27 media-centre gnome-keyring-daemon[7278]: dbus failure unregistering from session: Connection is closed

Feb 13 13:39:27 media-centre polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session26 (system bus name :1.279, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_ZA.UTF-8) (disconnected from bus)
____________________________________________________________________

Can this be a hardware problem?

I have done MB, CPU and RAM tests with Hiren Boot CD, with no reported errors.

Any advice?

Tnx

---

