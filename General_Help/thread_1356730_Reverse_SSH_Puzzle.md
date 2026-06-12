---
title: "Reverse SSH Puzzle"
date: 2009-12-16
forum: General Help
---

### Post by wgcampbell on 2009-12-16
I have a reverse SSH tunnel initiated from a remote machine to a server machine.  I'm using mobile broadband service for the remote location (why I need the reverse tunnel).

I'm using autossh to initiate the reverse connection and keep it alive.  Everything works fine most of the time.  However, every night at midnight, the mobile broadband service drops the connection and the dialer must re-establish the connection.  At this point (on the server machine), I receive the following error:

```
Dec 16 00:10:17 server sshd[26922]: error: bind: Address already in use
Dec 16 00:10:17 server sshd[26922]: error: channel_setup_fwd_listener: cannot listen to port: XXXX
```

I have researched this problem and found several posted suggestions to change the sshd_config option to "X11UseLocalhost yes" (that is suppose to add additional timing so that the server properly drops the existing port listening).  That doesn't help.

I'm not sure it's a timing issue - the remote machine is waiting 10 minutes before trying to reconnect.  Also, if I (purposely) drop the ssh connection on the server side, it reconnects just fine.  (Not sure how to manually drop the connection on the client side - if I kill the ssh process, it kills the autossh process.)

I think the key here is that the logs on the server machine don't show that the ssh connection has been dropped prior to the client machine trying to re-connect at 10 minutes after midnight. But I'm not sure how to solve this?

---

### Post by wgcampbell on 2009-12-18
Not sure this is a total solution, but things are working now by adding:

ExitOnForwardFailure yes

...to the ssh_config file, or as an ssh command option.

---

