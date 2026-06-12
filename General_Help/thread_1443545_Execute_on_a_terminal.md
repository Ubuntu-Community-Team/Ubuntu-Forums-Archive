---
title: "Execute on a terminal"
date: 2010-03-31
forum: General Help
---

### Post by j_arquimbau on 2010-03-31
Hello!

I've copied a little shell script from the net and when I run it in xfce4-terminal it just works
```
sudo ./script.sh
```
The problem is that this script needs interaction with the user (entering a password) and I want to run it at the startup. I've put it in the /etc/init.d folder, configured the options but I need to know how you can get a terminal to appear at the start up to ask you for the password.

```
#!/bin/bash
	
	echo "1. Enter your password

	oldConfig=`stty -g`
	stty -echo
	read password
	stty $oldConfig

	echo "2. Decrypting ..."

	truecrypt -t /home/custom/.gnupg2 /home/custom/.gnupg --password="$password"  -k "" --protect-hidden=no
```

---

### Post by vzomik on 2010-03-31
here is the answer you want&#65292;but it's in chinese
[http://linuxtoy.org/archives/run-top-automatical-in-tty-after-boot.html](http://linuxtoy.org/archives/run-top-automatical-in-tty-after-boot.html)

---

### Post by j_arquimbau on 2010-03-31
Oh Thank you! It's a pitty I can't speak chinese and that google translator isn't that good...

---

