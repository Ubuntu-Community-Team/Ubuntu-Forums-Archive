---
title: "Ubuntu Tweak Messed Up apt-get"
date: 2009-09-06
forum: General Help
---

### Post by espmartin on 2009-09-06
Hello All,

When I run apt-get **ANYTHING**, I get the results of the command, but then I get this at the end of the results in Terminal:
> Setting up ubuntu-tweak (0.4.9-0~20090830~karmic1) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
No matter what the apt-get command is, ALWAYS Ubuntu Tweak results show as above.
I **CAN** run Ubuntu Tweak, as it does work. So why do I get this error message?

---

### Post by drs305 on 2009-09-06
Try these in order. Accomplish the next if the previous doesn't work. Each is a separate attempt to correct the problem, ending with an attempted update. If an update works, STOP and do not run the subsequent commands.

```

sudo apt-get purge ubuntu-tweak
sudo apt-get update
___

sudo apt-get install -f
sudo apt-get update
___

dpkg --configure ubuntu-tweak
sudo apt-get update
___

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update

```

If one of these sets don't solve it, you can get a bit more aggressive. You have already backed up the status file to status.bad. Now you will remove the ubuntu-tweak information.

```

gksudo gedit /var/lib/dpkg/status

```
Find the entry for ubuntu-tweak. It will start with:
> "Package: ubuntu-tweak"
*and end with*
"Homepage: http://ubuntu-tweak.com"
Delete the entire section, save the file, and then run the update command again. You can also then try to reinstall ubuntu-tweak if you wish.


Added: *Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance. * And tell us how you fixed it.

---

### Post by espmartin on 2009-09-06
Thanks for the tips! Here's what I got:
```

sudo apt-get purge ubuntu-tweak
sudo apt-get update

```Same problem
___
```

sudo apt-get install -f
sudo apt-get update

```Same problem
___
```

dpkg --configure ubuntu-tweak
sudo apt-get update

```Same problem
___
 ```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status-old
sudo apt-get update

```Now I get this when running apt-get:
> Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
```

gksudo gedit /var/lib/dpkg/status

```This opens an empty file...

---

### Post by drs305 on 2009-09-06
Sorry for the typo:
```

sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update

```

Then continue if it doesn't work. I'll correct the original. 

The reason it came up empty is because there wasn't a /var/lib/dpkg/status file. If you get an error message because you have saved the empty one, delete it before running the above.

---

### Post by espmartin on 2009-09-06
I also get this in my Panel's Status Area:
[IMG]http://fiercestreetnetworks.com/images/update-error.png[/IMG]

---

### Post by espmartin on 2009-09-06
Thanks! So I removed that section from the file. Do I need to restart X?

---

### Post by espmartin on 2009-09-06
You ROCK [drs305]("http://ubuntuforums.org/member.php?u=223945")!!! Thanks. Fixed via your instructions above.

---

### Post by drs305 on 2009-09-06
> **espmartin said:**
> Thanks! So I removed that section from the file. Do I need to restart X?


No, just running the apt-get update command would be sufficient.

---

