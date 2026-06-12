---
title: "Remote access"
date: 2012-06-26
forum: General Help
---

### Post by 5t3ph on 2012-06-26
HI, I'm a newbie at use ubuntu.
I have installed it and it's working fine.. however I would like to book up my pc and start a remote connection automatically without viewing the ubuntu desktop? I have create a remote connection and it works fine.
Can someone help me out please?
Thanks you!:confused:

---

### Post by TheFu on 2012-06-26
> **5t3ph said:**
>  I would like to book up my pc and start a remote connection automatically without viewing the ubuntu desktop?

Can you please be more specific about the remote connection type?

[LIST]
[*]Is this a VPN? If so, what type of VPN (pptp, ipsec, openvpn, other)?
[*]Is this an ssh tunnel?
[*]Is this a GUI desktop? If so, which protocol is used? RDP, VNC, NX, something else?
[*]Is a hardware token used for authentication?
[/LIST]
*"book up my pc*" is confusing to me.Could you please clarify?

Almost anything can be scripted under Linux, but there are difficulties is making some other program have complete control instead of the desktop. OTOH, launching a program at login is pretty easy when you don't need to worry about remote logins to the machine you are using. Just add the command to the end of the ~/.login file (assuming a Borne shell compatible shell is used).

---

