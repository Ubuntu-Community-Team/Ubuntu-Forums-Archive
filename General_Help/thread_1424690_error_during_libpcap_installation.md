---
title: "error during libpcap installation"
date: 2010-03-08
forum: General Help
---

### Post by AbyssRock on 2010-03-08
hi, i've tried to install libpcap 1.0.0 , it was all ok until I run the make install, then I received this message: 
```
ln: creating hard link `/usr/local/share/man/man3/pcap_datalink_val_to_description.3pcap' to `/usr/local/share/man/man3/pcap_datalink_val_to_name.3pcap': File exists
make: *** [install] Error 1
```
so I tried 
```
sudo mv /usr/local/share/man/man3/pcap_datalink_val_to_description.3pcap /usr/local/share/man/man3/pcap_datalink_val_to_description.3pcap.backup
```
e re-run make install but the problem is still there.Any ideas?

---

