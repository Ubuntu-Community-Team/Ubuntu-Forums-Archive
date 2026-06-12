---
title: "running a shell script as root from inside another script"
date: 2012-09-04
forum: General Help
---

### Post by cheerPuncH on 2012-09-04
Hi,

I designed a plugin for our machine at work. The requirements for the plugin were it had to have a 'launch.sh' file and a file that would do the work (most the time it would be a perl or python script). The plugin works great, but the resulting file of the plugin needs to be moved to a shared windows server.

For that I've written the following.
```
#!/bin/bash

mount -t cifs //server/share /mnt -o user=domain/user,password=pass
cp /file /mnt/destination
unmount.cifs /mnt
```

I decided to attach the code above at the end of launch.sh to move the resulting file from the plugin to windows, but it gave me permission errors. Only 'mount' can be used with the root user.

So, I created a separate file called 'mount' with the code above in it and placed it in /usr/local/bin and gave it the permissions chmod 755.
At the bottom of 'launch.sh' I inserted the line...
```
sudo -u ionadmin mount
```

The error I get this time, isn't about permission issues it is...
```
sudo: no tty present and no askpass program specified
```

I realize this means that I didn't provide a password and therefore it couldn't do anything. I didn't mention this earlier, but the reason this process is so important is because the entire pipeline needs to be automated. (I can't run scripts as data comes off the machine...one input, one output)

I started to do some research on 'sudoers'. I'm not sure if I took this in the right direction, but I went into the sudoer file /etc/sudoers (using visudo) and wrote at the bottom ...
```
admin ALL=(ALL) NOPASSWD: /usr/local/bin/mount
```

I re-ran the script and ...
```
sudo: no tty present and no askpass program specified
``` the same error.

How can I automate this process? More specifically, how can I run mount as a root user within launch.sh?

Thanks in advance.

---

### Post by drmrgd on 2012-09-04
Another Ion Torrent user...nice!

I don't know if this will specifically help or not, but have a look at the code for the new Ion Cloud Plugin.  I think their strategy is to input the password as a variable in the parameters when you launch the plugin.  That password can then be passed to the script from there.  I really don't know if there's a better, more secure way of doing it, but maybe that's a start?

---

### Post by cheerPuncH on 2012-09-05
Thanks for responding drmrgd!

It looks like the easiest way to do this is mount from fstab 'noauto' and set 'users' in the options. This way anyone can mount and unmount.

---

