---
title: "samba issues"
date: 2006-04-06
forum: General Help
---

### Post by RicJD on 2006-04-06
My samba won't start anymore.  I've tried looking through logs and messages and all seems fine.  I ran "testparm" and this didn't give any errors.  Does anyone know where I can start to troubleshoot this?

Thanks is advanced

---

### Post by Ramses de Norre on 2006-04-06
```
smbd -s /etc/samba/smb.conf -i
```
What's the output of this?

---

### Post by RicJD on 2006-04-06
The output is:

```
smbd version 3.0.14a-Ubuntu started.
Copyright Andrew Tridgell and the Samba Team 1992-2004
Unable to open printcap file /etc/printcap for read!
Unable to open printcap file /etc/printcap for read!
file_init: Information only: requested 10000 open files, 1004 are available.
Failed to open /var/lib/samba/secrets.tdb
Failed to open /var/lib/samba/secrets.tdb
Failed to open /var/lib/samba/secrets.tdb
pdb_generate_sam_sid: Failed to store generated machine SID.
smb_panic(): calling panic action [/usr/share/samba/panic-action 13479]
/usr/share/samba/panic-action: line 48: mail: command not found
smb_panic(): action returned status 127
PANIC: Could not generate a machine SID

BACKTRACE: 7 stack frames:
 #0 smbd(smb_panic2+0x79) [0x81d3463]
 #1 smbd(smb_panic+0x19) [0x81d3660]
 #2 smbd(get_global_sam_sid+0x287) [0x8192ba7]
 #3 smbd(init_guest_info+0x5a) [0x82100a0]
 #4 smbd(main+0x2a2) [0x8246335]
 #5 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d52ec2]
 #6 smbd [0x8079a11]
Aborted
```

having a quick search on the net seems to suggest to disable SELinux, but a) I don't know 100% what this is and b) i don't want to disable stuff without knowing the consequences

If anyone could shed some light it would be greatly received

---

