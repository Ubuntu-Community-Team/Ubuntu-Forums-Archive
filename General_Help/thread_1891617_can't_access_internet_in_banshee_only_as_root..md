---
title: "can't access internet in banshee only as root."
date: 2011-12-06
forum: General Help
---

### Post by rizos on 2011-12-06
i have an admin account and recently from no where now i cant access internet radio stations in banshee and download applications via ubuntu software center or install anything via terminal.

but internet and ubuntu one is working as expected.


then if i launch banshee as root then i can connect to internet radio stations in banshee or software center.


apt-get update, upgrade or install wont work cause cant connect to the server of ubuntu.



i try to change owner of home folder via chown -R user:user /home/user


but error of input/output wont let me.

some how ubuntu thinks im not root and have not enough permits to access internet.


very odd case.


what can be wrong?

any ideas?

---

### Post by phidia on 2011-12-06
One way to start trouble shooting this is to open a terminal and as your regular user type banshee then press enter. What's the output of that?

Did you recently create the superuser account or make some changes as su?

---

### Post by rizos on 2011-12-06
the output of banshee in terminal when trying to play a radio station (connect to internet) is 

[Warn  09:35:58.076] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0


Error 09:36:26.418] GStreamer resource error: NotFound


and totem shows:


** Message: Error: Cannot connect to proxy (127.0.0.1)
gstsouphttpsrc.c(922): gst_soup_http_src_finished_cb (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstSoupHTTPSrc:source:
libsoup status code 5


but im not behind a proxy at all.

---

### Post by phidia on 2011-12-06
This is a bug reported at lunchpad-you can view that [here]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/751575"). I'm not sure if it's the same issue.

However [this webpage]("http://fredreh.wordpress.com/2008/06/12/banshee-media-player-10-and-gstreamer-resource-error/") seems to address your problem specifically-good luck!

---

### Post by rizos on 2011-12-07
actually my issue is not related to the link you post (thanx though) the issue is that proxy is set somewhere for this account and is bloicking internet conection to certain applications such as totem, banshee and ubuntu software center.

in network settings i disable proxy wide system. 


but somewhere some how proxy still on.

the out put of: env | grep proxy 

http_proxy=http://127.0.0.1:8123/
https_proxy=https://127.0.0.1:8123/

i uninstall polipo and vidalia and didnt fix the issue

any ideas how to fix this?.

---

### Post by zero2xiii on 2011-12-07
Hay,

127.0.0.1 is the localhost, should not cause any issues?

What is the output of **sudo route**?

Check you network manager when editing a connection (the one you use to connect to the internet) that the box in the botom left hand conner that says "Availible to all users" are checked.

Cherz

---

### Post by rizos on 2011-12-08
last thing i did was uninstall vidalia but i notice there was a .vidalia folder still in my home folder after that now i have full conection to internet.

but i cant really tell what solve the issue.

should i mark this as solved?

---

### Post by zero2xiii on 2011-12-08
Yes,

Techinaly it was a missconfiguration of vidalia:
[http://www.pc-library.com/ports/tcp-udp-port/8123/](http://www.pc-library.com/ports/tcp-udp-port/8123/)

Please marked as solved, as your issue is resolved.
Thanks
CHerz

---

