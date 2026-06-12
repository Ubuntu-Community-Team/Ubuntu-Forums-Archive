---
title: "cron job not working"
date: 2010-02-08
forum: General Help
---

### Post by kcchen on 2010-02-08
Hi
I'm currently using Ubuntu 9.10 on a local machine, and having some strange issues with it's cronjob. 

Let's say my local machine is Local and is running Ubuntu and I run commands primarily from Local. A remote machine is called Remote and running Centos 5. 

I'm trying to setup an automatic copy of a file from Remote to Local. I've done the ssh-keygen and all the necessary setup so that it does scp copying a log file from Remote to Local without asking me for password and passphrase. All this from my Local login as bash user.

The problem is when I set up a cronjob, it just doens't work. Nothing happens. I've tried a simple test file and ran a cronjob 0 10 * * * /usr/bin/scp user@remote:/home/user/simpletestfile /home/user/

Let's say at 10 am, I checked the process, the cronjob seems to run it, but doesn't execute the command line. I tried it as a script, even placed my entire environment into the script, I've changed the crontab environment to /bin/bash - all these didn't work.

All the work, running the script or the command above works perfectly and without asking me for password or passphrase.

I've never faced a problem betwen redhat or centos machines. But this is the first time between different distros and between ubuntu and centos.

Very puzzling, any hints is much appreciated.

thanks,
k

---

