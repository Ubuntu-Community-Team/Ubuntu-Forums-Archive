---
title: "Ticket Forwarding / GSSAPI / Failed gssapi-with-mic"
date: 2010-12-11
forum: General Help
---

### Post by schulze-tue on 2010-12-11
Hi all,

I am trying to get kerberos ticket forwarding via SSH to work between RHEL and Ubuntu. It is working, when connecting from Ubuntu to RHEL, but not the other way round. (It also works between RHEL machines.) I have enabled the GSSAPI features in both SSH client and server, checked keytabs and verified, that my ticket is forwardable.

When doing ssh -vvv, I get the following on the client
```
debug1: Next authentication method: gssapi-with-mic
debug2: we sent a gssapi-with-mic packet, wait for reply
debug1: Delegating credentials
debug1: Delegating credentials
Connection closed by 134.2.9.120 (This is the server IP)
```On the server, I get
```
Dec 11 12:14:09 arahanga sshd[5733]: debug1: Forked child 6973.
Dec 11 12:14:09 arahanga sshd[6973]: debug1: rexec start in 4 out 4 newsock 4 pipe 6 sock 7
Dec 11 12:14:09 arahanga sshd[6973]: debug1: inetd sockets after dupping: 3, 3
Dec 11 12:14:09 arahanga sshd[6973]: Connection from 134.2.9.176 port 36317
Dec 11 12:14:09 arahanga sshd[6973]: debug1: Client protocol version 2.0; client software version OpenSSH_4.3p2
Dec 11 12:14:09 arahanga sshd[6973]: debug1: match: OpenSSH_4.3p2 pat OpenSSH_4*
Dec 11 12:14:09 arahanga sshd[6973]: debug1: Enabling compatibility mode for protocol 2.0
Dec 11 12:14:09 arahanga sshd[6973]: debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
Dec 11 12:14:10 arahanga sshd[6973]: debug1: PAM: initializing for "schulze"
Dec 11 12:14:10 arahanga sshd[6973]: debug1: PAM: setting PAM_RHOST to "prejudice.informatik.uni-tuebingen.de"
Dec 11 12:14:10 arahanga sshd[6973]: debug1: PAM: setting PAM_TTY to "ssh"
Dec 11 12:14:10 arahanga sshd[6973]: Failed none for schulze from 134.2.9.176 port 36317 ssh2
Dec 11 12:14:10 arahanga sshd[6973]: debug1: Received some client credentials
Dec 11 12:14:10 arahanga sshd[6973]: Authorized to schulze, krb5 principal schulze@INFORMATIK.UNI-TUEBINGEN.DE (krb5_kuserok)
Dec 11 12:14:10 arahanga sshd[6973]: debug1: do_pam_account: called
Dec 11 12:14:10 arahanga sshd[6973]: Failed gssapi-with-mic for schulze from 134.2.9.176 port 36317 ssh2
Dec 11 12:14:10 arahanga sshd[6973]: debug1: do_cleanup
Dec 11 12:14:10 arahanga sshd[6973]: debug1: PAM: cleanup
```As you can see, there is no information, why gssapi-with-mic is failing and I already have switched sshd to DEBUG log level. When doing klist on the client after the failure, I can see, that I **did** get the host ticket from the server (it's the last one in the list):

Dec 11 12:28:45  Dec 12 13:28:45  krbtgt/INFORMATIK.UNI-TUEBINGEN.DE@INFORMATIK.UNI-TUEBINGEN.DE
Dec 11 12:28:45  Dec 12 13:28:45  [EMAIL="afs@INFORMATIK.UNI-TUEBINGEN.DE"]afs@INFORMATIK.UNI-TUEBINGEN.DE[/EMAIL]
Dec 11 12:28:52  Dec 12 13:28:45  host/arahanga.informatik.uni-tuebingen.de@INFORMATIK.UNI-TUEBINGEN.DE

Any idea, how to get more information? Could it have s. th. to do with using allow_weak_crypto=yes in our krb5.conf? I have to use that, because our kerberos server only supports DES encryption.

Any help is appreciated.

---

### Post by schulze-tue on 2010-12-11
Turns out, it was a pam configuration problem in /etc/pam.d/common-account. The debug output was ```

debug1: do_pam_account: called

```
but I had overlooked that message, because it did not state any error.

---

### Post by Javache on 2011-06-28
I'm having the exact same issue. How did you solve it?

---

### Post by sapg on 2012-08-15
I'd like to know the solution too, it isn't clear.

---

