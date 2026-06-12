---
title: "Smbpasswd script with ssh, help :("
date: 2009-12-09
forum: General Help
---

### Post by xzased on 2009-12-09
Hi. Im having trouble with a script passing down the smbpasswd for a user that already exists. If anyone can give me some pointers of how to go around this it would be great :o Here is what I have so far (I only have the smb restart part :( ) :

```
#!/bin/sh
#
for HOSTS in  192.168.0.1 192.168.0.2 192.168.0.3 
do
echo "Connecting to $HOSTS"
echo "Resetting SAMBA"
echo ""
ssh $HOSTS  '\/etc/init.d/smb restart;\'
echo "Finished job on $HOSTS"
echo ""

done

```

I've tried with stdin option but it only gives me the "-- invalid option"

---

