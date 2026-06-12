---
title: "Network usage locks up ubuntu."
date: 2010-03-02
forum: General Help
---

### Post by Travisivart on 2010-03-02
Hi everyone!

I've been having an issue with my Ubuntu server the past few days. I'm running Ubuntu 9.10 x64 server edition. I have this machine set up as an apache/tomcat server to host some websites. I recently decided that since my web server is always running I would attach a usb hard drive I have which stores dvd isos of a few the movies I own. Then for convenience I had this usb drive shared over the network using samba to any computer on the network which wants to access a movie for playback. Since I have been doing so, it seems that while I am watching a movie on my main PC, the server will suddenly freeze and lock up. I've tried doing an ssh into the server and it just hangs. I've gone so far as to hook up a spare monitor and keyboard to the server and I watch to see if I get an error message or anything of the like when it hangs up but I don't get anything. The monitor goes into standby mode and gives the message that it's not hooked up.

Would anyone have some ideas on what I can do to trace the source of this issue. I know that the only time I have ever had this server lock up on me is when I am watching a movie over the network. It seems to me to be related to either samba or a mounted and shared usb drive. Is there a log somewhere I could look at and try to find how this is happening, or maybe a command I could use to bring Ubuntu back to the shell so I don't have to hard reset it every time?

Any help would be greatly appreciated. Thanks!

---

