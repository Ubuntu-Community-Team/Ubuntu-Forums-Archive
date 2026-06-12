---
title: "nuatilus wont start with gksudo"
date: 2012-01-23
forum: General Help
---

### Post by boregard on 2012-01-23
Hi,I'm having a problem with starting Nautilus with gksudo.When I enter the command to run Nautilus it returns (Syncdaemon not running),see screen shot1 below. Then it comes back with warning about nautilus-gdu extension see screenshot2. Any help would be appreciated.Thanks

---

### Post by bluexrider on 2012-01-23
do you get the same errors using just sudo

---

### Post by boregard on 2012-01-23
> **bluexrider said:**
> do you get the same errors using just sudoyes, when i  just use sudo the same thing happens. also a window opens up showing desktop folder,

---

### Post by bluexrider on 2012-01-23
Here is another thread [http://ubuntuforums.org/showthread.php?t=1384038](http://ubuntuforums.org/showthread.php?t=1384038)

---

### Post by boregard on 2012-01-23
> **bluexrider said:**
> Here is another thread [http://ubuntuforums.org/showthread.php?t=1384038](http://ubuntuforums.org/showthread.php?t=1384038)
after trying that still get same error.

---

### Post by bluexrider on 2012-01-23
Make sure your system is up to date:

Another thread about syncdaemon not running seems an update fixed it
[http://ubuntuforums.org/showthread.php?t=1792640](http://ubuntuforums.org/showthread.php?t=1792640)



```

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tisseskCrok on 2012-01-23
Oops!

---

### Post by boregard on 2012-01-23
> **bluexrider said:**
> Make sure your system is up to date:

Another thread about syncdaemon not running seems an update fixed it
[http://ubuntuforums.org/showthread.php?t=1792640](http://ubuntuforums.org/showthread.php?t=1792640)



```

sudo apt-get update && sudo apt-get upgrade
```
I did that earlier today but I just tried it again and still get same output. Thinking maybe earlier update has caused the problem.

---

### Post by yugnip on 2012-01-23
Interesting. I get the exact same messages, but Nautilus runs as root. So the problem isn't that Nautilus won't run as root, but just an understanding of the output messages? Not sure, but you could avoid seeing them by typing alt+f2 and running the same commands :)

---

### Post by yugnip on 2012-01-23
Interesting. I get the exact same messages, but Nautilus runs as root. So the problem isn't that Nautilus won't run as root, but just an understanding of the output messages? Not sure about that. But you could avoid seeing them by typing alt+f2 and running the same commands :)

---

### Post by boregard on 2012-01-23
> **yugnip said:**
> Interesting. I get the exact same messages, but Nautilus runs as root. So the problem isn't that Nautilus won't run as root, but just an understanding of the output messages? Not sure, but you could avoid seeing them by typing alt+f2 and running the same commands :)tried your suggestion and still get same results.here is more info maybe it will help.see attachment below.

---

### Post by dcstar on 2012-01-24
[http://ubuntuforums.org/showpost.php?p=11636133&postcount=3](http://ubuntuforums.org/showpost.php?p=11636133&postcount=3)

---

### Post by boregard on 2012-01-24
> **dcstar said:**
> [http://ubuntuforums.org/showpost.php?p=11636133&postcount=3](http://ubuntuforums.org/showpost.php?p=11636133&postcount=3)After doing some more searches I found this  [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) hat tip to psychocats. I may try your suggestion though. So I'll mark this thread as solved,Thanks to all that replied.

---

### Post by hawthornso23 on 2012-01-24
Sorry to append to your thread, but my question follows directly. What are the negative consequence to using gksudo in a terminal? In other words why not  just put

```
 alias sudo gksudo 
```

in .loginrc and be done with it.

---

### Post by boregard on 2012-01-24
> **hawthornso23 said:**
> Sorry to append to your thread, but my question follows directly. What are the negative consequence to using gksudo in a terminal? In other words why not  just put

```
 alias sudo gksudo 
```in .loginrc and be done with it.Not really sure,maybe someone with alot more experience than me will come along with an answer. The link above your post goes into detail why its better to use gksudo than sudo.Have a good one.regards

---

