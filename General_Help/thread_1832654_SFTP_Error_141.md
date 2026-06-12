---
title: "SFTP Error 141 ?"
date: 2011-08-25
forum: General Help
---

### Post by TuxLyn on 2011-08-25
Can some one help me with this SFTP error ?

```
Error:    Connection closed by server with exitcode 141
Error:    Could not connect to server
```

This is what I have found on google, but I don't know what this means lol
[I]
System error code 141 means "The system tried to SUBST a drive to a directory on a joined drive." This error code may also display as "ERROR_SUBST_TO_JOIN" or as the value 0x8D.[/I]

My Config (which worked before)
Ubuntu Server 10.04.3 LTS 32-bit (SolusVM) VPS
SSH configured on Port 2222 and root login disabled, only one user login allowed.
Using to connect to the VPS, FileZilla 3.5.0 on Ubuntu 10.10 64-bit

---

### Post by TuxLyn on 2011-08-25
I just tried sftp using ubuntu terminal with verbal option:
sftp -v -oPort=2222 [email]user@domain.com[/email]

This is the debug output:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.utf8
debug1: Sending subsystem: sftp
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype [email]eow@openssh.com[/email] reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
Transferred: sent 1528, received 1960 bytes, in 0.2 seconds
Bytes per second: sent 6341.2, received 8134.0
debug1: Exit status 141
Connection closed

So it looks like authentication worked, this is not an issue with login using username and password.

Any ideas ?

---

### Post by TuxLyn on 2011-08-25
Alright guys, by using scp I was able to see in debug mode this error: 
Couldn't open /dev/null: Permission denied

So all I needed to do is simply change permission:
```
chmod 666 /dev/null
```

and everything started working again :D I hope this helps some one else, to save them an hour of headache.

---

