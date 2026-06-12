---
title: "Problem with Klamav"
date: 2010-01-29
forum: General Help
---

### Post by antiphoton on 2010-01-29
I ran a virus scan on my computer today and following the scan it picked up 25 "hazardous"items.All of these items were encrypted zip files. It picked up a Thunderbird file which I had downloaded and installed through the basic Ubuntu Software Centre, as an encrypted zip file. My first question is if any of these encrypted zip files are hazardous because I know exactly what they all are. Secondly (this is really the big problem) all the files I selected for quarantine except for one were not able to be quarantined. When prompted it displayed this message:

"There was a problem quarantining /usr/lib/libclamav.so.6.0.5. Check your diskspace, the permissions on your quarantine location and whether a file with the same name already exists in the quarantine." 

I have 194 GB of disk space remaining so I doubt that is the problem. I checked the permissions on the quarantine folder and it was fully operational under my username, which happens to be the only user on my computer. If anyone out there could help me in any way, it would be greatly appreciated. I am running Karmic.

EDIT: I am running KlamAV version 0.46.

---

### Post by mhgsys on 2010-01-29
try running clamscan with sudo to check all files on the computer, displaying the name of each file: 

```
sudo clamscan -r /
```

---

### Post by antiphoton on 2010-01-29
Thank you. I ran the scan and came up with 0 viruses found. But do you have any idea to fix the quarantine problem in KlamAV?

---

### Post by mhgsys on 2010-01-29
when running it sudo the same error appeared?

I thought running it with sudo would overwrite permissions on your quarantine location and a file with the same name would be overwritten.

(I must say; I'm not an expert on clamav and I run 9.04 myself)

---

### Post by antiphoton on 2010-01-29
Well, when running the scan through sudo clamscan -r / it did not pick up any viruses, so I guess I'm fine. Thanks for your help though.

---

### Post by KEE on 2010-02-02
Klamav is broken isnt it? I know that error has been around for awhile, nobody cares to fix it i guess =/

---

