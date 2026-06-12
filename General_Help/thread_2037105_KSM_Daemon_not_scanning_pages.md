---
title: "KSM Daemon not scanning pages"
date: 2012-08-03
forum: General Help
---

### Post by livin4th on 2012-08-03
Hello,
        I am trying to test the KSM feature of the kernel on my ubuntu system and seem stuck. The kernel was compiled with CONFIG_KSM=y and my application runs fine. But the ksmd daemon doesn't just scan any pages and reports the no of full_scans as 0. Is there any issue with the KSM and  ubuntu that i am not aware of? or is there something I am not doing right? I have already enabled the ksm and can see the ksmd running in the background.
 
Thanks,
livin

---

### Post by gordintoronto on 2012-08-03
Are you running multiple copies of the application? Did you read this page:
[http://www.linux-kvm.com/content/using-ksm-kernel-samepage-merging-kvm](http://www.linux-kvm.com/content/using-ksm-kernel-samepage-merging-kvm)

---

### Post by livin4th on 2012-08-06
Yes I wrote an application which mmaps a chunk of anon memory and ran 20 instances of the application at the same time. Each instance also sleeps for 1 minute to make sure that all instances have ovelapping execution times. I used the MADV_MERGEABLE flag too. I am not using any VM as such , but I think the ksmd is generic.

---

