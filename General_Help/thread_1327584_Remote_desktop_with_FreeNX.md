---
title: "Remote desktop with FreeNX?"
date: 2009-11-15
forum: General Help
---

### Post by Lucky75 on 2009-11-15
Hey,

so I installed the freenx server on 9.10, since I wanted something a little more secure than VNC. I can log in fine. However, I can't seem to log in to the CURRENT session or see my currently open windows. It seems to create a new gnome session instead.

Any ideas on how to view the current one sitting at :0 ?

Thanks!

---

### Post by Lucky75 on 2009-11-16
up

---

### Post by sefs on 2009-11-16
If the server works like nxserver from [http://nomachine.com](http://nomachine.com)  run over to that website and get there administrator doc and see what you can make happen.

---

### Post by Lucky75 on 2009-11-16
I've looked there, it is indeed similar, but a little different. In my /etc/nxserver I see the following which I think has to do with it, but I still can't get it to work.

```

ENABLE_DESKTOP_SHARING=1

#
# General shadowing / mirroring notes:
#
# By default shadowing is only allowed for the same user.
#
# If nxserver finds nxshadowacl binary, it asks it, for which users
# the permission is granted.
#
# nxshadowacl <user>
#
# Exit code:
#
# 0 -> Save cookie in session file for other users
# 1 -> Do not save cookie
#
# Check if user is allowed to be shadowed by admin user.
#
# nxshadowacl <user> <admin>
#
# Exit code:
#
# 0 -> Yes, allow shadowing and add to list
# 1 -> No, don't allow shadowing
#

#
# When using NX 3.0 shadowing, this enables asking the user whether
# he authorizes another user to shadow his session
#
# 0: No authorization request will be presented,
#    and the session will be shadowed as if the user had approved.
# 1: (default) Ask for authorization
#
ENABLE_SESSION_SHADOWING_AUTHORIZATION=0

# Allow session shadowing in interactive mode:
#
# 1: The shadowing user can interact with the shadowed session.
#
# 0: The shadowed session is view-only. No interaction with the
#    shadowed session is possible.
#
ENABLE_INTERACTIVE_SESSION_SHADOWING=1


```

---

### Post by Lucky75 on 2009-11-16
actually, i uninstalled  freenx and installed the nomachine one, but I still can't seem to get it to log in to my current session. Anyone have any experience with this?

---

### Post by walkerstreet on 2009-11-16
Hi,
I've been trying to connect to the 'real' or 'live' screen with freenx (using 32 bit karmic machines at both ends.  I read this is called shadowing. However I can't get it to work.  They connect, but the session terminates (disappears) before the screen even appears at the client end.  Using freenx in its usual mode (you connect to a separate X session) works fine.

I use the same username at both ends so shadowing should work with no alteration to config files.  If you have  a different username the following is supposed to work:

In **/etc/nxserver/node.conf** (server side), change/add the following:
**ENABLE_SESSION_SHADOWING_AUTHORIZATION=0**

In **/etc/nxserver/nxshadowacl** (server side), change/add the following:
**exit 0**

Either way, I can't get shadowing to work.  Anyone worked it out?

Walker

---

### Post by Lucky75 on 2009-11-16
Mine doesn't disconnect, it just always creates a new session. I'm using nomachine now. I just want to connect to my currently running session like a standard RD.

```


#
# Allow session shadowing on this server:
#
# 1: Enabled.  Each user can require to attach to an already running
#    session. The session owner has to accept connection.
#
# 0: Disabled. Session shadowing is forbidden.
#
EnableSessionShadowing = "1"

#
# Allow session shadowing in interactive mode:
#
# 1: Enabled. User attaching to the session can interact with
#    the session.
#
# 0: Disabled. The session is shadowed in view-only mode. User
#    attaching to the session can't interact with the session.
#
EnableInteractiveSessionShadowing = "1"

#
# Enable or disable NX server requiring authorization to the owner
# of the NX session before sharing the session.
#
# 1: Enabled. NX server asks for authorization to the owner
#    of the master session before trying to share the session.
#
# 0: Disabled. NX server tries to share the NX session without
#    the need of any authorization from the owner of the master
#    desktop.
#
EnableSessionShadowingAuthorization = "0"

#
# Allow desktop sharing on this server:
#
# 1: Enabled. User can require to attach to the native display
#    of the nodes. The desktop's owner has to accept connection.
#
# 0: Disabled. Desktop sharing is forbidden.
#
EnableDesktopSharing = "1"

#
# Allow desktop sharing in interactive mode:
#
# 1: Enabled. User attaching to the desktop can interact with
#    the session.
#
# 0: Disabled. The session is shadowed in view-only mode. User
#    attaching to the desktop can't interact with the session.
#
EnableInteractiveDesktopSharing = "1"

#
# Allow the NX user to connect to a desktop owned by a user who is
# not an NX user:
#
# 1: Enabled. Allow an NX user to connect to a desktop owned
#    by a user who is not an NX user. This requires running a
#    privileged script as root and will work only if the node
#    is the same machine where NX server is running.
#
# 0: Disabled. An NX user can connect only to a desktop owned
#    by an NX user when EnableDesktopSharing is enabled.
#
EnableFullDesktopSharing = "0"

#
# Allow the NX user to connect to a desktop owned by root:
#
# 1: Enabled. Allow an NX user to connect to a desktop owned by
#    root (or Administrator on a Windows machine). This requires
#    EnableFullDesktopSharing to be enabled.
#
# 0: Disabled. A NX user is forbidden to connect to a desktop
#    owned by root.
#
#EnableAdministratorDesktopSharing = "0"

#
# Enable or disable NX server requiring authorization to the owner
# of the desktop before sharing the session.
#
# 1: Enabled. NX server asks for authorization to the owner
#    of the desktop.
#
# 0: Disabled. NX server tries to share the native display
#    without the need of any authorization from the owner
#    of the desktop.
#
EnableDesktopSharingAuthorization = "0"

#
# Enable or disable NX server requiring authorization before sharing
# the session either when the X server is running as root or gdm.
#
# 1: Enabled. NX server needs authorization to proceed with
#    sharing the session.
#
# 0: Disabled. NX server tries to share the native display
#    without the need for any authorization. Sharing the
#    session is also possible when a user is not logged
#    on to the local desktop.
#
#EnableSystemDesktopSharingAuthorization = "1"


```

Edit: Ugh, so I managed to log into the current session running on :0 by turning on the System/Administrator sharing. Unfortunately, I'm running into two problems:

1) While I can interact with my desktop and move windows around/click/etc, I cannot SEE those changes on the client. It doesn't want to seem to redraw.
2) I have multiple monitors on the server, and whenever I connect everything seems to be compressed into one screen instead of adding a scrollbar or something or zooming. I can't see a thing.

