---
title: "Help with Bind9 and DNS on Ubunutu Server"
date: 2011-01-11
forum: General Help
---

### Post by rededit on 2011-01-11
I am trying to set up a local domain so I followed the tutorial located [here]("http://ubuntuforums.org/showthread.php?t=236093") to set up a nameserver. My local domain seems to be working with all the tests but I cannot browse to the dns server which also host an internal site. I asked for help in that thread but I think that nobody is replying on that thread anymore. I posted all of my config files and my question [here]("http://ubuntuforums.org/showthread.php?t=236093&page=15"). I was hoping that some one could point me in the right direction or maybe let me know what I am doing wrong. All of the tests I ran are located in my post. Any help would be greatly appreciated.

---

### Post by rededit on 2011-01-13
I got my problem resolved. I basically was using ssh to remote into my server from home. I created a tunnel and was using that tunnel to browse and test my dns settings from home as if I was at work. This way I could browse to my internal web-server by typing the local lan ip since my web-server is internal and not accessible via the internet, it is intended to only be used internally. Well I was able to browse via lan ip 192.168.x.x but could not browse to the site using the domain that was created x.local. Well I got to work and the dns server seemed to be doing fine. I was able to browse to the webserver using the domain instead of the lan ip. I am not sure if this was the problem but it seems to have been resolved and the only difference is I am not using an ssh tunnel to try to browse internal lan pages.

---

