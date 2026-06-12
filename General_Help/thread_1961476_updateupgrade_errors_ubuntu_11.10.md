---
title: "update/upgrade errors ubuntu 11.10"
date: 2012-04-19
forum: General Help
---

### Post by uniqueone-85 on 2012-04-19
I recently installed ubuntu 11.10. Once i got the internet going i wanted to do some updates so that i wouldn't have any problems with the programs i was using. when i tried to upgrade everything (using terminal) i was met with an error after everything was finished downloading, i guess it happened when ubuntu was getting ready to install the upgrades. I unfortunatly did not save the error i got the first time because noting else would work after that even firefox. So i restarted and tried again in terminal to install the upgrades needed. After i put in the command to update i was met with these errors:

Reading package lists... Error!
E: Problem parsing dependency Conflicts
E: Error occurred while processing librarian0 (NewVersion2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I would like to know if there is a fix for this, i have used ubuntu for about 1yr now and i am still not that great with figuring out this type of stuff. Any help will be appreciated.

---

### Post by IWantFroyo on 2012-04-19
I assume you ran "sudo apt-get update" and then "sudo apt-get dist-upgrade"

Seems you have a dependency issue. Try:
```
sudo apt-get install -f
```

---

### Post by uniqueone-85 on 2012-04-19
i tried that and unfortunately was the same error remains.

---

### Post by IWantFroyo on 2012-04-19
Try changing your software sources. Software Center->Edit->Software Sources. Then update.

---

### Post by uniqueone-85 on 2012-04-19
ok tried changing and still no dice......what sources should i be using?

---

### Post by uniqueone-85 on 2012-04-19
ok so i tried doing the trouble shoot procedure.....and after a couple of tries i get this error:

Fetched 247 MB in 13min 49s (298 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 148979 files and directories currently installed.)
Preparing to replace gzip 1.3.12-9ubuntu1.1 (using .../gzip_1.3.12-9ubuntu1.2_i386.deb) ...
Unpacking replacement gzip ...
Processing triggers for install-info ...
Processing triggers for man-db ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 12859 package 'manpages':
 'insdalled' is not allowed for third (status) word in `status' field
E: Sub-process /usr/bin/dpkg returned an error code (2)

tried install -f and still not working

---

