---
title: "Damaged hard disk 2TB data recovery"
date: 2011-12-01
forum: General Help
---

### Post by h313 on 2011-12-01
My 2TB Seagate Dashboard crashed after falling off the table.
I am not able to mount this drive on pc now.

What is the best way to recover data from this drive ?

I know 2TB is too large, but atleast i need to recover some important files totaling around 300-400GB.

I can hear a rubbing noise from the hard disk, when i put my ear on it.
Thus it may be pretty hard to read from it.
Since all my efforts to recover it in ubuntu failed, i shifted to windows and i am using power data recovery 6.5 to recover the data.
But i am not convinced that, it will be successfull.

What should i do now ??
help me out.
really got some important data!! cannot afford to loose it.

---

### Post by 741Baus on 2011-12-01
Hi h313 , I had a similar experience dropped a 1tb hard drive and it would not mount at all .
I'm guessing its formatted to ntfs as your using Windows to try and recover your data .
You could use ntfsfix  
 
```
sudo apt-get install ntfsfix
``` 

```
sudo ntfsfix /dev/sdxy
```

where sdxy is the drive that you are trying to access, with this I was able to mount and access that particular drive that was dropped . 
     Peter

---

### Post by h313 on 2011-12-02
I will follow the steps and notify about the results soon.

Meanwhile, i tried Power Data Recovery too and performed Damaged Partition Recovery on it.
I was able to successfully recover 150GB of my data.
But, it had some inconsistencies. Are there chances that i still recover these files. Or they are permanently damaged ?

---

### Post by h313 on 2011-12-02
This was the output for
```
]sudo ntfsfix /dev/sdc
```
Where **sdc** is my drive

```
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.
```

What should i do now ?

---

