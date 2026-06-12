---
title: "Hundreds/thousands of ecryptfs errors!"
date: 2010-02-13
forum: General Help
---

### Post by tom66 on 2010-02-13
I'm backing up my data asap. 

However, I am getting hundreds, maybe thousands of disk I/O errors when trying to run everyday programs, such as sqlite and firefox. 

Looking at dmesg, I see these items repeated many, many times:

```

[ 2405.989631] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000048e])
[ 2405.989692] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2405.989695] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 2405.989697] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000048e])
[ 2496.764860] Valid eCryptfs headers not found in file header region or xattr region
[ 2496.764865] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[ 2620.951023] ecryptfs_write_lower: octets_written = [-28]; expected [8192]
[ 2620.951032] ecryptfs_write_metadata_to_contents: Error attempting to write header information to lower file; rc = [-22]
[ 2620.951036] ecryptfs_write_metadata: Error writing metadata out to lower file; rc = [-22]
[ 2620.951041] Error writing headers; rc = [-22]
[ 2621.107998] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2621.108006] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 2621.108011] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000614])
[ 2621.197827] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2621.197835] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 2621.197840] ecryptfs_write: Error encrypting page; rc = [-22]
[ 2621.197845] ecryptfs_write_begin: Error on attempt to truncate to (higher) offset [6389760]; rc = [-22]
[ 2621.287747] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2621.287755] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 2621.287760] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000116])
[ 2621.377681] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2621.377689] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 2621.377694] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000116])
[ 2621.469124] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2621.469133] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]

...

[ 3691.046589] Valid eCryptfs headers not found in file header region or xattr region
[ 3691.046596] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[ 3696.997598] Valid eCryptfs headers not found in file header region or xattr region
[ 3696.997602] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[ 3720.670098] INFO: task firefox:5833 blocked for more than 120 seconds.
[ 3720.670102] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3720.670105] firefox       D 0000000000000000     0  5833      1 0x00000004
[ 3720.670110]  ffff880074f959d8 0000000000000082 0000000100000009 0000000000015880
[ 3720.670115]  ffff88008e1c9a60 0000000000015880 0000000000015880 0000000000015880
[ 3720.670119]  0000000000015880 ffff88008e1c9a60 0000000000015880 0000000000015880
[ 3720.670123] Call Trace:
[ 3720.670132]  [<ffffffff810da8c0>] ? sync_page+0x0/0x50
[ 3720.670137]  [<ffffffff8152af88>] io_schedule+0x28/0x40
[ 3720.670140]  [<ffffffff810da8fd>] sync_page+0x3d/0x50
[ 3720.670144]  [<ffffffff8152b572>] __wait_on_bit_lock+0x52/0xb0
[ 3720.670147]  [<ffffffff810da8a2>] __lock_page+0x62/0x70
[ 3720.670151]  [<ffffffff81078bd0>] ? wake_bit_function+0x0/0x40
[ 3720.670154]  [<ffffffff810da6d9>] ? find_get_page+0x19/0xa0
[ 3720.670158]  [<ffffffff810dc34e>] find_lock_page+0x5e/0x80
[ 3720.670161]  [<ffffffff810dc3b5>] grab_cache_page_write_begin+0x45/0xc0
[ 3720.670166]  [<ffffffff811ff2a5>] ecryptfs_write_begin+0x45/0x320
[ 3720.670169]  [<ffffffff810da322>] generic_perform_write+0xb2/0x1d0
[ 3720.670172]  [<ffffffff810db153>] generic_file_buffered_write+0x83/0x140
[ 3720.670176]  [<ffffffff810dcad0>] __generic_file_aio_write_nolock+0x240/0x470
[ 3720.670180]  [<ffffffff810dce20>] generic_file_aio_write+0x70/0xf0
[ 3720.670184]  [<ffffffff8111f302>] do_sync_write+0xf2/0x130
[ 3720.670188]  [<ffffffff81078b90>] ? autoremove_wake_function+0x0/0x40
[ 3720.670192]  [<ffffffff81138b6b>] ? mntput_no_expire+0x2b/0x100
[ 3720.670196]  [<ffffffff81224af1>] ? security_file_permission+0x11/0x20
[ 3720.670200]  [<ffffffff8111f5e8>] vfs_write+0xb8/0x1a0
[ 3720.670203]  [<ffffffff8112009c>] sys_write+0x4c/0x80
[ 3720.670208]  [<ffffffff81012042>] system_call_fastpath+0x16/0x1b
[ 3840.660185] INFO: task firefox:5833 blocked for more than 120 seconds.
[ 3840.660192] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3840.660196] firefox       D 0000000000000000     0  5833      1 0x00000004
[ 3840.660204]  ffff880074f959d8 0000000000000082 0000000100000009 0000000000015880
[ 3840.660211]  ffff88008e1c9a60 0000000000015880 0000000000015880 0000000000015880
[ 3840.660218]  0000000000015880 ffff88008e1c9a60 0000000000015880 0000000000015880
[ 3840.660224] Call Trace:
[ 3840.660236]  [<ffffffff810da8c0>] ? sync_page+0x0/0x50
[ 3840.660244]  [<ffffffff8152af88>] io_schedule+0x28/0x40
[ 3840.660249]  [<ffffffff810da8fd>] sync_page+0x3d/0x50
[ 3840.660254]  [<ffffffff8152b572>] __wait_on_bit_lock+0x52/0xb0
[ 3840.660259]  [<ffffffff810da8a2>] __lock_page+0x62/0x70
[ 3840.660266]  [<ffffffff81078bd0>] ? wake_bit_function+0x0/0x40
[ 3840.660271]  [<ffffffff810da6d9>] ? find_get_page+0x19/0xa0
[ 3840.660277]  [<ffffffff810dc34e>] find_lock_page+0x5e/0x80
[ 3840.660282]  [<ffffffff810dc3b5>] grab_cache_page_write_begin+0x45/0xc0
[ 3840.660289]  [<ffffffff811ff2a5>] ecryptfs_write_begin+0x45/0x320
[ 3840.660294]  [<ffffffff810da322>] generic_perform_write+0xb2/0x1d0
[ 3840.660300]  [<ffffffff810db153>] generic_file_buffered_write+0x83/0x140
[ 3840.660306]  [<ffffffff810dcad0>] __generic_file_aio_write_nolock+0x240/0x470
[ 3840.660312]  [<ffffffff810dce20>] generic_file_aio_write+0x70/0xf0
[ 3840.660319]  [<ffffffff8111f302>] do_sync_write+0xf2/0x130
[ 3840.660324]  [<ffffffff81078b90>] ? autoremove_wake_function+0x0/0x40
[ 3840.660331]  [<ffffffff81138b6b>] ? mntput_no_expire+0x2b/0x100
[ 3840.660337]  [<ffffffff81224af1>] ? security_file_permission+0x11/0x20
[ 3840.660343]  [<ffffffff8111f5e8>] vfs_write+0xb8/0x1a0
[ 3840.660349]  [<ffffffff8112009c>] sys_write+0x4c/0x80
[ 3840.660356]  [<ffffffff81012042>] system_call_fastpath+0x16/0x1b

...

[ 4948.737837] ecryptfs_write_end: Error encrypting page (upper index [0x00000000000003c9])
[ 4949.006812] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 4949.006817] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 4949.006820] ecryptfs_write: Error encrypting page; rc = [-22]
[ 5196.943225] Valid eCryptfs headers not found in file header region or xattr region
[ 5196.943232] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO

```

