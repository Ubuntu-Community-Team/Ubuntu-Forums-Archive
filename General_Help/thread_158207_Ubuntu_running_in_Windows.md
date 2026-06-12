---
title: "Ubuntu running in Windows"
date: 2006-04-10
forum: General Help
---

### Post by _linux_ on 2006-04-10
I have Windows XP on one hard drive, and Linux on another. Is there any way to run Ubuntu and Windows at the same time?

---

### Post by taurus on 2006-04-10
Yeah by a way of emulator like vmware or qemu!!!

---

### Post by YuHoo on 2006-04-10
sadly, I believe that is impossible with commercial hardware. Yes, if you're a maniac (like this guy [http://www.tomshardware.com/2005/06/13/extreme_modding/index.html](http://www.tomshardware.com/2005/06/13/extreme_modding/index.html)) you could scrape it together, but I'd suggest not doing it and just buying a second computer. After that just network them. I did some researching on your issue and found no progress at all in that field. I did however get sidetracked reading [http://en.wikipedia.org/wiki/Category:Operating_system_technology](http://en.wikipedia.org/wiki/Category:Operating_system_technology) which basically led me to think that there was only the option of the reboot for multiple operating systems to live happily.

You could create some type of overlord that manages which kernel/OS gets priority, but like creating your own frankenstein, it's not practical (or possible?)

Keep looking, I want to be proven wrong.

---

### Post by skymt on 2006-04-10
What you probably want isn't to run both at the same time. It would make much more sense just to run, say, Windows programs in Ubuntu. For this you should use [Wine](http://www.winehq.com/) ([wiki](https://wiki.ubuntu.com/Wine)). If you want to play Windows games, add [Cedega](http://www.transgaming.com/), if you want Microsoft Office, try [CrossOver Office](http://www.codeweavers.com/) (both of those cost money).

---

### Post by krismatth3 on 2006-04-10
[http://www.vmware.com/](http://www.vmware.com/) will allow you to use both at the same time.

---

### Post by _linux_ on 2006-04-10
What about loadlin? :confused:

---

### Post by YuHoo on 2006-04-10
Obviously you can simulate an environment for the other operating system, but you will face heavy reductions in performance. They have come a long way in terms of speed, but you should not expect what I think you were expecting which is to run both simultaneously and run apps in each one at the native speed.

---

