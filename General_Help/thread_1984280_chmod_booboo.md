---
title: "chmod booboo"
date: 2012-05-21
forum: General Help
---

### Post by Belgatom on 2012-05-21
Been a long time since I've been here. Has to be a good sign, no? 

But unfortunately, I've done a booboo and need help to get out. 

All started with HTPC project. I wanted to be able to approach my Ubuntu machine from the Windows 7 running XBMC. I had never set up a samba share so followed [this advice]("https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html"). Everything worked fine, except, I had no permission to write in the share. Only when I ran sudo nautilus, could I do this. 

I found this a tad to complex, so I thought, and here it come...
"why don't I make my Download folder in my Home directory a share". 

I followed the guide and substituded /srv/samba/share with /home/myuser/Download. 

Followed ofcourse by "sudo chown nobody.nogroup /home/myuser/download/"

Resulting in me not having any rights in my own download folder and the XMBC not being able to approach the download folder. 

I need help with two things:

1. very important: how do I reset my rights in my own download folder

2. how can I make a share that I have rights to write and the Windows 7 XBMC have rights to read. 

I've looked up chmod and stuff but I've been giving support all day on our software products and my brain is going googoo. 

Thanx in advance. 

(next time, I'm setting up Ubuntu as base of XBMC)

---

### Post by kanikilu on 2012-05-21
For the permissions issue, it sounds like you just need to chown it back to your account and then chmod it to allow xmbc.

By default, the Downloads folder is given 755 permissions, so, just change it back:

```
cd ~/
sudo chmod 755 Downloads/
```

Now change the owner to your username and primary group name:

```
sudo chown username.groupname Downloads/
```

If you don't already know your username and group, you can use these two commands (separately):

```
whoami
id -ng `whoami`
```

As for XBMC, I've never tried it, so can't really help there, but by default, your home directory and your downloads folder are readable by everyone (again, 755), so I don't think the unix permissions are the issue. Maybe the samba config is an issue?

---

