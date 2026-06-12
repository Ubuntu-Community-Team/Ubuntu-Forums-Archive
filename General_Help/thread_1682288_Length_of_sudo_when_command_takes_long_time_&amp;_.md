---
title: "Length of sudo when command takes long time &amp; wget?"
date: 2011-02-05
forum: General Help
---

### Post by ianc1 on 2011-02-05
I am planning on using wget to download some files at a specific time and then ask the machine to shut down.
I'll use something like:
```
sudo wget http://www.blahblahblah ;; shutdown -h 0
```Now if this takes a while to do will I continually be a super user ie is my machine exposed?

Also will this download continue if my screen lock comes on and what happens if the machine shuts down as the battery runs out or something.

Finally is there anyway to send the machine to sleep and then wake up without a log in to perform this task.

Thanks in advance.

---

### Post by arsenic23 on 2011-02-05
What is going to happen with that command is that your admin privileges will likely expire before the shutdown is run and it will fail.

You could:
```
sudo bash
wget XXX && shutdown -h now
```
BUT 'sudo bash' isn't the greatest practice in general.

Also your file is going to have root as it's owner so you'll have to chown it out when the download is finished.   Screen lock shouldn't interfere but if the machine powers off on it's own you'll be left with a partially downloaded file.  You'll then have to start it up again with something like:
```
wget --tries=0 --retry-connrefused -c http://www.blahblahblah
```

---

### Post by ianc1 on 2011-02-06
Thanks arsenic23.  I was assuming that by the time the shutdown command was reached that the machine would not still require sudo privileges as the sudo command was used to execute the full line of script.

For a relative newbie can you explain why  'sudo bash' isn't the greatest practice?  Is it because the entire time the script is running the machine has root privileges?

Cheers

---

### Post by ianc1 on 2011-03-09
I think I've worked out why sudo bash is not a good idea.

Is it because the bash command opens an interactive bash interpreter and therefore if sudo was used to launch this the all commands entered would have root privileges.  Is this correct?

---

### Post by wojox on 2011-03-09
You need [Cron]("https://help.ubuntu.com/community/CronHowto")

---

### Post by tordeu on 2011-03-09
Yes, that's correct. Every command you would type in would have root privileges. This is considered a bad idea, because you could really do something bad. Having a shell without root privileges and using "sudo" where needed is safer, because this protects you somewhat from accidentally typing in something stupid. Of course, if you type

```

sudo <something stupid>

```then there is no protection whatsoever. But if you are root all the time, the risk of destroying something is a lot bigger.

But this is not necessary anyway, cause as you mentioned yourself: When you call

```

sudo wget ... && shutdown ...

```you're root privileges will not suddenly expire before the shutdown even if the wget takes sometime.

---

