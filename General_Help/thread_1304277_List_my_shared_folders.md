---
title: "List my shared folders"
date: 2009-10-29
forum: General Help
---

### Post by bigred1 on 2009-10-29
How can I see a list of the folders I have shared?

I have shared many filders (right-click->Sharing Optims or right-click->Properties->Share), and there are now so many that I want to remove some.

I know about Places->Network, but that shows my folders as if from the outside. It does not tell me the local path of the folder. Moreover, when I go to some of the local folders that appear, from the Places->Network list, to be shared, there is no sharing icon and right-lcik->Sharing Options does not say that are shared.

Is there a Samba GUI or  command-line command which will tell me the full list of local folders which are shared?

---

### Post by albandy on 2009-10-29
smbclient -L localhost

---

### Post by swerdna on 2009-10-29
run this command:```
ls -l /var/lib/samba/usershares
```all the shares created in Nautilus will be listed by that command. Suppose one of them is "billymusic". To get the path for the share called billymusic run this command:```
cat /var/lib/samba/usershares/billymusic | grep path
```it will show you the path to the directory.

---

### Post by bigred1 on 2009-10-29
Thanks. That did it.

---

### Post by loopduplicate on 2011-01-06
You can do this and see all shares in one command:
```
shares=$(ls -l /var/lib/samba/usershares | awk '{print "/var/lib/samba/usershares/"$8}')
for i in $shares
do
cat $i | grep path
done

```

---

### Post by loopduplicate on 2011-07-25
And here is how I unshare all folders with one script:
```
#!/bin/sh
shares=$(ls -l /var/lib/samba/usershares | awk '{print $8}')
for i in $shares
do
net usershare delete $i
done

```

---

