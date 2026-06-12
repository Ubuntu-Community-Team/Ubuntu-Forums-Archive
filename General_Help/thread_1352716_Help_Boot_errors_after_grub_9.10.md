---
title: "Help: Boot errors after grub 9.10"
date: 2009-12-11
forum: General Help
---

### Post by ngrieb on 2009-12-11
I just noticed my computer was running a bit slow, so I restarted. After grub and before my login screen I can barely make out an error something to the effect of:

Error can access directory blah... 

It's too fast to read. Is there any kind of boot error log I can use to help me? If so where is it at? Xorg has been consuming ungodly amounts of ram lately as well, so I wouldn't be surprised if it had something to do with this...

Thanks in advance.

---

### Post by Leppie on 2009-12-11
If you remove the quiet and splash options, you can use pause when the error appears.

Otherwise, take a look [here]("http://ubuntuforums.org/showthread.php?t=49925") to enable bootlogd

---

### Post by darco on 2009-12-11
It can be found under Administrator/Log File Viewer/ or in a terminal type:


```
dmesg | more
```



darco

---

### Post by ngrieb on 2009-12-12
Ok, just to be sure...after looking this up. I get rid of the splash screen by editing my grub list?
I did these ^^, but the messages were still too fast, and I didn't get any boot log warning either...?
Now that I am aware of it, I get some errors logging out as well. 
Any other way I can see wtf is going on?

---

### Post by Leppie on 2009-12-12
yes, as darco stated use dmesg.
or otherwise enable bootlogd.

---

### Post by ngrieb on 2009-12-14
dmesg gives me a million and a half entries. What is the best way to tell what is the cause of the problem?

---

