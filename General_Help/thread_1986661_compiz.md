---
title: "compiz"
date: 2012-05-25
forum: General Help
---

### Post by ahso4271 on 2012-05-25
Hi
how to enable rotating cube:
ctrl/alt/left etc.
and wobbling windows
Thanks

---

### Post by fantab on 2012-05-25
There is plenty of information available on World Wide Web. Linux "attitude" is "I'll do it myself". So please Search, Read, and Understand what you have read.

Try this **[post]("http://ubuntuforums.org/showthread.php?t=1414548")**.

---

### Post by ahso4271 on 2012-05-25
Not working...is that broken with the latest Nvidia?

---

### Post by samitharansara on 2012-05-25
Did you run a compiz test on your hardware?  Google and you will find plenty of 'em mate.  A similar thread is reported here as well.. 

[http://ubuntuforums.org/showthread.php?t=1967419](http://ubuntuforums.org/showthread.php?t=1967419)

[http://askubuntu.com/questions/67538/how-to-enable-unity-3d-on-an-nvidia-quadro-1000m](http://askubuntu.com/questions/67538/how-to-enable-unity-3d-on-an-nvidia-quadro-1000m)

If Unity3D is not supported, you can forcefully enable it by 
```

sudo nano /etc/environment
```

add: 
```

UNITY_FORCE_START=1

```
Save the file with Ctrl+S
reboot

Hope that helps..

---

### Post by ahso4271 on 2012-05-25
No Unity only Gnome 3.4 here. I might have a look but am terribly bored by bugs...

---

### Post by zombifier25 on 2012-05-25
Run this command in the terminal
```
/usr/lib/nux/unity_support_test -p
```
and post the result.

---

### Post by ahso4271 on 2012-05-26
I don't have such...did you read my previous post?

Anyone to confirm that's a 64Bit bug? Or maybe any 12.04 64bit 
Gnome success stories?

---

### Post by stinkeye on 2012-05-26
> **ahso4271 said:**
> I don't have such...did you read my previous post?

Anyone to confirm that's a 64Bit bug? Or maybe any 12.04 64bit 
Gnome success stories?

What desktop environment do you want to run compiz in?
gnome-shell uses mutter as the window manager.

---

### Post by ahso4271 on 2012-05-26
default Gnome 3.4. Probabyl a Nvidia bug? I use the latest driver.

---

### Post by stinkeye on 2012-05-26
I'm on 12.04 64bit with nvidia running compiz.
 
Without Unity, you would need to... 
```
sudo apt-get install gnome-panel
```
to give yourself a classic gnome session to run compiz in.

After install logout and change session.

---

### Post by ahso4271 on 2012-05-26
Yea what the heck do u think I'm using?

---

### Post by stinkeye on 2012-05-26
> **ahso4271 said:**
> Yea what the heck do u think I'm using?
When replying to questions with very limited input I have no idea of your competence or what you are trying to do.
If you have so little patience just do a search and do some reading.
Sorry for trying to help.
Bye.

---

