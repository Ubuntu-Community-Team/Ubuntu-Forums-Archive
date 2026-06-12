---
title: "sudo chmod: Operation not permitted"
date: 2010-09-16
forum: General Help
---

### Post by klausner on 2010-09-16
Trying to change permissions on a file in /proc/sys/fs/inotify. The command syntax are:
```
sudo chmod u+w max_user_watches
```
and the result is:
```
chmod: changing permissions of `max_user_watches': Operation not permitted
```

Also tried to change it when logged in as root, same results.

Parent directory permissions are dr-xr-xr-x, and are the same up the chain. Tried to change the directory permissions to u+w, that didn't work either.

FWIW, /proc is part of the / partition, and it has ~600MB free space.

How can root *not* be allowed to change permissions?

---

### Post by harrismh777 on 2010-09-17
BE CAREFUL and try this:

   sudo su -

... give it your password and you will be root (with full authority).

Now, change directory into /proc and knock your socks off... just don't shoot yourself in the foot. I'm not responsible.

There are some things in /proc that you should not touch, and frankly, the kernel may prevent you ...   

Which file(s) are you trying to change?

---

### Post by klausner on 2010-09-17
> **harrismh777 said:**
> BE CAREFUL and try this:

   sudo su -

... give it your password and you will be root (with full authority).

Now, change directory into /proc and knock your socks off... just don't shoot yourself in the foot. I'm not responsible.

There are some things in /proc that you should not touch, and frankly, the kernel may prevent you ...   

Which file(s) are you trying to change?

I already tried it as root, and get the same error. The file I'm trying to change is the one I specified in the first message.

---

### Post by CharlesA on 2010-09-17
Try using either "o" for owner, "g" for group, or "a" for all.

What are you trying to do?

Er nevermind, I just tried chmod 777 and it spit back the same error.

Check [here]("http://forums.debian.net/viewtopic.php?f=5&t=46494") for some info on /proc.

---

### Post by sisco311 on 2010-09-17
Why do you want to change the permissions of the file?

---

### Post by klausner on 2010-09-17
> **CharlesA said:**
> Try using either "o" for owner, "g" for group, or "a" for all.

Uh, wrong. "o" is for Other. Valid arguments are ugoa. See "man chmod."

---

### Post by klausner on 2010-09-17
> **sisco311 said:**
> Why do you want to change the permissions of the file?
Uh, so I can change it?

---

### Post by klausner on 2010-09-17
> **CharlesA said:**
> Check [here]("http://forums.debian.net/viewtopic.php?f=5&t=46494") for some info on /proc.

If this is true, then I'm screwed. I'm trying to use Beagle, and getting errors. Their troubleshooting file says to change the file in /proc. So either they are wrong, or the article you linked to is.

---

### Post by sisco311 on 2010-09-17
> **klausner said:**
> If this is true, then I'm screwed. I'm trying to use Beagle, and getting errors. Their troubleshooting file says to change the file in /proc. So either they are wrong, or the article you linked to is.

Do you have to change the file permissions or increase the number of inotify watches available on your system?

---

### Post by klausner on 2010-09-17
> **sisco311 said:**
> Do you have to change the file permissions or increase the number of inotify watches available on your system?

The instructions on the Beagle site say to increase the number of inotify watches by changing the file. From their site:
> ...you will need to increase the number of inotify watches available on your system.

...

The default number of watches is 8192. 16384 is a good value for most people, and 32768 is probably more than enough. Using additional watches does increase the amount of memory used inside the kernel, but increasing the number does not affect the amount of memory if they aren't used.

To change the limit:

```
# echo 16384 > /proc/sys/fs/inotify/max_user_watches
```

---

### Post by sisco311 on 2010-09-17
> **klausner said:**
> The instructions on the Beagle site say to increase the number of inotify watches by changing the file. From their site:

Well, in Maverick, the default number of watches is 524288. So, first check out if the value is high enough:
```
sysctl fs.inotify.max_user_watches
```
If not, then change it:
```
sudo sysctl fs.inotify.max_user_watches=524288
```

To make the changes permanent, edit the /etc/sysctl.d/30-nepomuk-inotify-limit.conf file (create it if doesn't exist), to look like this:
```
fs.inotify.max_user_watches = 524288
```

---

### Post by klausner on 2010-09-17
> **sisco311 said:**
> Well, in Maverick, the default number of watches is 524288. So, first check out if the value is high enough:
```
sysctl fs.inotify.max_user_watches
```
If not, then change it:
```
sudo sysctl fs.inotify.max_user_watches=524288
```

To make the changes permanent, edit the /etc/sysctl.d/30-nepomuk-inotify-limit.conf file (create it if doesn't exist), to look like this:
```
fs.inotify.max_user_watches = 524288
```

That seems to work! The number of watches was 16384, so I only changed it to 32768.

Thanks.

---

### Post by harrismh777 on 2010-09-18
Have you tried Beagle configs?

---

