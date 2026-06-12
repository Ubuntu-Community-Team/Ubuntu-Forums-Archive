---
title: "Recover a bash script file (.sh)"
date: 2012-08-15
forum: General Help
---

### Post by khan2k on 2012-08-15
Hi,

I was wondering if anyone can guide me in recovering a custom made .sh file which I accidently deleted. I have tried:

[LIST]
[*]Searching on the forum, but searching for script, sh and recovery gives results regarding script creation.
[*]Foremost - but Foremost does not support sh files and I am unsure how to add sh as custom file type 
[/LIST]

---

### Post by raja.genupula on 2012-08-15
[https://help.ubuntu.com/community/DataRecovery/#Extract_individual_files_from_recovered_image](https://help.ubuntu.com/community/DataRecovery/#Extract_individual_files_from_recovered_image)

---

### Post by khan2k on 2012-08-15
The site you refer to is the one I found Foremost in. I am unsure how to use it to search for .sh files because Foremost does not natively support .sh files. Any ideas or workarounds?

---

### Post by raja.genupula on 2012-08-16
try this
```
mkdir ~/output
sudo magicrescue -r sh -d ~/output /dev/hdb1
```

place harddisk partition ID at hdb1 .

try the remaining methods too .

---

