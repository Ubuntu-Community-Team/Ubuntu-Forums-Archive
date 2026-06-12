---
title: "Flash 10 on x64 only as root"
date: 2009-11-07
forum: General Help
---

### Post by bcrazynutter on 2009-11-07
Can somebody please help, I am running Flash 10 alpha on Ubuntu 9.10 x64 but it only works when I run Firefox with sudo or as root. If I run as a user and go to BBC Iplayer (as an example) Firefox closes. The error message I get in a terminal is 'Segmentation fault'.

I have been working on this all day to no avail, I can't be the only one who has had this problem.

Thanks in advance

---

### Post by ElSlunko on 2009-11-07
I also have this issue but mine is on launch. I suppose my homepage has flash on it.

---

### Post by unamanic on 2009-11-07
It won't tell you the cause, but I find that for 64bit distributions it's best to use the 64bit plugin from Adobe Labs  [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

-Go to Adobe Labs and click the Download 64-bit Plugin for Linux link
-Go to the location (usually on your desktop or Downloads folder)
-Right click on the libflashplayer tar.gz file and select extract here
-Select libflashplayer.so file and copy it
-Go to your home directory and turn on hidden files (ususally an option under view)
-Navigate to the .mozilla folder then the plugins folder
-Paste the file here
-Restart firefox and you&#8217;re done

ref: [http://unamanic.witt-family.net/aboutplugins/](http://unamanic.witt-family.net/aboutplugins/)

---

### Post by bcrazynutter on 2009-11-08
That's what I have done, hence running Flash 10 alpha. But still can only use as root, not as user because it causes Mozilla to crash

---

### Post by unamanic on 2009-11-08
First, if you've run firefox with sudo, you should ensure that the permissions of .mozilla folder haven't been effected, so reset them back (sudo has reset permissions on my config files in the past):
```

sudo chown -R  [username]:[username] /home/[username]/.mozilla
sudo chmod -R o+rw /home/[username]/.mozilla

```

If that doesn't work, create a new user on the machine and see if it works for them.

---

### Post by ElSlunko on 2009-11-08
Creating a new user fixed FF for that person but it's still broken for my main account. I'm going to try to copy the .mozilla from my temp user and see if that works.

---

