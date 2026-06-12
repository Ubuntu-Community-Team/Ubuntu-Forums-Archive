---
title: "Can't ssh into ubuntu machine?"
date: 2011-02-06
forum: General Help
---

### Post by HimeNoHogosha on 2011-02-06
I am running 10.10, and tried to follow [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") to get the ssh server running. The only change I made to the default config file was to enable verbose logging and to disable password authentication. 

Then I tried using putty on my windows machine to ssh in. I am able to get a login prompt, but after I type in my username putty gives me a "Disconnected : No supported authentication methods available."

Here are the log messages. I stopped the server, started it again, and attempted a login with putty:

```
$ sudo /etc/init.d/ssh stop
 * Stopping OpenBSD Secure Shell server sshd                                                                                                                                                                                           [ OK ] 

$ sudo /etc/init.d/ssh status
 * could not access PID file for sshd

$ tail /var/log/auth.log
Feb  6 10:52:47 hnh-nas sudo:    jesse : TTY=pts/0 ; PWD=/home/jesse ; USER=root ; COMMAND=/etc/init.d/ssh stop
Feb  6 10:52:48 hnh-nas sshd[3422]: Received signal 15; terminating.
Feb  6 10:52:56 hnh-nas sudo:    jesse : TTY=pts/0 ; PWD=/home/jesse ; USER=root ; COMMAND=/etc/init.d/ssh status

$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server sshd                                                                                                                                                                                           [ OK ] 

$ sudo /etc/init.d/ssh status
 * sshd is running

$ tail /var/log/auth.log
Feb  6 10:52:47 hnh-nas sudo:    jesse : TTY=pts/0 ; PWD=/home/jesse ; USER=root ; COMMAND=/etc/init.d/ssh stop
Feb  6 10:52:48 hnh-nas sshd[3422]: Received signal 15; terminating.
Feb  6 10:52:56 hnh-nas sudo:    jesse : TTY=pts/0 ; PWD=/home/jesse ; USER=root ; COMMAND=/etc/init.d/ssh status
Feb  6 10:58:25 hnh-nas sudo:    jesse : TTY=pts/0 ; PWD=/home/jesse ; USER=root ; COMMAND=/etc/init.d/ssh start
Feb  6 10:58:25 hnh-nas sshd[3569]: Set /proc/self/oom_adj from 0 to -17
Feb  6 10:58:25 hnh-nas sshd[3569]: Server listening on 0.0.0.0 port 22.
Feb  6 10:58:25 hnh-nas sshd[3569]: Server listening on :: port 22.
Feb  6 10:58:29 hnh-nas sudo:    jesse : TTY=pts/0 ; PWD=/home/jesse ; USER=root ; COMMAND=/etc/init.d/ssh status

$ tail /var/log/auth.log
Feb  6 10:52:47 hnh-nas sudo:    jesse : TTY=pts/0 ; PWD=/home/jesse ; USER=root ; COMMAND=/etc/init.d/ssh stop
Feb  6 10:52:48 hnh-nas sshd[3422]: Received signal 15; terminating.
Feb  6 10:52:56 hnh-nas sudo:    jesse : TTY=pts/0 ; PWD=/home/jesse ; USER=root ; COMMAND=/etc/init.d/ssh status
Feb  6 10:58:25 hnh-nas sudo:    jesse : TTY=pts/0 ; PWD=/home/jesse ; USER=root ; COMMAND=/etc/init.d/ssh start
Feb  6 10:58:25 hnh-nas sshd[3569]: Set /proc/self/oom_adj from 0 to -17
Feb  6 10:58:25 hnh-nas sshd[3569]: Server listening on 0.0.0.0 port 22.
Feb  6 10:58:25 hnh-nas sshd[3569]: Server listening on :: port 22.
Feb  6 10:58:29 hnh-nas sudo:    jesse : TTY=pts/0 ; PWD=/home/jesse ; USER=root ; COMMAND=/etc/init.d/ssh status
Feb  6 10:58:55 hnh-nas sshd[3580]: Set /proc/self/oom_adj to 0
Feb  6 10:58:55 hnh-nas sshd[3580]: Connection from 192.168.200.64 port 2634

$
```

---

### Post by stlsaint on 2011-02-06
Sooooo since you turned off password authentication....what method to authenticate are you using?? The best method would be to use encryption keys but first you must enable password authentication to be able to setup keys.

---

### Post by efflandt on 2011-02-06
If you were properly using keys, you should not even get a terminal login prompt.  You should only get prompted for the pass phrase for your key (although, in Ubuntu X the gui prompt for your pass phrase might appear to be a password prompt).  If you generate a key in Linux, PuTTY has a utility to convert that to a key it can use.

In Ubuntu make sure that your ~/.ssh/ directory is 700 permission and any files in it have 600 permission.

---

### Post by HimeNoHogosha on 2011-02-06
Wow total rookie mistake. As you mentioned, I didn't even set up keys properly. I guess the page I should have also checked was [https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"). The main thing I didn't understand at first was the need for a private key on my client machine, and a public key on the server. 

Since I'm using a windows machine to log into ubuntu, I was using putty, and so this page was very helpful as well [http://www.howtoforge.com/ssh_key_based_logins_putty]("http://www.howtoforge.com/ssh_key_based_logins_putty"). Once I generated the keys and copied things into the right places, everything worked smoothly. 

Thanks!

---

