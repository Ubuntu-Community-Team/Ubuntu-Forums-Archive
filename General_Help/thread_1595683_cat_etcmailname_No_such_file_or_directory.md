---
title: "cat: /etc/mailname: No such file or directory"
date: 2010-10-13
forum: General Help
---

### Post by x-shaney-x on 2010-10-13
So been running meerkat for all of 10 minutes and already hit a problem.

Trying to get google earth, install the google-earth package thing but when I try to run it...

```
# sudo make-googleearth-package
cat: /etc/mailname: No such file or directory
Refusing to run as root; use --force to override.
```

---

### Post by TeoBigusGeekus on 2010-10-13
Go to 
[http://www.google.com/earth/index.html]("http://www.google.com/earth/index.html")
Select Download, then Agree and download and save the .bin file somewhere, your Desktop for example.
Open terminal and type
```
cd ~/Desktop
```
to go to your Desktop.
```
chmod +x GoogleEarthLinux.bin
```
to make the file executable.
Finally 
```
./GoogleEarthLinux.bin
```
to run the file.

---

### Post by x-shaney-x on 2010-10-13
Yes but that doesn't solve the underlying problem of why I'm getting the message.

---

### Post by miegiel on 2010-10-22
> **x-shaney-x said:**
> So been running meerkat for all of 10 minutes and already hit a problem.

Trying to get google earth, install the google-earth package thing but when I try to run it...

```
# sudo make-googleearth-package
cat: /etc/mailname: No such file or directory
Refusing to run as root; use --force to override.
```

I'm getting the same error. Did you find a sollution?

Never mind, ```
sudo make-googleearth-package --force
``` did the trick

---

