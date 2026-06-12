---
title: "warning and suspect file properties displayed"
date: 2011-06-18
forum: General Help
---

### Post by h4ck0lic on 2011-06-18
Today when I scanned my system with rkhunter, It gave me 3 file properties warnings.

rkhunter --check -l log.txt

1). /usr/bin/last  => warning
2).  /usr/bin/perl => warning
3). /sbin/sulogin => warning.


What does this warning indicates as i had no warnings earlier, This is recent warnings, and How can i rectify it.

Thanks

---

### Post by prodigy_ on 2011-06-18
> **h4ck0lic said:**
> 1). /usr/bin/last  => warning
2).  /usr/bin/perl => warning
3). /sbin/sulogin => warning.
This doesn't look like a part of rkhunter log. Should be something like:
```
[15:27:40] /usr/bin/mail                                     [ Warning ]
[15:27:41] Warning: The file '/usr/bin/mail' exists on the system, but it is not present in the rkhunter.dat file.
```

Use **sudo cat log.txt** to read the log file.

---

### Post by h4ck0lic on 2011-06-18
File Properties :-

```
/usr/bin/last                                         [ Warning ]
/usr/bin/perl                                         [ Warning ]
/sbin/sulogin                                         [ Warning ]


```
Performing trojan specific checks

```
Checking for enabled inetd services                   [ Warning ]

Warning: Found enabled inetd service: tftp


```

```

Checking if SSH root access is allowed                [ Warning ]

Warning: The SSH and rkhunter configuration options should be the same:
[02:30:35]          SSH configuration option 'PermitRootLogin': yes
[02:30:35]          Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no



```

Performing filesystem checks

```
Checking /dev for suspicious file types               [ Warning ]
Checking for hidden files and directories             [ Warning ]

 Checking /dev for suspicious file types         [ Warning ]
[02:30:36] Warning: Suspicious file types found in /dev:
[02:30:36]          /dev/shm/pulse-shm-3744425219: data
[02:30:36]          /dev/shm/pulse-shm-3080383606: data
[02:30:36]          /dev/shm/pulse-shm-4165232942: data
[02:30:36]          /dev/shm/pulse-shm-3175425441: data
[02:30:36]          /dev/shm/pulse-shm-928137017: data
[02:30:37]   Checking for hidden files and directories       [ Warning ]
[02:30:37] Warning: Hidden directory found: /etc/.java
[02:30:37] Warning: Hidden directory found: /dev/.udev
[02:30:37] Warning: Hidden directory found: /dev/.initramfs




```

---

### Post by h4ck0lic on 2011-06-19
Can anyone help me here ?

---

### Post by dFlyer on 2011-06-19
> **h4ck0lic said:**
> Today when I scanned my system with rkhunter, It gave me 3 file properties warnings.

rkhunter --check -l log.txt

1). /usr/bin/last  => warning
2).  /usr/bin/perl => warning
3). /sbin/sulogin => warning.


What does this warning indicates as i had no warnings earlier, This is recent warnings, and How can i rectify it.

Thanks

Have you read up on rkhunter. Some of your warning may be normal hits. What makes you think you have a rootkit?

---

