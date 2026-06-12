---
title: "Cryptsetup not working when trying to setup external drive"
date: 2010-04-04
forum: General Help
---

### Post by CsRueK8hzJ@§ on 2010-04-04
Hi guys,

I'm trying to cryptsetup an external USB-drive on a Ubuntu 9.10 with all updates installed. But all I get is this:

```

root@localhost:~# tail -f /var/log/syslog -n0 &
[1] 4304
root@localhost:~# LC_ALL=en_US cryptsetup -yc cbc-essiv-aes:sha256 create sdc /dev/sdb1
Enter passphrase: 
Verify passphrase: 
Command failed: device-mapper: reload ioctl failed: Invalid argument
Apr  4 23:24:19 localhost kernel: [ 2744.341938] device-mapper: table: 252:3: crypt: Error allocating crypto tfm
Apr  4 23:24:19 localhost kernel: [ 2744.341944] device-mapper: ioctl: error adding target to table
Apr  4 23:24:19 localhost kernel: [ 2744.342213] device-mapper: ioctl: device doesn't appear to be in the dev hash table.
root@localhost:~# 

```What's strange: the system is running from an crypted root partition. So dmcrypt should work, obviously and all the necessary modules are loaded:

```

root@localhost:~# cryptsetup status sda3_crypt
/dev/mapper/sda3_crypt is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda3
  offset:  2056 sectors
  size:    254242634 sectors
  mode:    read/write
root@localhost:~# lsmod | egrep '(cbc|aes|crypt|sha)'
sha256_generic         11580  0 
aes_i586                8124  3 
aes_generic            27484  1 aes_i586
cbc                     3516  1 
dm_crypt               12928  1 
root@localhost:~#

```

I really don't know why it isn't working ... Hopefully anyone of you does! :)

regards, mh166

---

