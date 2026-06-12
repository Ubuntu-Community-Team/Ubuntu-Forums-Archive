---
title: "Ongoing windows decorator issue"
date: 2012-03-18
forum: General Help
---

### Post by kkelly77 on 2012-03-18
I had a problem that was kind of solved about a week ago ([http://ubuntuforums.org/showthread.php?t=1936221&highlight=docky](http://ubuntuforums.org/showthread.php?t=1936221&highlight=docky)  )

However, every time I boot up my laptop, I have to enter the following code in Terminal just so I can get my min, max and close buttons

```
 compiz --replace & 
```This gives me the following output

```
[1] 1624 
 laptop@laptop:~$ libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory 
 Couldn't find a perfect decorator match; trying all decorators 
 Found no decorator to start
  
```This will give me back my control buttons but not on all windows, VLC for example, they are still missing. 

My system seems to have both Compiz and Metacity on it. Could these be conflicting? BTW, this problem started when I installed/uninstalled Docky.

---

### Post by kkelly77 on 2012-03-18
```
sudo apt-get install --reinstall compiz
```

This appears to have resolved the problem with Firefox, 'Places' windows etc. However, VLC is still missing the min max and close buttons.

---

