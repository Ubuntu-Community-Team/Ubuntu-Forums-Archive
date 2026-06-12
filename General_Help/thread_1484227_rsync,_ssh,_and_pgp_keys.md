---
title: "rsync, ssh, and pgp keys"
date: 2010-05-15
forum: General Help
---

### Post by jerome1232 on 2010-05-15
I setup keyed ssh between two of my computers on my lan. It was working great. I used Ubuntu's Passwords and Encryption Keys tool to generate the key because I'm lazy.

Yesterday I tried rsync'ing a grip of files to the ssh server and couldn't get it to work, I figured I was just messing the rsync command up. Today I just tried to log in using ssh and it just hangs there after I type the ssh command.

With verbosity on it stops at checking the blacklist file. Does this mean it decided my key is one of the badly generated ones? Why would it decide this now I thought it was supposed to catch that when generating the key.


edit: Also I just checked that file it's trying to check doesn't even exist. Should it?
```
ssh -vvv -i /home/jeremy/.ssh/id_rsa jerome@voiceserv
OpenSSH_5.3p1 Debian-3ubuntu3, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to voiceserv [192.168.1.64] port 22.
debug1: Connection established.
debug3: Not a RSA1 key file /home/jeremy/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/jeremy/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048

```

---

### Post by jerome1232 on 2010-05-15
Okay so I dragged a Monitor and Keyboard over to the server and lo and behold it was sitting at a Kernel Panic! Looks like there were i/o errors while accessing sdb. I'm guessing that happened while I was rsync'ing to it.

I hope I don't need a new hdd, how can I look into that drive? This particular system has no gui so cli tools only.

Currently running a smartctl -t long test on it.

Before it ran i grabbed some smart info, I'm not very certain how to read the output though.

```
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   065   055   006    Pre-fail  Always       -       87446357
  3 Spin_Up_Time            0x0003   097   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       119
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       6
  7 Seek_Error_Rate         0x000f   087   060   030    Pre-fail  Always       -       499172886
  9 Power_On_Hours          0x0032   084   084   000    Old_age   Always       -       14856
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2172
194 Temperature_Celsius     0x0022   048   072   000    Old_age   Always       -       48
195 Hardware_ECC_Recovered  0x001a   065   055   000    Old_age   Always       -       87446357
197 Current_Pending_Sector  0x0012   076   076   000    Old_age   Always       -       26786
198 Offline_Uncorrectable   0x0010   076   076   000    Old_age   Offline      -       26786
199 UDMA_CRC_Error_Count    0x003e   200   198   000    Old_age   Always       -       8
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   074   227   000    Old_age   Always       -       26
```

---

