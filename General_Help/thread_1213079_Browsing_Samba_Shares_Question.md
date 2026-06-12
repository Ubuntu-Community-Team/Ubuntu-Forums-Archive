---
title: "Browsing Samba Shares Question"
date: 2009-07-14
forum: General Help
---

### Post by eyeprotocol on 2009-07-14
Hello. I have a home network consisting of my Ubuntu machine (Jaunty, freshly installed), a Debian 4 machine (running Samba among other things), a Windows XP machine (with one folder shared).

By going through Places ---> Network, i eventually see the workgroup (of the Debian and Windows machine), then i see the two icons representing the Debia and Windows machines.

If i open the icon representing the Windows machine, i am confronted with a credentials-submitting window and everything is ok from then on.

If i open the icon representing the Debian machine, nothing happens for a while. After a few seconds i am getting a window saying that " Unable to mount location. Failed to retrieve share list from server". And it ends there.

Now, my first thought would be that something is seriously wrong with smb.conf at the Debian machine. However, this can not be the case, since i can browse samba shares on the Debian, using the XP machine, even a portable Mac that was here yesterday. Only Ubuntu has trouble browsing these samba shares.

Please assist

Panos

P.S. I forgot to mention that this is a wired (not wireless) network, and all machine have static ips and can ping to each other without errors.

---

