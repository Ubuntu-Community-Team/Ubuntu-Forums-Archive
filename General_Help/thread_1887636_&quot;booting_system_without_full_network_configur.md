---
title: "&quot;booting system without full network configuration&quot; Hanging"
date: 2011-11-27
forum: General Help
---

### Post by tetelee on 2011-11-27
Hi all,
Recently I have updated my ubuntu to Linux 3.0.0-13-generic on my thinkpad T61 laptop. But now I got this classic "booting system without full network configuration" hanging problem. I noticed there are some solutions to this problem on the web but they didn't work for me. For example, like this one: 
[http://www.totalcomputersusa.com/2011/10/ubuntu-11-10-booting-system-without-full-network-configuration/]("http://www.totalcomputersusa.com/2011/10/ubuntu-11-10-booting-system-without-full-network-configuration/")
For one thing, they all say that even the screen hangs at "booting system without full network configuration" phase, it is still possible to press Ctrl+Alt+F1 to go to command line and login. However, in my situation it is totally stuck and Ctrl+Alt+F1 or Esc doesn't work (but it is possible to press Ctrl+Alt+Del to restart the computer).
Secondly, I tried go to recovery-mode and loging from command line there and performed the mentioned solution: basically uninstall the lightdm and install gdm. There were some warning when I remove the /var/run/ folder and re-link it. But the installation and configuration went through. However, I still got the same problem after I restarted.
It might be worth mentioning that unlike some other problem report, which happened as early as one year ago, my problem only happened after the recent update. Now I can still go back to use previous version (3.0.0-12-generic). But it is so bothering for me knowing that I have some problem with latest version. Any help will be appreciated!

---

