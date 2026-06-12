---
title: "Running multiple instances of Rtorrent"
date: 2010-04-13
forum: General Help
---

### Post by arvin2212 on 2010-04-13
Hello, I followed this guide here:

> [http://filesharingtalk.com/vb3/f-guides-and-tutorials-65/t-installing-rtorrent-and-rutorrent-on-debian-based-linux-393861](http://filesharingtalk.com/vb3/f-guides-and-tutorials-65/t-installing-rtorrent-and-rutorrent-on-debian-based-linux-393861)

Once done with the installation, everything runs fine. I can run rtorrent and also access its webui, rutorrent from my browser just fine.

However, what should i do if i want to run multiple instance of rtorrent and rutorrent on the same box under different users?

I have found a solution on this post: > [http://ubuntuforums.org/showthread.php?t=1119482&page=2](http://ubuntuforums.org/showthread.php?t=1119482&page=2)

However, it didn't work for me. I think for it to work, i must have more than 1 instance of rtorrent running at the same time. Now this is the issue, whenever i try running rtorrent under a different account, i would get an error saying that the current socket is in use (which is being used by the rtorrent on the initial account).

What i have found out is that , following the guide, rtorrent wouldn't be able to find its own config folder initially. Then i found a post here:

> [http://ubuntuforums.org/showthread.php?t=381377](http://ubuntuforums.org/showthread.php?t=381377)

which suggested that i do:

> cd ~/
wget [http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest](http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest)
mv rtorrent.rc\?rev\=latest .rtorrent.rc

and then proceed to edit the file. Once doing that, rtorrent no longer reports of not being able to locate its config file. Now this is an issue because the config file becomes centralized. When i run another rtorrent under another account, it would access that same configuration file and then the error comes.

Is there anyway i could go about this?

(I am running Ubuntu Server)

---

