---
title: "Apt Freezes while updating base-files_5.0.0ubuntu20_amd64.deb"
date: 2010-07-25
forum: General Help
---

### Post by ghetto2ivy on 2010-07-25
Lucid Lynx keeps giving me headaches. This is the second update to bork my system. I update my system daily and yesterday's update (July 24th) simply failed to install. It froze on Unpacking replacement files. I left it running and went out, came back 36 hours later and it was still at the same point. 

Killed apt, dpkg, then removed the locks (/var/cache/apt/archives/lock
 and /var/lib/dpkg/lock), ran sudo dpkg --configure -a, and ran the upgrade again. Again it freezes unpacking base-files_5.0.0ubuntu20_amd64.deb. 

Killed everything again and tried it from the gui and same result.

My system won't update. And since a kernel update is listed among the things to be updated, I am not going to be able to shut down my computer, lest I can't boot it back up. And since the system now sees the unfinished install, I also cant install any new software.

Here's where it freezes.

```
Preparing to replace base-files 5.0.0ubuntu20 (using .../base-files_5.0.0ubuntu20_amd64.deb) ...
Unpacking replacement base-files ...
```

Anyone else experiencing this?

---

### Post by robsoles on 2010-07-26
I am responsible for a few 10.04 LTS desktops and a server at work and have similes of these at home - none show me this problem to date.

I think you are still in your GUI/Desktop.

Please open two instances of Terminal and in one type ```
tail -f /var/log/messages
``` and in the other type ```
tail -f /var/log/dmesg
```Re-run the updates and watch these two logs - post the results back to this thread if you don't see anything you can pursue to fix this yourself.

---

### Post by ghetto2ivy on 2010-07-26
I ran a another upgrade with the logs (and dpkg log as well) open as you suggested. It doesn't appear to freeze on any particular program there. For example, I attempted to purge evince, but the process still hangs on "unpacking replacement base-file".

Here's what the dpkg log offers up:
```
2010-07-26 10:10:53 status half-installed base-files 5.0.0ubuntu20
2010-07-26 10:10:53 status triggers-pending install-info 4.13a.dfsg.1-5ubuntu1
2010-07-26 10:10:53 status half-installed base-files 5.0.0ubuntu20
2010-07-26 10:10:53 status triggers-pending man-db 2.5.7-2
2010-07-26 10:10:53 status half-installed base-files 5.0.0ubuntu20

```

And that's where it hangs. None of the other logs show any changes.

---

### Post by robsoles on 2010-07-26
I can't emulate your problem so far so I am not rushing into spouting advice to get around it.

This is more or less a BUMP post while I consider it some more.

---

### Post by ddvlad on 2010-07-28
I am experiencing the same issue, same configuration (amd64). Logs look identical to OP's. After interrupting the apt-get process, I tried starting it again. It wouldn't start, so I removed /var/lib/dpkg/lock, ran dpkg --configure -a, then restarted the dist-upgrade. The second time, it still hangs.

Is anyone else facing the same problem?

Thanks,
Vlad

---

### Post by robsoles on 2010-07-28
I think your machines probably reboot to GUI no real problem at this point(?).

Would either, both or perhaps any of you please post back the response to following in terminal
```
ls /var/lib/apt/dpkg/*
```
I am of the, possibly deluded, belief a healthy system on which updates didn't previously crash or otherwise get interrupted, will be
```
ls: cannot access /var/lib/apt/dpkg/*: No such file or directory
```

I'm too drunk to go spouting off *exactly* what to do about it if you get something else for it now, but moving it away from the /var/lib/apt directory seems good to me at this point, I will get back to the thread in less than a day with a firm statement when I've reconsidered sober!

Oh stuff it, have a bash at restarting your updates via the GUI ("System"->"Administration"->"Update Manager") after issuing following in terminal:
```
 sudo mv /var/lib/apt/dpkg /root/
sudo apt-get update
sudo apt-get upgrade
```
Though if you want to 'dist-upgrade' you do, of course, have to write that for yourself!


You can just undo the change to your file-system I asked for if it seems to make your situation worse:
```
 sudo mv /root/dpkg /var/lib/apt/dpkg
```


Feedback?

---

### Post by ddvlad on 2010-07-28
After rebooting the box, the upgrade went smooth. I have no clue what could have caused the hanging.

And, if it matters, you are correct, there is no /var/lib/apt/dpkg.

Thanks for the support,
Vlad

---

### Post by robsoles on 2010-07-28
Just rebooting after such an event and retrying the overall action often overcomes such problems but sometimes does bite you in the backside by not booting functionally, as ghetto2ivy's OP seemed to make me think they didn't 'feel' it's going to be accessible easily after rebooting. Very welcome anyway ddvlad.

How's it going ghetto2ivy? Restarted since the update crash? What happens if you apply the terminal commands from my #6 post above? I expect a same or better situation for you.

---

### Post by ghetto2ivy on 2010-07-28
I did indeed fear that my system would be left in an non-bootable state, and took the necessary precautions (burning a live cd). But, yes, a reboot did indeed solve the issue.

Rebooted and all went well, afterward upgraded the packages without issue. 

I didn't get to visit this thread before then, so I only checked afterward, but /var/lib/apt/ dir does not have a dpkg directory now. 

Thanks for the help everyone.

---

### Post by samuelrivas on 2011-06-30
I'm facing the same problem right now. If it's useful:

```

$ ls /var/lib/apt/
cdroms.list  extended_states  keyrings  lists  mirrors  periodic

```

---

### Post by robsoles on 2011-07-01
Welcome to UF.

That is useful, it shows the dpkg entry isn't there, but would you please show us the response to ```
sudo apt-get update
sudo apt-get upgrade
```
from terminal?

---

