---
title: "Could not look up internet addres for...(gnome problem)"
date: 2006-04-13
forum: General Help
---

### Post by inovermyheadd on 2006-04-13
I get this "error" while trying to log into gnome.

"Could not look up internet address for .  This will prevent GNOME from operating correctly.  It may be possible to correct by adding to the file /etc/hosts"

then it allows me to try again, or log in anyway.  

I think I may have messed something up trying to use the internet w/ my Dad's new router.  I really don't know what to do...should I just reformat?

---

### Post by Ensnared on 2006-04-13
The problem is that Gnome couldn't find the IP for your computers hostname, which is a pretty common thing for LAN's. There's a simple way to fix it though, and that is to add your computers hostname to the list of names for the 127.0.0.1 entry in /etc/hosts.

For reference, this is what mine looks like (actual hostname is gargamel):
```
127.0.0.1       localhost.localdomain   localhost       gargamel
```

So just edit this file and add the name, close and exit, and restart Gnome, and you should be home free.

---

### Post by inovermyheadd on 2006-04-14
ok, so I attempted to gedit hosts but I can't use sudo.  When I tried to do so I got this error:

"sudo:  unable to lookup  via gethostbyname()"

I can, however, look at the hosts file and it says:

[PHP]127.0.0.1       localhost.localdomain   localhost [/PHP]

so I am assuming that all I need to do is put my username at the end of localhost...but I can't because it is read only.  Man I have no clue how I did this, lol...I appreciate the help though!

---

### Post by Al3xanR0 on 2006-04-14
[QUOTE=inovermyheadd]ok, so I attempted to gedit hosts but I can't use sudo.  When I tried to do so I got this error:

"sudo:  unable to lookup  via gethostbyname()"

I can, however, look at the hosts file and it says:

[PHP]127.0.0.1       localhost.localdomain   localhost [/PHP]

so I am assuming that all I need to do is put my username at the end of localhost...but I can't because it is read only.  Man I have no clue how I did this, lol...I appreciate the help though![/QUOTE]

This can be done using your favorite text  editor. For instance I use vi, you would simply

```
su
```

or in your case 

```
sudo
```

then 

```
vi /etc/hosts
```

type

```
i
``` for insert, make your edits then type

```
wq!
```

to save.

---

