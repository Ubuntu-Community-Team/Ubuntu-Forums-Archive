---
title: "Cannot access encrypted /home partition  - 'not a valid LUKS device'"
date: 2011-02-17
forum: General Help
---

### Post by kwacka on 2011-02-17
After a  new install (Ubuntu 10.10 AMD64 from 10.04), I now cannot access (previously) encrypted /home.

Booting from Desktop CD,
```
sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sda4 crypt1
```

I get the response:
```
Device /dev/sda4 is not a valid LUKS device.
```

In addition I have tried ```
sudo mount -t ecryptfs /dev/sda4/.Private /mnt
```

and gone with defaults

enter passphrase - (entered)
select cipher - aes
select key bytes - 16
plaintext passthrough - n
enable filename encrytion - n
proceed with mount - yes
append sig - no

and received Error mounting eCryptfs: [-20] Not a directory.


Can I remove the encryption (I do have passphrase of course)?

Would another re-install, marking partition as 'encrypted' cause data loss?

Any advice would be welcome.

---

