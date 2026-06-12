---
title: "Need some help with permissions on a mount"
date: 2010-05-04
forum: General Help
---

### Post by RockDawg on 2010-05-04
I hope this is the right forum for this post.

I have two computers.  One is running XBMC Live media center which is built on a minimal Ubuntu installation.  On this machine XBMC stores thumbnails of my movies in /home/kevin/.xbmc/userdata/Thumbnails/. I am trying to centralize this thumbnail cache by putting it on my server, but it needs to appear as local to my XBMC machine.  My server is running unRaid NAS softeare which is build on Linux (slackware I believe.

I have successfully created a mount as follows:

```
mount -t cifs //192.168.1.20/disk7/xbmc_thumbs/Thumbnails  Thumbnails
```

I ran that inside /home/kevin/.xbmc/userdata.  //192.168.1.20/disk7/xbmc_thumbs/Thumbnails is the folder on my server that I mounted in XBMC (Ubuntu).

If I log into XBMC as root, I can copy files to the Thumbnails folder on my server and it shows up in the same folder on XBMC and vice versa.  If I log in as my usual XBMC user 'kevin' (which is the user XBMC will be when it's writing to the cahe) and try to do the same thing, I get permission denied errors.  How can I correct these permission issues?  I am green as can be when it come to Linux so I'm hoping someone could point me in the right direction.

---

### Post by v1ad on 2010-05-04
man chown 

sudo chown username directory

might need a r or something kinda forgot so use man and then go off that.

---

### Post by RockDawg on 2010-05-04
I tried that with no luck:

```
kevin@XBMCLive:~$ man chown
-bash: man: command not found

```

```
kevin@XBMCLive:~$ sudo chown kevin /home/kevin/.xbmc/userdata/Thumbnails
[sudo] password for kevin:
kevin@XBMCLive:~$ cd /home/kevin/.xbmc/temp
kevin@XBMCLive:~/.xbmc/temp$ cp localthumb.jpg /home/kevin/.xbmc/userdata/Thumbnails
cp: cannot create regular file `/home/kevin/.xbmc/userdata/Thumbnails/localthumb.jpg': Permission denied

```


```
kevin@XBMCLive:~$ sudo chown -R kevin /home/kevin/.xbmc/userdata/Thumbnails
kevin@XBMCLive:~$ cd /home/kevin/.xbmc/temp
kevin@XBMCLive:~/.xbmc/temp$ cp localthumb.jpg /home/kevin/.xbmc/userdata/Thumbnails
cp: cannot create regular file `/home/kevin/.xbmc/userdata/Thumbnails/localthumb.jpg': Permission denied

```

Any other suggestions?

---

### Post by RockDawg on 2010-05-05
Can anyone help me out here?

---

