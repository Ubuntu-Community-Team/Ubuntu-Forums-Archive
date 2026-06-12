---
title: "banshee remote root access"
date: 2012-03-31
forum: General Help
---

### Post by crazymac680 on 2012-03-31
I'm trying to install the banshee remote. It requires me to have root access and to download a file into  /usr/lib/banshee/Extensions. How do I do this?
The file is located 
[http://www.dartmouth.edu/~nstamato/android.html](http://www.dartmouth.edu/~nstamato/android.html)
Thanks for any help
Daniel

---

### Post by crazymac680 on 2012-03-31
I'm managing to enter my password in terminal but I'm still not aloud to drag and drop the file into the correct place. Guessing I need to move it in terminal. Does anyone have any idea what the commands would be?
Thanks
Daniel

---

### Post by HiImTye on 2012-03-31
as per the Banshee extensions page, put them in ```
~/.config/banshee-1/addins
```
[http://banshee.fm/download/extensions/](http://banshee.fm/download/extensions/)

---

### Post by crazymac680 on 2012-04-01
Thanks. I looked at that page but I'm so useless at this that I dont know how to use terminal to move a file from my downloads to that location.
Thanks
Daniel

---

### Post by HiImTye on 2012-04-01
go to your home folder
hit ctrl+H to show hidden files/folders
go to .config
go to banshee-1 (if it doesnt exist go to file>new>folder and make it)
go to addins (same as last step)
place it in here

---

### Post by crazymac680 on 2012-04-01
Thanks but it's still not working. The banshee remote website says I need to put it "  /usr/lib/banshee/Extensions " That location requires root access and says access denied when I try to drag and drop.

---

### Post by crazymac680 on 2012-04-01
The file I need to move is called BansheeRemoteListener.dll and is located on the desktop. I need to move it to                       " /usr/lib/banshee/Extensions " which needs root access.
Any ideas on the command I need to use in Terminal. I've tried to understand the instructions for terminal but it's not making any sense to me.

---

### Post by HiImTye on 2012-04-01
```
sudo cp BansheeRemoteListener.dll  /usr/lib/banshee/Extensions
```

---

### Post by crazymac680 on 2012-04-01
Your my boy blue!!!!!!!
It's working. Thanks so much
Daniel

---

### Post by HiImTye on 2012-04-02
no problem :)

---

