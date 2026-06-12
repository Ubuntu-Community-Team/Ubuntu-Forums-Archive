---
title: "Google earth flash plugin missing..."
date: 2011-07-02
forum: General Help
---

### Post by cacs on 2011-07-02
Hi.
I have a Google earth (last version) running on my natty and it runs pretty well except when I insert a video from youtube it says that flash plugin is missing and offers to download it from adobe. But I have it installed and running on my browsers...
Any ideas?
Ty C.S.

---

### Post by idoitprone on 2011-07-02
enter 

```
about:plugins
```in the navigation bar.

If firefox does not see the flashplayer.. you have to check 

```
/usr/lib/mozilla/plugins/
``` to see that libflashplayer.so exist 

If not then you have to check which type of machine is running 64 bit or 32 bit.
Type ```
uname -a 
```in the terminal
If it is x86_64 then it is 64 bit
other such as i386 or i686 are 32 bit

flash player for the 64 bit machine 
type this in the terminal
```
sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer
```to install flash for the 32 bit
[https://help.ubuntu.com/community/RestrictedFormats/Flash#Ubuntu%209.04%20%28Jaunty%20Jackalope%29%20and%20later]("https://help.ubuntu.com/community/RestrictedFormats/Flash#Ubuntu%209.04%20%28Jaunty%20Jackalope%29%20and%20later")

---

### Post by pqwoerituytrueiwoq on 2011-07-02
google flash aid it makes life easy

---

### Post by cacs on 2011-07-02
> **idoitprone said:**
> enter 

```
about:plugins
```in the navigation bar.

If firefox does not see the flashplayer.. you have to check 

```
/usr/lib/mozilla/plugins/
``` to see that libflashplayer.so exist 

If not then you have to check which type of machine is running 64 bit or 32 bit.
Type ```
uname -a 
```in the terminal
If it is x86_64 then it is 64 bit
other such as i386 or i686 are 32 bit

flash player for the 64 bit machine 
type this in the terminal
```
sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer
```to install flash for the 32 bit
[https://help.ubuntu.com/community/RestrictedFormats/Flash#Ubuntu%209.04%20%28Jaunty%20Jackalope%29%20and%20later](https://help.ubuntu.com/community/RestrictedFormats/Flash#Ubuntu%209.04%20%28Jaunty%20Jackalope%29%20and%20later)

Thank you for your ready answer.
I tried it all... no chance.:(
In the end purged the flash plugin, downloaded it from adobe and installed! My "about: plugins" under the "Shockwave flash" says that are a  libflashplayer.so present, but in the "/usr/lib/mozilla/plugins/" that  is a "flashplugin-alternative.so"... GE still miss the flash player  plugin!

---

### Post by cacs on 2011-07-02
Hi.
I was digging and found the libflashplayer.so in the /usr/lib/adobe-flashplugin/ folder!
So it is there, and FX can play flv's but GE don't! :(
C.S.

---

### Post by idoitprone on 2011-07-02
you should try pqwoerituytrueiwoq's suggestion. If i give commands it will be long and complicated. I will suggest to install flash aid.

[http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)

Edit: ??????????????????// google earth uses flash? or is it google maps?

---

### Post by cacs on 2011-07-03
> **idoitprone said:**
> you should try pqwoerituytrueiwoq's suggestion. If i give commands it will be long and complicated. I will suggest to install flash aid.

[http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)

Edit: ??????????????????// google earth uses flash? or is it google maps?


Thanks I'll try.

---

