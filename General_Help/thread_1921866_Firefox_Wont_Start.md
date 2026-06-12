---
title: "Firefox Wont Start"
date: 2012-02-07
forum: General Help
---

### Post by caned_monkey on 2012-02-07
I'm sharing my Firefox profile with  XP, it worked fine when I first linked  to my xp profile through profile manager but now whenever i boot into ubuntu and try to launch Firefox I get the error: 

Firefox is running but not responding. Terminate this process first or reboot before trying to open a new window.

There is no process to kill in system manager and i tried killall firefox in terminal but it says  no process running.

This only happens when i try to use the XP profile and this happens even after a reboot. XP is not running because i have booted straight into ubuntu.

Any help appreciated.

Ta.

---

### Post by jerrrys on 2012-02-08
I do not do this, but a search seems to have some solutions.  good luck

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=sharing+Firefox+profile+windows&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=sharing+Firefox+profile+windows&sa=Search&cof=FORID:9)

---

### Post by SeijiSensei on 2012-02-08
On Linux, Firefox uses two "lock" files that must not exist in order for it to start up.  Open your /home/username/.mozilla/firefox/randomchars.default directory and delete both the "lock" and ".parentlock" files if they exist.  To see .parentlock you must either use the "ls -a" command in a terminal, or tell the GUI file manager to show "hidden" files.

My guess is that the way the locks are managed in Windows and Linux are different.  For instance, I don't know what the equivalent would be to .parentlock since hidden files with leading dots don't exist in the Windows world.  (I don't even know if a file with a leading dot is valid in Windows.)

Where is the profile being stored?  On an ext2/3/4 (Linux) filesystem or an NTFS filesystem?  NTFS doesn't have the same characteristics as "POSIX" filesystems used in Linux, so sharing the directory between them can be tricky.

---

