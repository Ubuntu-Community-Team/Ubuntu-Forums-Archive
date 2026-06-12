---
title: "Custom init script problem"
date: 2010-06-08
forum: General Help
---

### Post by bbgarber on 2010-06-08
So I created a script to start my jungledisk service, "jdd.sh" and then created a symlink to it in the init.d/ directory. Then I ran the command "sudo update-rc.d jdd defaults 98 02" which appeared to create the appropriate links in the rc?.d directories. However, jungledisk will not run on startup.

I noticed that the links in the rc?.d directories belong to root:root, and I cannot change that.

The jdd.sh script works a-ok when I run it in the shell as "user". What can I try next? 

Thanks,
Brian

---

### Post by Brandon Williams on 2010-06-09
Does the script rely on anything that would only be part of the environment when you run as yourself? For example, is it looking for any files that are in your home directory using '~' or $HOME as part of the path?

One way to debug the script for use as a startup script is to run it as root. Use 'sudo -i' to get to a root prompt and then run run '/etc/init.d/jdd.sh start'. Does it work? If not, what are the errors it displays?

---

### Post by bbgarber on 2010-06-10
Thanks for your reply! 

I do have the script in /home/user/, so that may be my problem? By the way I do have a symlink to that script in the /etc/init.d/ directory.

So when I ran the /etc/init.d/jdd start as root (sudo -i), it worked, with no error messages and I can see the contents of the jungledisk directory. But if I exit as root user, I cannot see the contents of the same directory.

Where is the best place to put scripts like this?

Thanks again,
Brian

---

### Post by Brandon Williams on 2010-06-16
I don't think this one is about where the script is located. It sounds like the script is doing something that must be done as a regular user in order for the directory to be accessible by a regular user. When you run the script as root, keep that terminal open with the root session still running and then, in a different terminal, check whether you can view the contents of the directory as a regular user.

---

### Post by bbgarber on 2010-06-19
Nope, you're right, I cannot access the directory as a regular user. This is even after invoking the "allow_other" option.

Is there a way to fix this?

Thanks,
Brian

---

### Post by Brandon Williams on 2010-06-28
Sorry for the delay ... I was hoping that someone familiar with jungledisk might respond.

My best suggestion is to use sudo in your init.d script in order to start the service as if you were starting it as the regular user. That way, at least the one user will be able to access the resources. If you need multiple users to be able to access the service, then you'll need a response from someone more familiar with jungledisk.

---

### Post by bbgarber on 2010-06-28
Hey Brandon, no worries.

I finally resolved this issue with help from the Jungledisk support group. It was actually a very convoluted process! 

After giving up on first the rc?.d approach JD support advised me to change fstab and mount it there. That would work when I ran 'sudo mount -a' after the machine was booted, but during a reboot it would hang on that entry in fstab since eth0 was not yet configured. 

Next I added a 'noauto' option in the fstab command. Finally I created a simple shell script (mountjd.sh) that ran ```
mount /media/jungledisk
``` and then re-ran the ```
sudo update-rc.d mountjd defaults 98 02
``` command.

This is finally working for me!

---

