---
title: "Configure rssh Chroot Jail To Lock Users To Their Home Directories Only"
date: 2011-12-16
forum: General Help
---

### Post by bigoten on 2011-12-16
I have a home server running Ubuntu 9.04.
I want to configure rssh chroot jail to lock users to their home directories. I found a couples of guides online.
[http://www.cyberciti.biz/tips/howto-linux-unix-rssh-chroot-jail-setup.html](http://www.cyberciti.biz/tips/howto-linux-unix-rssh-chroot-jail-setup.html)
and
[http://www.cyberciti.biz/tips/linux-unix-restrict-shell-access-with-rssh.html](http://www.cyberciti.biz/tips/linux-unix-restrict-shell-access-with-rssh.html)
seem to explain everything that is needed. I followed all steps (or so I think).
Eventually I tested the system using an ftp client (FireFTP extension in Firefox). But the user I created continues not being jailed in his own home directory, he can basically surf through all the files in the server.

Can anyone show me a possibly different way to achieve what I am trying to do? I don't know what else to try now.

Thanks!
bigoten

---

### Post by Lars Noodén on 2011-12-16
> **bigoten said:**
> Can anyone show me a possibly different way to achieve what I am trying to do? I don't know what else to try now.

You can do what you need to using OpenSSH-server.  The snippet from [/etc/ssh/sshd_config](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) assumes there is a group **sftponly** and that the restricted accounts are members of it.

```

Subsystem sftp internal-sftp

Match Group sftponly
        ChrootDirectory /home
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

The chroot directory is [font=Courier New]/home[/font] instead of the users' home directories because the chroot directory must be owned by root and not writable by anyone else.

---

### Post by bigoten on 2011-12-16
Hi Lars,
thanks for the reply.
I opened /etc/ssh/sshd_config as you suggested. I did not know where precisely to change the code as you said, so I just added it at the end of the file (I changed ChrootDirectory to /users, to meet my settings).
Then I created a user's group called sftponly, and I added a guest user to it.
And still, the problem remains: guest is not jailed in /users...

What do you think?
Thanks,
bigoten

---

### Post by Lars Noodén on 2011-12-16
Did you reload/restart sshd for the new configuration to take effect?

---

### Post by bigoten on 2011-12-17
Hi Lars,
I tried restarting sshd the usual way (/etc/init.d/ssh restart), but it gave an error. So I decided to reboot the server. After reboot I couldn't access the server. After some time I figured it out: I had to comment out the command 
Subsystem sftp /usr/lib/openssh/sftp-server
so that your code could work properly.
Now restarting the sshd worked, and guest is indeed jailed in /users.
Thanks!, you helped me a lot!

I have some more questions.

1. sftp'ing guest to the server puts him in the chroot defined by me (/users). This is fine, but I wonder how to make guest login directly in, say, /users/guest home folder, with no possibility of accessing files in the parent directory (like /users/bin, /users/etc and so on)?

2. In my prior attempt to make this work I was editing /etc/rssh.conf (I tried adding exception lines for guest user...). Is it fine now that I just reset that file to default configuration?

3. I don't want guest to ssh into the server (I don't want him to have shell control). With my prior setting using rssh.conf I had this working: issuing the command
ssh guest@192.168.1.5
would give an immediate message stating that guest was not allowed in.
With my current setup that you suggested, issuing 
ssh guest@192.168.1.5
leaves the terminal blank, kind of non-responsive. Typing exit logs guest out. So, was guest logged in? I don't want this, guest is supposed to use sftp only to enter. Can you suggest something?

4. Finally, how can I set home folder /users/guest read-only for guest? Guest is only supposed to pick up some files from the server, nothing more.

Thanks again,
bigoten

---

### Post by Lars Noodén on 2011-12-17
> **bigoten said:**
> 
1. sftp'ing guest to the server puts him in the chroot defined by me (/users). This is fine, but I wonder how to make guest login directly in, say, /users/guest home folder, with no possibility of accessing files in the parent directory (like /users/bin, /users/etc and so on)?


You can set the ChrootDirectory directive to whatever you want, as long as that directory is owned by root and not writable by anyone else.

> **bigoten said:**
> 
2. In my prior attempt to make this work I was editing /etc/rssh.conf (I tried adding exception lines for guest user...). Is it fine now that I just reset that file to default configuration?


If you have OpenSSH running, then you do not need rssh.  It and the configuration files can be removed.

> **bigoten said:**
> 
3. I don't want guest to ssh into the server (I don't want him to have shell control). With my prior setting using rssh.conf I had this working: issuing the command
ssh guest@192.168.1.5
would give an immediate message stating that guest was not allowed in.
With my current setup that you suggested, issuing 
ssh guest@192.168.1.5
leaves the terminal blank, kind of non-responsive. Typing exit logs guest out. So, was guest logged in? I don't want this, guest is supposed to use sftp only to enter. Can you suggest something?


Make sure that group has a forced command:
         ForceCommand internal-sftp

> **bigoten said:**
> 
4. Finally, how can I set home folder /users/guest read-only for guest? Guest is only supposed to pick up some files from the server, nothing more.


You can make it owned by root.

```

sudo chown root.root /users/guest

```

---

### Post by bigoten on 2011-12-18
Thank you! Everything works now as I wanted, no exception.
You were a MAJOR help!:D

---

