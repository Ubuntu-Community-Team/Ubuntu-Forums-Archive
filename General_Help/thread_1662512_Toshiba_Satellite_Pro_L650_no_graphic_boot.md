---
title: "Toshiba Satellite Pro L650: no graphic boot"
date: 2011-01-08
forum: General Help
---

### Post by Lineplus on 2011-01-08
Bonjour,
I installed Ubuntu 10.10 in dual-boot with Windows 7 on a Toshiba Satellite Pro L650. I boot on my Live USB, everything works very well. I install without any problem. But when I start Ubuntu, Plymouth starts (with an ugly resolution, it was not the case with the Live USB), then it starts in CLI (I posted several screenshots showing the first instants of the starting - there is different informations on each). When I try to shutdown with *sudo shutdown -h now*, failsafe-x is killed, and Plymouth is killed half the time. I seen on forum posts posted some months ago that the computer works very well after a BIOS update: I tried with and without, same result. I reinstalled it two times, and I don't think the problem is caused by my USB key, who successfully installed Ubuntu on two others computers (not the same model). The 13 lines with set_chan backs regularly and whenever.

[[IMG]http://pix.toile-libre.org/upload/thumb/1294487160.jpg[/IMG]]("http://pix.toile-libre.org/upload/original/1294487160.jpg") [[IMG]http://pix.toile-libre.org/upload/thumb/1294487175.jpg[/IMG]]("http://pix.toile-libre.org/upload/original/1294487175.jpg") [[IMG]http://pix.toile-libre.org/upload/thumb/1294487209.jpg[/IMG]]("http://pix.toile-libre.org/upload/original/1294487209.jpg") [[IMG]http://pix.toile-libre.org/upload/thumb/1294487214.jpg[/IMG]]("http://pix.toile-libre.org/upload/original/1294487214.jpg") [[IMG]http://pix.toile-libre.org/upload/thumb/1294487727.jpg[/IMG]]("http://pix.toile-libre.org/upload/original/1294487727.jpg") [[IMG]http://pix.toile-libre.org/upload/thumb/1294487216.jpg[/IMG]]("http://pix.toile-libre.org/upload/original/1294487216.jpg") [[IMG]http://pix.toile-libre.org/upload/thumb/1294487215.jpg[/IMG]]("http://pix.toile-libre.org/upload/original/1294487215.jpg")

Thanks in advance for your help.

---

### Post by TeoBigusGeekus on 2011-01-08
From what I've found in [here]("http://ubuntuforums.org/showthread.php?t=1601023"), you might need to blacklist the intel_ips module. 
So (from command line)
```
sudo nano /etc/modprobe.d/blacklist
```
Add this line
```
blacklist intel_ips
```
at the end of the file, save (ctrl+x) and reboot. Post us what happened.

---

### Post by Lineplus on 2011-01-08
Thanks, it works !

---

