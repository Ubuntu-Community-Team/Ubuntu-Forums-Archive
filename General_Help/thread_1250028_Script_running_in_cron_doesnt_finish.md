---
title: "Script running in cron doesnt finish"
date: 2009-08-26
forum: General Help
---

### Post by parrimin on 2009-08-26
Hi,

I modified some script i found somewhere i cant remember to stop my virtual machines, tar/gzip its folders, and finally resume the virtual machines. This task is done one vmware image, and when finished, next vmware image is backed up same way.

If i run this script manually ir runs ok, but when in cron (with crontab -e) at 1:00 am, it starts, but not finish. When i come back to office in the morning, the first virtual machine is stopped, Some tar file is created, but is not running anymore. I know script is not running by several reasons:
1. tar file is not growing
2. The entire should have ended in about 2 hours.

I was searching about timeouts, but im not finding any helpful post, can anybody suggest what's happening?

Thanks!

---

### Post by kpkeerthi on 2009-08-26
Redirect the cron's output & error to a file and take a look at the file's content. 

```

xx yy * * * /some/cron/job > /home/<user-id>/cron.log 2>&1

```

---

### Post by parrimin on 2009-08-26
> **kpkeerthi said:**
> Redirect the cron's output & error to a file and take a look at the file's content. 


Ok, ill try now.

---

### Post by parrimin on 2009-08-26
Hey, the cron job finished, and seeing the log, it seems to be running an old version of myscript. Is it possible that if i create a job to run myscript, and after that i rewrite myscript cron runs the old version? It seems to be doing it... And if so, how can i say cron to run the newer version?

---

### Post by kpkeerthi on 2009-08-26
> **parrimin said:**
> Is it possible that if i create a job to run myscript, and after that i rewrite myscript cron runs the old version? 
No. Thats not possible. 

Just add some new **echo** statements to your script and let the cron run. Then, verify if it appears in the log file. Also, ensure that you are referring to your script using absolute path in the crontab.

---

### Post by parrimin on 2009-08-27
Hey, i have solved. It seems that the command ```
vmware start "mymachine"
``` needs gui, so cron in normal mode cant execute it. So i went to crontab -e, and put:
```
00 1 * * * env DISPLAY=:0 /home/user/myscript > /home/user/cron.log 2>&1
```

All running ok! Many thanks kpkeerthi. One more question. Whats 2>&1?

---

### Post by kpkeerthi on 2009-08-27
1 and 2 are the file descriptors for standard output and error respectively. 

In **/some/command > /some/file.log 2>&1**, the construct 2>&1 sends the command's standard error to the same place where standard output goes, which is the log file. 

You may google to read more about standard output/error and file descriptor.

---

