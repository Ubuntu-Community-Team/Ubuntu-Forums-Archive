---
title: "Ping shows active computer but ssh does not connect"
date: 2010-04-20
forum: General Help
---

### Post by umeboshi80 on 2010-04-20
Hi,

I posted the same problem before but did not get answers, I guess due to the unattractive title. I have two Ubuntu machines, both desktop version with a server installed on top. They are both on the same network. It seems that when I restart the remote computer, I can ssh to it fine for a while but then I get the following:

Read from remote host ...: Connection reset by peer
lost connection

(where ... is the ip address)

When I do ssh -vv it gets to the point where it asks me for the password and then the output is:

debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug1: channel 0: free: client-session, nchannels 1
Read from remote host ... : Connection reset by peer
Connection to ... closed.
Transferred: sent 1280, received 1752 bytes, in 98.9 seconds
Bytes per second: sent 12.9, received 17.7
debug1: Exit status -1

Pinging it shows that the remote computer is active (cannot access it physically).
This has only happened recently. I am at loss of ideas. Thanks for any input.
Hadassa

---

### Post by darolu on 2010-04-20
> Read from remote host ... : Connection reset by peer
That makes me think the problem is in the other end, it closes connection while reading, so I believe it maybe a permissions issue, the directory you're trying to reach is not present or has changed its name or similar.

---

### Post by DrMelon on 2010-04-20
I don't know why you're hiding the IP address, it's most likely a local LAN address like 192.168.0.24 or something.

In any case, it sounds as if the host machine is terminating the connection once it begins, so I would check the settings on the other machine to make sure it isn't doing anything stupid (like denying access to any user or something).

---

### Post by umeboshi80 on 2010-04-20
Wow, thanks for those quick replies. Since I'm kind of a newbie, would you mind telling me what I should be looking for once I will have the time to travel to the remote computer?
How come it used to work perfectly before (I also tried reaching it from a different computer and it did not work)?

Thanks,
Hadassa

---

