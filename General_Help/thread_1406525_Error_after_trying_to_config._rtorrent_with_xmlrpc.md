---
title: "Error after trying to config. rtorrent with xmlrpc"
date: 2010-02-14
forum: General Help
---

### Post by Ukuntu on 2010-02-14
First Greetings to all my fellows in the path of discovering Ubuntu

I have faced an error during my attempt to install rtorrent which is an exclusive torrent client for Linux. For long I have wanted to try this app. Honestly I am not familiar much with Ubuntu or any other Distro. I am trying to install rtorrent with rutorrent as a Web GUI on my home PC.

here is the sequence of commands of rtorrent install:
cd /tmp
sudo wget [http://libtorrent.rakshasa.no/downloads/rtorrent-0.8.6.tar.gz](http://libtorrent.rakshasa.no/downloads/rtorrent-0.8.6.tar.gz)
sudo tar zxfv rtorrent-0.8.6.tar.gz
cd rtorrent-0.8.6
sudo ./configure &#8211;with-xmlrpc-c ---------------------> I am stacked here 
sudo make
sudo make install

After Entering: sudo ./configure &#8211;with-xmlrpc-c
Terminal gives this error: checking build system type&#8230; Invalid configuration `.with-xmlrpc-c&#8217;: machine `.with-xmlrpc&#8217; not recognized
configure: error: /bin/bash ./config.sub &#8211;with-xmlrpc-c failed

---

### Post by Ukuntu on 2010-02-15
The Above Error has been solved by typing the command (not copy/paste the command).
I have finished installing rtorrent & rutorret & finshed the settings of rtorrent.rc on my home PC but I believe I have done something wrong in rtorrent.rc because  when I try to run rtorrent by entering &#8220;rtorrent&#8221; in terminal it shows this Error:

Error in option file: ~/.rtorrent.rc:7: Wrong number of arguments.
username@username-desktop:/tmp/rtorrent-0.8.6/doc$

I appreciate any help regarding this matter.

---

