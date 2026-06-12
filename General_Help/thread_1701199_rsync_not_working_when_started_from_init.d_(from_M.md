---
title: "rsync not working when started from init.d (from Motion)"
date: 2011-03-06
forum: General Help
---

### Post by Fynn on 2011-03-06
Hi, and thanks in advance for your help.

Any idea why Motion can sucessfully call rsync when started by typing **#motion start**, but not when typing **#/etc/init.d/motion start**.  

(It will start from init.d, but can't seem to start rsync).

---

### Post by Fynn on 2011-03-07
*bump*

I guess that it's because the motion daemon runs as **motion**, does rsync have to run as root?

Any ideas?

---

### Post by dining_philosopher on 2012-03-31
Hello!

I suffered from similar problem. Rsync doesn't work because it expects you to enter login and password (if you're syncing by ssh). In order to allow syncing without entering password you should tell it to your ssh:

```
# ssh-keygen
# ssh-copy-id -i /home/[username]/.ssh/id_rsa.pub [remote_user]@[remote_ip]
```

(and enter to any questions).

However, if motion is started as daemon, it is executed from user "motion" rather than your user or root. Moreover, this user has no home directory and user preferences, so you cannot neither do "su motion", nor save ssh keys in its home. But there is solution:

```
sudo mkdir /home/motion
sudo chown motion /home/motion
cd /home/motion
sudo -u motion /bin/sh           # so you are logged in as motion now
ssh-keygen
ssh-copy-id -i /home/motion/.ssh/id_rsa.pub [remote_user]@[remote_ip]
```

So motion will be able to invoke ssh actions without password.

Also do not forget that you can always check what is going on. For instance, to ensure that motion is executing commands on events you may ask it to write some string into file:

```
on_movie_start echo "Annuit coeptis\n" >> /home/motion/log.txt
```

Or even you may find out what exactly is %f:

```
on_movie_start echo "%f\n" >> /home/motion/log.txt
```

Rsync (at least in debian) itself writes diagnostic messages in /var/mail/username, but if it does not, you can get its output in similar way:

```
on_movie_end rsync -v %f mason@192.168.1.111:%f 2> rsynclog.txt
```

-v is for verbose, 2> redirects stderr.



But there is more simple (and reliable) way to sync your video requiring no operations with motion at all. You just add rsync to your crontab:

```
crontab -e     # no sudo!!
```

and in crontab file:


```
*/1 * * * * rsync -rl ~/video mason@192.168.1.111:~/
```

Or, for instance, */3 if you want to synchronize every 3 minutes. All you have to do is generate ssh key (as above) and enjoy. This way has at least two benefits - first, you get long movies synced "in situ", and second, if internet connection is lost for some time, you can be sure that all movies recorded during this time will be synced at reconnection.

P. S. And never forget about user rights!!

---