Anybody else seeing this problem?

---

### Post by Allochtoon on 2010-04-03
> **tom66 said:**
> I'm backing up my data asap. 

However, I am getting hundreds, maybe thousands of disk I/O errors when trying to run everyday programs, such as sqlite and firefox. 

Looking at dmesg, I see these items repeated many, many times:

```

[ 2405.989631] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000048e])
[ 2405.989692] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2405.989695] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 2405.989697] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000048e])
[ 2496.764860] Valid eCryptfs headers not found in file header region or xattr region
[ 2496.764865] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[ 2620.951023] ecryptfs_write_lower: octets_written = [-28]; expected [8192]
[ 2620.951032] ecryptfs_write_metadata_to_contents: Error attempting to write header information to lower file; rc = [-22]
[ 2620.951036] ecryptfs_write_metadata: Error writing metadata out to lower file; rc = [-22]
[ 2620.951041] Error writing headers; rc = [-22]
[ 2621.107998] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2621.108006] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 2621.108011] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000614])
[ 2621.197827] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2621.197835] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 2621.197840] ecryptfs_write: Error encrypting page; rc = [-22]
[ 2621.197845] ecryptfs_write_begin: Error on attempt to truncate to (higher) offset [6389760]; rc = [-22]
[ 2621.287747] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2621.287755] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 2621.287760] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000116])
[ 2621.377681] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2621.377689] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 2621.377694] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000116])
[ 2621.469124] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 2621.469133] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]

...

[ 3691.046589] Valid eCryptfs headers not found in file header region or xattr region
[ 3691.046596] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[ 3696.997598] Valid eCryptfs headers not found in file header region or xattr region
[ 3696.997602] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[ 3720.670098] INFO: task firefox:5833 blocked for more than 120 seconds.
[ 3720.670102] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3720.670105] firefox       D 0000000000000000     0  5833      1 0x00000004
[ 3720.670110]  ffff880074f959d8 0000000000000082 0000000100000009 0000000000015880
[ 3720.670115]  ffff88008e1c9a60 0000000000015880 0000000000015880 0000000000015880
[ 3720.670119]  0000000000015880 ffff88008e1c9a60 0000000000015880 0000000000015880
[ 3720.670123] Call Trace:
[ 3720.670132]  [<ffffffff810da8c0>] ? sync_page+0x0/0x50
[ 3720.670137]  [<ffffffff8152af88>] io_schedule+0x28/0x40
[ 3720.670140]  [<ffffffff810da8fd>] sync_page+0x3d/0x50
[ 3720.670144]  [<ffffffff8152b572>] __wait_on_bit_lock+0x52/0xb0
[ 3720.670147]  [<ffffffff810da8a2>] __lock_page+0x62/0x70
[ 3720.670151]  [<ffffffff81078bd0>] ? wake_bit_function+0x0/0x40
[ 3720.670154]  [<ffffffff810da6d9>] ? find_get_page+0x19/0xa0
[ 3720.670158]  [<ffffffff810dc34e>] find_lock_page+0x5e/0x80
[ 3720.670161]  [<ffffffff810dc3b5>] grab_cache_page_write_begin+0x45/0xc0
[ 3720.670166]  [<ffffffff811ff2a5>] ecryptfs_write_begin+0x45/0x320
[ 3720.670169]  [<ffffffff810da322>] generic_perform_write+0xb2/0x1d0
[ 3720.670172]  [<ffffffff810db153>] generic_file_buffered_write+0x83/0x140
[ 3720.670176]  [<ffffffff810dcad0>] __generic_file_aio_write_nolock+0x240/0x470
[ 3720.670180]  [<ffffffff810dce20>] generic_file_aio_write+0x70/0xf0
[ 3720.670184]  [<ffffffff8111f302>] do_sync_write+0xf2/0x130
[ 3720.670188]  [<ffffffff81078b90>] ? autoremove_wake_function+0x0/0x40
[ 3720.670192]  [<ffffffff81138b6b>] ? mntput_no_expire+0x2b/0x100
[ 3720.670196]  [<ffffffff81224af1>] ? security_file_permission+0x11/0x20
[ 3720.670200]  [<ffffffff8111f5e8>] vfs_write+0xb8/0x1a0
[ 3720.670203]  [<ffffffff8112009c>] sys_write+0x4c/0x80
[ 3720.670208]  [<ffffffff81012042>] system_call_fastpath+0x16/0x1b
[ 3840.660185] INFO: task firefox:5833 blocked for more than 120 seconds.
[ 3840.660192] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3840.660196] firefox       D 0000000000000000     0  5833      1 0x00000004
[ 3840.660204]  ffff880074f959d8 0000000000000082 0000000100000009 0000000000015880
[ 3840.660211]  ffff88008e1c9a60 0000000000015880 0000000000015880 0000000000015880
[ 3840.660218]  0000000000015880 ffff88008e1c9a60 0000000000015880 0000000000015880
[ 3840.660224] Call Trace:
[ 3840.660236]  [<ffffffff810da8c0>] ? sync_page+0x0/0x50
[ 3840.660244]  [<ffffffff8152af88>] io_schedule+0x28/0x40
[ 3840.660249]  [<ffffffff810da8fd>] sync_page+0x3d/0x50
[ 3840.660254]  [<ffffffff8152b572>] __wait_on_bit_lock+0x52/0xb0
[ 3840.660259]  [<ffffffff810da8a2>] __lock_page+0x62/0x70
[ 3840.660266]  [<ffffffff81078bd0>] ? wake_bit_function+0x0/0x40
[ 3840.660271]  [<ffffffff810da6d9>] ? find_get_page+0x19/0xa0
[ 3840.660277]  [<ffffffff810dc34e>] find_lock_page+0x5e/0x80
[ 3840.660282]  [<ffffffff810dc3b5>] grab_cache_page_write_begin+0x45/0xc0
[ 3840.660289]  [<ffffffff811ff2a5>] ecryptfs_write_begin+0x45/0x320
[ 3840.660294]  [<ffffffff810da322>] generic_perform_write+0xb2/0x1d0
[ 3840.660300]  [<ffffffff810db153>] generic_file_buffered_write+0x83/0x140
[ 3840.660306]  [<ffffffff810dcad0>] __generic_file_aio_write_nolock+0x240/0x470
[ 3840.660312]  [<ffffffff810dce20>] generic_file_aio_write+0x70/0xf0
[ 3840.660319]  [<ffffffff8111f302>] do_sync_write+0xf2/0x130
[ 3840.660324]  [<ffffffff81078b90>] ? autoremove_wake_function+0x0/0x40
[ 3840.660331]  [<ffffffff81138b6b>] ? mntput_no_expire+0x2b/0x100
[ 3840.660337]  [<ffffffff81224af1>] ? security_file_permission+0x11/0x20
[ 3840.660343]  [<ffffffff8111f5e8>] vfs_write+0xb8/0x1a0
[ 3840.660349]  [<ffffffff8112009c>] sys_write+0x4c/0x80
[ 3840.660356]  [<ffffffff81012042>] system_call_fastpath+0x16/0x1b

...

[ 4948.737837] ecryptfs_write_end: Error encrypting page (upper index [0x00000000000003c9])
[ 4949.006812] ecryptfs_write_lower: octets_written = [-28]; expected [4096]
[ 4949.006817] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-22]
[ 4949.006820] ecryptfs_write: Error encrypting page; rc = [-22]
[ 5196.943225] Valid eCryptfs headers not found in file header region or xattr region
[ 5196.943232] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO

```

Anybody else seeing this problem?

me. my system showed these errors but i thought it was just a bug. how wrong i presumed. a few days ago my system began freezing violently during usage. 

for the time being ill just run an unencrypted home dir.

---

### Post by nicolasdiogo on 2011-03-26
same error here

did you find out how to solve this?

thanks,

---

### Post by Khelair on 2011-04-22
I've just noted the exact same set of problems happening to me today.  This comes after a kernel module modification that I had to make yesterday in order to get my Cisco Linksys AE 1000 USB wireless networking adapter to work.  At first that I thought I was having some sort of networking issue causing massive transmission errors hanging everything...  Turns out that the whole issue is causing issues that are skyrocketing my processor usage from rsyslogd (up to 140% on a quad-core PhenomII) and one of the gnome filesystem helper programs (taking up almost all of another core).

I was wondering if you've found any resolution or if there's any further data on this.  I'm going to try to turn off my encrypted home directory for now, but I'd like to be able to solve this and return to my original configuration, at some point.

Is this a fairly well known problem/bug?  I saw it listed on another forum as a numbered bug, as well, I believe.

TIA

---

