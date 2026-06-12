---
title: "Lockout Root, Lockout Sudo"
date: 2012-02-01
forum: General Help
---

### Post by bambuntu on 2012-02-01
I'm remastering a distro intended to be run live.  I want it to lock out all root privileges.  No root sign in.  No sudo elevated privileges.  Period.  It's intended just to run live as a non-root user.  Happliy, an Atheist Distro, one without the god Root.

So, far I've attempted to remove the god this way:

sudo rm /usr/bin/sudo

If I delete the sudo, it seems to take care of the problem.  But someone mentioned to me that he could just download the god to the computer and all would be the same again.  Is this second coming true?  I have an example that follows that seems to say the opposite.

```
artist@artist ~ $ sudo mv /usr/bin/sudo /home/artist
[sudo] password for artist: 
artist@artist ~ $ sudo su
bash: /usr/bin/sudo: No such file or directory
artist@artist ~ $ ls
Desktop  Documents  Downloads  Linux Kreator.torrent  Music  Pictures  Public  sudo  Templates  tor-browser_en-US  torrenttext  Videos
artist@artist ~ $ sudo mv sudo /usr/bin/
bash: /usr/bin/sudo: No such file or directory
artist@artist ~ $ 
```*I originally started this discussion on Ask Ubuntu, but sadly I can't finish the discussion because I hate AU's forum editors (small editing boxes and mini-markdown) and now refuse to participate there, although great people.*

---

### Post by Grenage on 2012-02-02
Hi there,

Is there some reason you can't just modify the /etc/sudoers file?

---

### Post by rgubele on 2012-02-02
> **bambuntu said:**
> 
So, far I've attempted to remove the god this way:

sudo rm /usr/bin/sudo

If I delete the sudo, it seems to take care of the problem.

sudo is not the only way to elevate privileges.

> But someone mentioned to me that he could just download the god to the computer and all would be the same again.Someone is mistaken. sudo gains root privileges because it is setuid root. A normal user can set the setuid bit, but they can't change the owner of a file.

> Is this second coming true?  I have an example that follows that seems to say the opposite.

```
artist@artist ~ $ sudo mv /usr/bin/sudo /home/artist
[sudo] password for artist: 
artist@artist ~ $ sudo su
bash: /usr/bin/sudo: No such file or directory
artist@artist ~ $ ls
Desktop  Documents  Downloads  Linux Kreator.torrent  Music  Pictures  Public  sudo  Templates  tor-browser_en-US  torrenttext  Videos
artist@artist ~ $ sudo mv sudo /usr/bin/
bash: /usr/bin/sudo: No such file or directory
artist@artist ~ $ 
```*I originally started this discussion on Ask Ubuntu, but sadly I can't finish the discussion because I hate AU's forum editors (small editing boxes and mini-markdown) and now refuse to participate there, although great people.*Actually, in your example, moving the binary maintains the ownership and the permissions. The reason you are getting the error is because you are not calling the binary, as sudo is no longer in your path. If you were to simply call it with a full path, ie.:

```
./sudo
# or
/home/artist/sudo
```or even just add it back into your path:

```
export PATH=$PATH:.
#or
export PATH=$PATH:/home/artist/
```...you could still elevate.

```

~$ ls -alh `which sudo`
-rwsr-xr-x 2 root root 165K 2011-09-11 12:09 /usr/bin/sudo
~$ cp `which sudo` .
~$ ./sudo id
sudo: must be setuid root
~$ chmod u+s sudo
~$ ./sudo
sudo: must be setuid root
~$ ls -alh | grep sudo
-rwsr-xr-x   1 ryan ryan 165K 2012-02-02 05:10 sudo
-rw-r--r--   1 ryan ryan    0 2011-06-06 22:21 .sudo_as_admin_successful
~$ chown root sudo
chown: changing ownership of `sudo': Operation not permitted
~$ sudo chown root sudo
~$ ./sudo id
sudo: must be setuid root
~$ ls -alh | grep sudo
-rwxr-xr-x   1 root ryan 165K 2012-02-02 05:10 sudo
-rw-r--r--   1 ryan ryan    0 2011-06-06 22:21 .sudo_as_admin_successful
~$ chmod u+s sudo
chmod: changing permissions of `sudo': Operation not permitted
~$ sudo chmod u+s sudo
~$ ./sudo id
uid=0(root) gid=0(root) groups=0(root)
~$ ls -alh | grep sudo
-rwsr-xr-x   1 root ryan 165K 2012-02-02 05:10 sudo
-rw-r--r--   1 ryan ryan    0 2011-06-06 22:21 .sudo_as_admin_successful
~$ sudo rm sudo
~$ sudo cp -a `which sudo` .
~$ ls -alh | grep sudo
-rwsr-xr-x   1 root root 165K 2011-09-11 12:09 sudo
-rw-r--r--   1 ryan ryan    0 2011-06-06 22:21 .sudo_as_admin_successful
~$ ./sudo id
uid=0(root) gid=0(root) groups=0(root)
~$ sudo rm sudo
~$
~$ sudo mv `which sudo` .
~$ sudo id
bash: /usr/bin/sudo: No such file or directory
~$ ./sudo id
uid=0(root) gid=0(root) groups=0(root)
~$ ./sudo mv sudo /usr/bin/sudo
~$ sudo id
uid=0(root) gid=0(root) groups=0(root)
~$ which sudo
/usr/bin/sudo
~$ 

```If simply downloading sudo allowed you to gain root, then any user could simply download a modified sudo that didn't do authentication (ie., ask for a password). That would hardly be good.

---

