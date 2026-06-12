---
title: "bash help for su -c sudo command needed"
date: 2011-03-31
forum: General Help
---

### Post by karaluh on 2011-03-31
I need to install two packages on a computer, that I don't have direct/remote access to. Also, the user that has those is not a sudoer and I would like him to stay that way. My idea is to prepare precompilled bash script and send it to the user. However both su and sudo do not work well with passwords. The script is:

```
su sudo_user -c "ls" << __eof
sudo_user_password
__eof
```

it outputs "su: musisz uruchamia&#263; z terminala" error, that is I have to run su from terminal. Do you know what's wrong with the script, or perhaps have better idea to accomplish the task?

---

### Post by btindie on 2011-03-31
Why not try
```
$ echo password | sudo -nS ls -l /root
```

-n means not to prompt for the password
-S read password from stdin

---

### Post by karaluh on 2011-03-31
> **btindie said:**
> Why not try
```
$ echo password | sudo -nS ls -l /root
```

-n means not to prompt for the password
-S read password from stdin

Thanks for the answer, that would be the second step. However, user that will be runing the script is not in the sudoers file, so he has to su to the user that is first.

---

### Post by btindie on 2011-04-01
> **karaluh said:**
> Thanks for the answer, that would be the second step. However, user that will be runing the script is not in the sudoers file, so he has to su to the user that is first.
Then use
```
$ sudo -u sudo_user
```You can also test for the uid first then run the script again as root or whoever...
```
if [ $(id -u) -ne 0 ]; then
  sudo "$0" "$@"
  exit $?
fi

# normal code.....

```Or test for the desired user to be run as...
```
if [ $(id -un) != "sudo_user_name" ]; then
  echo password | sudo -u sudo_user_name -nS "$0" "$@"
  exit $?
fi

# normal code now running as "sudo_user_name"
sudo rpm -ivh /tmp/my-package.rpm

```

---

### Post by karaluh on 2011-04-01
> **btindie said:**
> Then use
```
$ sudo -u sudo_user
```

Unfortunately that doesn't work. Non-sudoer canot use sudo to become one.

```
test@host:~$ sudo -u user_with_sudo ls
[sudo] password for test: 
test is not in the sudoers file.  This incident will be reported.
```

---

### Post by btindie on 2011-04-01
I see what you mean, the only other option I can think of would be to add the *normaluser* to /etc/sudoers with limited access requiring him to use the target users password.

sudoers
```
Defaults:normaluser  targetpw

normaluser   ALL=(adminuser)  /usr/bin/sudo
```

As the normaluser you can then do
```
$ sudo -u adminuser sudo whoami
```

---

### Post by karaluh on 2011-04-01
> **btindie said:**
> I see what you mean, the only other option I can think of would be to add the *normaluser* to /etc/sudoers with limited access requiring him to use the target users password.


Sure, but I'd need root access for that, which gets us back to square one. Thanks for trying.

---

