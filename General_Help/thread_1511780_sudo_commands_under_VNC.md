---
title: "sudo commands under VNC"
date: 2010-06-17
forum: General Help
---

### Post by lipinski on 2010-06-17
I'm running a VNC Server which I access via an RDP client over an SSH tunnel.  Everything works as expected with my standard login - use of programs and such in the VNC.

Except, when I try to run anything as a different user.  If I try to run any "Window-ed" program as a different user (su <user>; or sudo), I get the same error:
No protocol displayed
cannot open display: :1.0

I could understand if <user> doesn't have permission to open windows on the display, but the sudo seems strange - I would think root should have permission to open windows.

The one thing different with my setup is that the user I'm logged in as doesn't have sudo access directly, so I have to su to a different user, than run sudo.

So, I do this:
Logged in as user1.
su <user2>
sudo <command>

(user1 does not have any admin capabilities, user2 does - hence I need to su to user2 to be able to sudo).

Using the above example, I get the cannot open display error for any command executed as user2 or sudo via user2.  The vncserver was (and needs to be) started by user1.

Any ideas?

---

