---
title: "Samba new folder permission problem"
date: 2012-02-25
forum: General Help
---

### Post by JJamesR on 2012-02-25
Hi all, I apologize in advance for asking this question as it's probably been asked millions of times already. Because I'm new to Ubuntu and still finding my way around the command line, I would really appreciate your help with my specific issue and a solution to it...I'm sure it's one small thing that I'm missing. 

I've set up Ubuntu Server 10.04 LTS and a samba share where I would like everyone "full" rights to. From my Windows machines, I would like to do whatever I want with files/folders inside this share. Here is the share as set up in my /etc/samba/smb.conf: 

[media]
comment = media
path = /srv/samba/media
browsable = yes
guest ok = yes
read only = no
force create mode = 0777
force directory mode = 0777

The problem I am having is that everytime a new folder is created by LottaNZB, I cannot access that folder from my Windows machines (I get Access is Denied)

Then I putty into the server and run:
sudo chmod -R 0777 /srv/samba/media
I can then access it no problem. 

Please tell me what I am missing in smb.conf?

---

### Post by Morbius1 on 2012-02-25
I have no idea what a LottaNZB is so until someone comes around that does I have a suggestion.

[COLOR=Blue]EDIT: You could of course create another share say at /srv/samba/test just to test this all out and see if it does what you want before committing to the real share.[/COLOR]

Install the bindfs package on the server:
```
sudo apt-get install bindfs
```[COLOR=Blue]*Note: If you are using oneiric it won't work because the package is messed up. It will install previous to that release and so far it appears to be fixed for the release after however.*[/COLOR]
Then run the following command:
```
sudo bindfs -o perms=0666:+D /srv/samba/media /srv/samba/media
```[COLOR=Blue]*Note: That is not a typo although it does look a little strange - you are mounting a directory to itself with a "view" provided by bindfs.*[/COLOR]

From that point on during your session all your current files regardless of their existing Linux permissions and all files added will have read/write permissions to everyone ( 666 for files - 777 for folders ). Doesn't matter what permissions LottaNZB thinks it's setting and it doesn't matter what permissions Samba thinks it's setting - bindfs is in control.

If that's not what you want or if I've misunderstood your post you can undo all this with a umount:
```
sudo umount /srv/samba/media
```To have this done at boot time you can create your own upstart job:
```
gksu gedit /etc/init/bindfs-samba.conf
```With this content:
```
# Create samba share permissions using bindfs
description "Samba Share Permissions"

start on stopped mountall

script
  bindfs -o perms=0666:+D /srv/samba/media /srv/samba/media
end script

```

---

### Post by JJamesR on 2012-02-26
Ok let me put it this way....what do I need to add to smb.conf to make sure that whenever a **new folder** is created inside the share, that it gets created with the same permissions than it would have if I had to run "sudo chmod -R 0777 /srv/samba/media"?

---

### Post by JJamesR on 2012-02-29
Anyone?

---

### Post by Morbius1 on 2012-02-29
Take a look at: [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)
And look for the definitions of create mask, directory mask, force create mode, force directory mode, force directory security mode, force security mode, and maybe some others. And don't forget that they are bit-wise AND and/or OR'd so you may have to play around with it a bit. Bindfs is beginning to look pretty good as an alternative isn't it?

You could also force every remote user to look like a specific user so it doesn't matter what the permissions are. You would change the share definition to look something like this:
> [media]
comment = media
path = /srv/samba/media
browsable = yes
guest ok = yes
read only = no
[COLOR=Blue]force user = nobody[/COLOR]"nobody" should already be an actual user on your server.

The only question at this point is your LottaNZB thingy. If it accesses the target folder through the "media" share then whatever you do to the share definition might just work for it. But if it accesses the target folder directly - as in it saves files to /srv/samba/media directly - then no matter what you do to the share definition probably won't work.

---

### Post by JJamesR on 2012-03-08
Thanks Morbius..

I'm trying bindfs. I followed your instructions so I'll test and let you know how it goes. 

Thanks for your help!

---

