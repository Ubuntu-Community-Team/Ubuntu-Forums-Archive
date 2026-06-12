---
title: "How to inherit parent folder permissions when copying files"
date: 2011-03-28
forum: General Help
---

### Post by jocampo on 2011-03-28
I do have an Ubuntu Headless server which is running Samba on it. My mp3 file collection resides on that server on is being share.

So far, no problems connecting to that drive and writing from my Windows box on that share. But if I use my main laptop, which runs Ubuntu Lucid and download an mp3 song from Amazon, the moment I move that to the share, I got permissions problems from the Windows machine. This is clearly a permission issue with group and others; the song is being created on the share without read and write permissions to others or the samba group I created.

My question is. How can I make this process simple or automatic, when moving songs to the share? I don't want to go there everytime and run ...

```

chmod go+rw

```

Which was basically how I reset or fixed the problem.

I've read about umask, but not sure if that applies here or not, because I'm not creating the file but moving it.

Thanks in advance,

---

### Post by Morbius1 on 2011-03-28
There's a few ways to go about this I suppose but here's one you could try.

Add the following to the share definition in /etc/samba/smb.conf:
```
create mask = 0666
force create mode = 0666
directory mask = 0777
force directory mode = 0777

```That's the functional equivalent of "chmod go+rw" after the fact.

Don't forget to restart samba:
```
sudo service smbd restart
```

---

### Post by jocampo on 2011-03-28
Thanks Morbius,

Just adding those lines at the end of the Samba config file, like that?

Why some are 666 and others 777? I would only want to enforce group and others, and force read/write on both ....

---

### Post by Morbius1 on 2011-03-29
It's not at the end of smb.conf, it's within the share definition. For example, if your current share definition is this ( in black ) then just add the lines ( in blue ):
> [shared]
path = /home/Shared
valid users = @sambagroup
read only = No
[COLOR=Blue]create mask = 0666
force create mode = 0666
directory mask = 0777
force directory mode = 0777[/COLOR]Every new file will save with permissions of 666 - read and write to everyone.
Every new directory will save with permissions of 777 - read, write, and execute to everyone.

You need the execute bit to be turned on in a directory so that it can be "opened". Without it you can't get access to what's inside.

It may be that the share definition is the last thing in smb.conf so adding it to the end will work. But if it's not then those lines will be interpreted as pertaining to whatever came before it.

---

### Post by jocampo on 2011-04-01
Sorry for the delay, being busy.

Followed your advice, no luck. The new folder and file, still has read permissions only, no write. That's when created from a Windows box, of course.

---

### Post by jocampo on 2011-04-01
Morbius,

You actually helped me a lot! ;)

I fixed but doing this

```

[general]
        path = /home/jocampo/Music/Incoming
        comment = iPod
        writeable = yes
        browseable = yes
        guest ok = Yes
        force user = angel
[COLOR="Red"]        create mask = 0666
        directory mask = 0777[/COLOR]


```

The code or lines in red are those the one I changed. Now when I create a folder or a file from Windows, I can also write or delete from Ubuntu as well.

---

