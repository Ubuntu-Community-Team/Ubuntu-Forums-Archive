---
title: "Guide installation for Hp P1005 printer - Ubuntu"
date: 2009-09-15
forum: General Help
---

### Post by crazywire on 2009-09-15
HI to the community. I recently take my adventure with Linux using the distro UBUNTU 9.04. So when i get the time to install my printer HP P1005 discovered a lot of trouble trying to startup. So surfing in the diferent post i Found this thread: 

[http://ubuntuforums.org/showthread.php?t=644041](http://ubuntuforums.org/showthread.php?t=644041)

where after a lot discusion take action using a HP suport for linux in this link

[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html) and

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Some people can get start up without a trouble, but in my case, like others, i can't. Coz when you finished the instalation the software say something like that: "you need a hp-plugin property". So in this point i follow all instruction about try to get that plugin, but nothing happen.
At this point, start to burn my head :P but i found in a russian forum th magical link than solved my trouble, this:

russian forum: [http://forum.ubuntu.ru/index.php?topic=56086.0](http://forum.ubuntu.ru/index.php?topic=56086.0)
magical link: [http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/](http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/)

in the last link i found it a completly database of all plugins, so i download it, and then when excecute hp-setup, and ask to me for this plugins i choice the option, i have the file. get the path and go on. 
Just take my attention when the utility of HP toll me something like: the plugins don't pass the digital sing. BUT i just go on until finished the configuration, and voila printing a test page without any trouble. I think a completly functional printing, and not get a latency when i try to print some document in no more 3 sec the printer starter the job.

procedure for me: 
1.- download the last HPLIP in my case was HPLIP 3.9.8
2.- Install.
3.- Go to the web page, than i nicknamed magical link
4.- Download the same number version of my HPLIP, but plugin file: hplip-3.9.8-plugin.run
5.- go to Hp-Setup and follow the instruction.


Well thx for your time, and i hope this thread can help somebody in this community.

p.d.- Sorry if the post exist, and is my first post.. but i search and found not match.

---

### Post by sumpm1 on 2009-12-03
I want to thank you so much crazywire. I have 3 of these printers intended for Ubuntu use. This tutorial got me up and running.

I am running 9.10. When the printer is plugged in, Ubuntu prompts you to automatically install the plugin. But I was not even able to print a test page that way. This method got me working right away.

---