Anyone have any suggestions? Thanks!!

---

### Post by Lucky75 on 2009-11-17
up

---

### Post by Lucky75 on 2009-11-19
up

---

### Post by juancarlospaco on 2009-11-19
You dont need NX, use SSH, it can safely tunnel X or VNC.

---

### Post by XCan on 2009-11-20
VNC is broken by default and won't update the screen unless visual effects are turned off. ssh -X won't give the current running session.

---

### Post by Lucky75 on 2009-12-05
NX is faster than VNC.

---

### Post by imtheguru on 2009-12-10
> **Lucky75 said:**
> Edit: Ugh, so I managed to log into the current session running on :0 by turning on the System/Administrator sharing. Unfortunately, I'm running into two problems:

1) While I can interact with my desktop and move windows around/click/etc, I cannot SEE those changes on the client. It doesn't want to seem to redraw.
2) I have multiple monitors on the server, and whenever I connect everything seems to be compressed into one screen instead of adding a scrollbar or something or zooming. I can't see a thing.

Anyone have any suggestions? Thanks!!You're almost there.

1. Turn off compiz on the host.
2. Set a screen size in the client session.

Cheers.

---

### Post by imtheguru on 2009-12-10
> **Lucky75 said:**
> NX is faster than VNC.Yes and no.

New X sessions (Gnome, KDE) are almost native speed.
Shadowing isn't much faster than VNC, but may be required for some scenarios.

Your mileage may vary,
Cheers.

---

### Post by btbluesky on 2009-12-25
Same thing here, cannot conn to live session. Other session is fine. BUT one trick I found is that, combine NX with a x11vnc (start a x11vnc on display:0, then using native NX session, open that vnc), is actually faster than just using vnc. And I'm on wireless LAN w/ 3840x1200, the speed diff is very noticeable, like double.
Anyway, until I can find something else, this'd be good.

---

