---
title: "Script setuid question"
date: 2011-06-30
forum: General Help
---

### Post by Davii on 2011-06-30
OK, so I'm sort of new to Linux, and trying my hand at a few scripts. I've read info >[here]("http://bashshell.net/shell-scripts/forcing-scripts-to-run-as-root/")< about checking for root permissions, and info >[here]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html")< about the setuid bit. My understanding is that the following should work... but it doesn't! Please would someone be generous enough to suggest why?!

```

~/tmp$ cat test
  #!/bin/bash
  echo $EUID
  if [[ $EUID -ne 0 ]]; then echo "Not root!" 1>&2; exit 1; fi
  exit 0
~/tmp$ sudo chown root:root test
~/tmp$ sudo chmod 755 test
~/tmp$ sudo chmod u+s test
~/tmp$ ls -al test
  -rwsr-xr-x 1 root root 91 2011-06-30 12:26 test
~/tmp$ ./test
  1000
  Not root!
~/tmp$ 

```

My understanding is that $EUID should be the effective user id of the script, and that the u+s should set the setuid bit, which should make the script run as root no matter who initiates it. I have tried making the script do things that require root privileges eg:
```
cp /etc/hosts /etc/hosts.old.$(date +%Y%m%d)
```
which fails with
```
cp: cannot create regular file `/etc/hosts.old.20110630': Permission denied
```
So I'm inclined to believe there's a problem with the setuid part, but I know that it works on my system - because sudo has no problems running.
```
~/tmp$ ls -al /usr/bin/sudo
-rwsr-xr-x 2 root root 144508 2011-05-30 06:51 /usr/bin/sudo

```

Please would someone shed some light on where I'm going wrong?

---

### Post by blueridgedog on 2011-06-30
Take a look here, especially the reply:

[https://answers.launchpad.net/ubuntu/+question/9920](https://answers.launchpad.net/ubuntu/+question/9920)

You may need to compile the script, as I suspect the OS is ignoring the setuid of the shell script for security reasons.

---

### Post by Davii on 2011-06-30
Thank you - it's been driving me mad for hours!

Looks like there are a few options, but from what I can see, none of them is going to be as secure as sudo, so I guess I'll cope with typing my password for the moment, and hope I don't actually need a script to do this in future.

---

