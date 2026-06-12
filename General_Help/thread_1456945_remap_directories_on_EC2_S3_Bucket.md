---
title: "remap directories on EC2 S3 Bucket"
date: 2010-04-17
forum: General Help
---

### Post by bluethundr on 2010-04-17
I am trying to map several directories (/tmp, /var, /var/logs) to an S3 bucket on EC2. I have set up the partitions as /dev/sdb1, /dev/sdb2 and /dev/sdb3 and labelling them with e2label. 

I am giving them interim names with '2' at the end (e.g. /tmp2) so that I can move the contents of those folders to the right place on the S3 bucket, then delete the original directories and then rename the ones on S3 as the mount points I want to have there. I created a dry run with /tmp2 in my /etc/fstab (which I backed up) but the device (/dev/sdb1) will not mount. Any clues how best to proceed?

```

 
      # /etc/fstab: static file system information.
      # <file system>                                 <mount point>   <type>  <options>       <dump>  <pass>
  
      proc                                            /proc           proc    defaults        0       0
  
      /dev/sda3                                       None            swap    defaults        0       0
  
      /dev/sda1                                       /               ext3    defaults        0       0
   
      #/dev/sdb                                       /mnt            ext3    defaults        0       0
   
      /dev/sdb1                                       /tmp2       ext3    defaults            0       0

```

---

