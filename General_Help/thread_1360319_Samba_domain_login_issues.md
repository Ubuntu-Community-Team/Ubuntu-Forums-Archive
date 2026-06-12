---
title: "Samba domain login issues"
date: 2009-12-20
forum: General Help
---

### Post by BraedonVickers on 2009-12-20
I am using a custom PAM configuration to login to Ubuntu 9.10 desktop machines with a Samba domain account. However, there are strange issues with the authentication over time; it seems to drop out randomly, with varied consequences and symptoms.

For example, if you do not log in within 5 minutes or so of booting a machine, the login fails with "Access is Denied" (I have occasionally seen other messages as well).

A few minutes after logging in successfully, any new terminal will first display
```
groups: cannot find name for group ID 26187
groups: cannot find name for group ID 15513
groups: cannot find name for group ID 26001
groups: cannot find name for group ID 26019
groups: cannot find name for group ID 26021
groups: cannot find name for group ID 26025
groups: cannot find name for group ID 26067
groups: cannot find name for group ID 26133
groups: cannot find name for group ID 26147
```or similar.

After a further period of time, sudo can stop working, either not letting you sudo at all, or rejecting your password. Once again, there seem to be a number of possible error messages. For example:
```
braedon is not in the sudoers file.  This incident will be reported.
```Other commands can also be affected sometimes, such as ssh, saying
```
you do not exist, go away!
``` or something like that.

When any of this will happen, or the speed in which it happens, seems to be very random. Sometimes you will get hours of perfect function. Other times it will break within minutes, and keep breaking every 5 minutes, or never trouble you again after the initial time.

All of these issues, with the exception of the group name errors at terminal startup (which seems to persist after it starts no matter what you do) can be fixed by restarting winbind.
Occasionally it can be fixed with
```
wbinfo -t
```log.wb-<domain> is spammed with large numbers of these messages:
```
[2009/12/21 12:35:31,  0] libsmb/ntlmssp_sign.c:208(ntlmssp_check_packet)
  NTLMSSP NTLM2 packet check failed due to invalid signature!
[2009/12/21 12:35:31,  0] rpc_client/cli_pipe.c:620(cli_pipe_verify_ntlmssp)
  cli_pipe_verify_ntlmssp: failed to unseal packet from host TGA1. Error was NT_STATUS_ACCESS_DENIED.
``` periodically. I am not sure if this is related, however, as it seems to happen whether things are working or not.

log.winbindd also gets spammed with the same messages, though not as much, in a similar manner:
Other suspicious messages in the same log include:
```
[2009/12/21 10:28:43,  1] rpc_client/cli_pipe.c:948(cli_pipe_validate_current_pdu)
  cli_pipe_validate_current_pdu: RPC fault code DCERPC_FAULT_OP_RNG_ERROR received from host TGA1!
[2009/12/21 10:32:57,  1] winbindd/winbindd_group.c:1015(getgrgid_recv)
  could not convert gid 10000 to sid
```Their appearance or lack of also doesn't seem to follow any pattern that I have found.

The samba server was not set up by me, and runs on SME not Ubuntu (I am working on porting the setup to a Ubuntu server, to see if the issue is platform specific), but I should be able to get specific information about it if required. The server logs don't seem to show anything related.

I have yet to be able to determine if the problem is a bug or configuration issue, nor if it is a problem at server or client side.

I have attached related configuration files (there are quite a few so I have chucked them in a tar).

So, does anyone have any ideas for potential problems at the client side?

Thanks,
   Braedon

---

### Post by BraedonVickers on 2010-01-05
Upgrading samba-related packages on the client machine to the latest versions for Ubuntu 10.04 seems to fix the problems, if anyone is having similar issues.

<sarcasm> Thanks for all the help Ubuntu community </sarcasm> :P

   Braedon

---

