---
title: "Chromium browser crashes frequently after update"
date: 2012-10-01
forum: General Help
---

### Post by kwanylongy on 2012-10-01
Dear all,

I am on Ubuntu 12.04, and I use the Chromium browser as my default browser. My Ubuntu software manager prompted me to receive new updates last Wednesday (26th Sept), and since the update my chromium browser crashes frequently that has make it unusable. My Chrome browser had already become unusable some time ago after software update (so I have no alternative). Has anyone had a similar experience and knows what the problem is??

Any help would be much appreciated!

---

### Post by drmrgd on 2012-10-01
You might consider launching Chromium from the terminal and having a look at the stdout and stderr that is generated.  When the program crashes, you might then be able to see the error you're getting in order to fix it.  If you want, you can also log this error in order to evaluate later or post to the developers or something:

```
chromium >> /home/<username>/chromium_log.txt 2>&1
```

That will create a log called 'chromium_lot.txt' in your home directory (replace '<username>' with the actual username of that home directory) of the stdout and stderr.  That will be a good first step to troubleshooting the problem.

---

### Post by vasa1 on 2012-10-01
> **kwanylongy said:**
> ... My Chrome browser had already become unusable some time ago after software update (so I have no alternative). Has anyone had a similar experience and knows what the problem is??
...
In addition to drmrgd's suggestion, you can look at this answer: [Why is my Chrome so slow?]("http://askubuntu.com/a/83934/25656") and this official support thread on [creating a new profile]("http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059").

---

### Post by kwanylongy on 2012-10-01
Thanks, I will do that and post the error log here later

---

### Post by kwanylongy on 2012-10-01
Below are the errors I get from terminal and from the log file.

Thank you so much for your help!

_Terminal_
[LEFT]carlos@asurada:~$ chromium-browser >> /home/carlos/chromium_log.txt 2>&1 &
[4] 22523
[3]   Segmentation fault      (core dumped) chromium-browser >> /home/carlos/chromium_log.txt 2>&1[/LEFT]

_chromium_log.txt_
[LEFT]Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi [/LEFT]

---

### Post by kwanylongy on 2012-10-01
> **vasa1 said:**
> In addition to drmrgd's suggestion, you can look at this answer: [Why is my Chrome so slow?]("http://askubuntu.com/a/83934/25656") and this official support thread on [creating a new profile]("http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059").

vasa1,

I tried resetting Chrome's profile by renaming the /home/.config/google-chrome/Default folder, but Chrome's problem still persisted.

I'll read more into those posts to try out other potential solutions

Many thanks!

---

### Post by drmrgd on 2012-10-01
Thanks for posting that log file.  I'm not sure what would be causing the seg fault and if the missing nvidia libraries are the cause.  I'm afraid this might be a little too specific to Chromium and you might have to post this to the Chromium bug report page.  

Looking around the web for the library and chromium problems, I cam across this at the Arch Linux forums:

[https://bbs.archlinux.org/viewtopic.php?id=139108&p=2](https://bbs.archlinux.org/viewtopic.php?id=139108&p=2)

It was solved by an upgrade.  But, this is around 5 or 6 months ago, and you may have a more recent version anyway.  So, I don't know if it'll help.

---

### Post by kwanylongy on 2012-10-02
drmrdg,

Thank you so much for your help. Your help has identified my problem and I will try to solve it myself from here on.

Thanks!

---

### Post by ravisghosh on 2012-10-11
Did you get the solution for ubuntu? It's really annoying to have chrome crash every now and then.

---

