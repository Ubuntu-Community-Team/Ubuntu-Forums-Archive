---
title: "start chromium-browser from google"
date: 2010-11-16
forum: General Help
---

### Post by craq on 2010-11-16
I was just about to post about my problem starting the chromium browser when I found the answer where I wouldn't normally look:
[http://forum.nginx.org/read.php?26,131377,131440](http://forum.nginx.org/read.php?26,131377,131440)

So in case anybody else meets the same problem...

I installed the standard version from the repositories, but when I tried to run I got the following error:
[3726:3726:2110326575:ERROR:chrome/browser/process_singleton_linux.cc(452)] readlink failed: Permission denied 
[3726:3726:2110326625:ERROR:chrome/browser/process_singleton_linux.cc(251)] readlink(/home/username/.config/chromium/SingletonLock) failed: Permission denied 
[3726:3726:2110326654:ERROR:chrome/browser/process_singleton_linux.cc(251)] readlink(/home/username/.config/chromium/SingletonLock) failed: Permission denied 
[3726:3726:2110326663:ERROR:chrome/browser/process_singleton_linux.cc(275)] Failed to create /home/username/.config/chromium/SingletonLock: Permission denied 
[3726:3726:2110326676:ERROR:chrome/browser/process_singleton_linux.cc(452)] readlink failed: Permission denied 
[3726:3726:2110326685:ERROR:chrome/browser/process_singleton_linux.cc(251)] readlink(/home/username/.config/chromium/SingletonLock) failed: Permission denied 
[3726:3726:2110326696:ERROR:chrome/browser/browser_main.cc(1106)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption. 

The trick is to remove (or just move, just in case) the ~/.config/chromium folder and let it recreate itself when chromium-browser starts

---

### Post by Verbeck on 2010-11-16
alternatively, i think chown-ing it might fix it
```
sudo chown -R username:usergroup -R ~/.config/chromium
```

---

