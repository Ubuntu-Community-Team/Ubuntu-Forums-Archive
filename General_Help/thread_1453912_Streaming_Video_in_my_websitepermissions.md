---
title: "Streaming Video in my website/permissions"
date: 2010-04-13
forum: General Help
---

### Post by ZJ88 on 2010-04-13
Hi,
I am making a small html website to host some videos.  I'm hosting the site on my Ubuntu server but I have run into a few small snags.  One is permissions.  For some reason I have to go to almost each file and set the permissions so others can view the website.  I was wondering if there was an easy way to set these permissions so the site functions outside my network perfectly.  Also, I'm trying to stream videos.  I've embedded them and tested them and they seem to work.  The problem is, using a computer outside my network, the videos won't play.  I think I need to configure something so that my server will stream video out to others.  If anyone could help I'd greatly appreciate it.

Thanks in advance,  Zachary

The big thing I'm hoping to figure out right now is how to get the videos working.  If anyone knows how to do this please help.  I have apache2 installed, is there some kind of config file I need to change to get the videos to stream?

---

### Post by gzarkadas on 2010-04-14
Hi, its late here and I must go to sleep, so I will be quite brief for the moment:

Permissions: 
Web servers operate as user www which has limited rights; all the data you want to publish (usually under /var/www) must be world readable (files: -rw-r--r--, directories: drwxr-xr-x) and, generally, owned by root. Is your setup in line with this or it is different?

Streaming:
I am not sure at the moment, but I have the impression you need to set an appropriate mime type for your videos (in the headers that your web server sends); I will start looking to this from tomorrow.

Also, if from inside your network you can see things work, but from outside not, you should check your firewalls settings (on the gateway) and the settings of your apache site (/etc/apache2/sites-enabled/...) as well as other files inside /etc/apache2, to see what is blocking you. If you use a proxy such as squid, check also /etc/squid/squid.conf.

---

### Post by ZJ88 on 2010-04-15
Hey thanks for the help.  As far as permissions and such, at the moment, I have my site under a virtual server in my profile as public_html.  It isn't owned by root at the moment but by my user.  As far as I know, I just went in and changed them by going to properties, permissions, others, read-only. but that can be kind of a pain.

With streaming, I'm pretty sure I've worked that out.  After hearing about mimes I looked that up and realized I didn't have any declared.  I put them in and presto! it worked. For the most part. I have to go and make the video files a bit smaller so they will actually load in a timely manner.

---

### Post by gzarkadas on 2010-04-15
You can speed up such things as updating permissions by opening a terminal window and entering the following commands (since your user account owns the files, there is no need to sudo):

```

cd ~/public_html             # or whatever path you do use
find -type d -exec chmod g+rx,o+rx  '{}'  ';'
find -type f -exec chmod g+r,o+r  '{}'  ';'

```Also, if you have relaxed permissions of your account's home directory to make the web server work (say made everything world-readable), you don't need to; it suffices to set only the x bit in the top directories. For example (outputs of `ls-l' joined together):

```

drwx--x--x 1  ...  /home/<youraccount>
drwxr-xr-x 1  ...  /home/<youraccount>/public_html
/home

```

---

