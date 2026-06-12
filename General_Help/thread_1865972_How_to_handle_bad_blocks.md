---
title: "How to handle bad blocks?"
date: 2011-10-20
forum: General Help
---

### Post by thunderbirdje on 2011-10-20
Repartitioning my drive failed due bad blocks (details see below)

I have read on several threads that you can mark the bad blocks as 'bad'. However I have seen different commands for that like: ```
sudo dd if=<device-name> of=/dev/null bs=512 count=1 skip=<sector>
``` 

I am wondering if this is a correct syntax to do this??? Before I proceed and mess up my lovely Ubuntu partition :) Thank you for any help!

```
user@pc:~$ sudo badblocks -sv -b 512 /dev/sda
[sudo] password for user: 
Checking blocks 0 to 312581807
Checking for bad blocks (read-only test): 124740672one, 30:09 elapsed
124740688one, 31:03 elapsed
124740689one, 31:20 elapsed
124740690one, 31:39 elapsed
124740691one, 31:57 elapsed
124740692one, 32:14 elapsed
124740693one, 32:33 elapsed
124740694one, 32:51 elapsed
124740695one, 33:10 elapsed
done                                
Pass completed, 9 bad blocks found.
```

---

### Post by dcstar on 2011-10-21
> **thunderbirdje said:**
> Repartitioning my drive failed due bad blocks (details see below)

I have read on several threads that you can mark the bad blocks as 'bad'.
.......

```
man e2fsck
```

---

### Post by thunderbirdje on 2011-10-23
> **dcstar said:**
> ```
man e2fsck
```

Thank you!

I had to eventually reformat the whole drive. Because I needed a windows partition for some only windows programs for my university - such a pity -. The tool provided by my HD manufacturer (WD)  was only Windows based and could only handle the active windows partition. 

Thank you for the help!

---

