---
title: "Oh No What Should I Do ?!"
date: 2006-05-08
forum: General Help
---

### Post by Katocan on 2006-05-08
Ok so, I chmodded the /etc/ folder to 777 then I restarted ubuntu and now I can't login. I'm using XP to type this but I really need ubuntu, Does anyone think they can help me out?

Thanks for any help at all!

---

### Post by Gtaylor on 2006-05-08
It'd be a really good idea if you included any error messages, we're not able to help much unless we can see what's going on.

---

### Post by Katocan on 2006-05-08
Alright I'll post the messages

---

### Post by Katocan on 2006-05-08
Ok so after I enter my username and password.
This error is displayed
```

Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions

```

Then after I press OK this message is displayed
```

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions and see if you can fix this error.
```

Then it has a tick box saying
```
View details(~/.xsession-errors file)
```
and when you tick it, it displays the following
```

/etc/gdm/PreSession/Default: Registering your session with xtmp and utmp
/etc/gdm/PreSession/Defaukt: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "wez"
/etc/gdm/Xsession: Beginning session setup...
(gnome-session: 12866): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory `/var/.gnome2/': Permission denied

```

I would like to point out that I changed the directory for "wez" from /home/wez/ too the root folder which is //.

---

### Post by Katocan on 2006-05-08
So does anyone think they could be of help?

I will be more than happy if this is solved :)

---

### Post by Katocan on 2006-05-08
I really hate to bump topics but I really need to know if anyone can help out :(

---

### Post by Ramses de Norre on 2006-05-08
```
sudo chown username -R ~
chmod 644 ~/.dmrc
chmod -R +rw ~
```

Are you sure you chmod'ed /etc/ ? All the errors are about your home folder..

---

### Post by Katocan on 2006-05-09
I can't login what so ever as that was the only user and I can't login. Is there a way to start it up in a mode where you dont have to login or maybe theres a default user and pass.

Anything will be of great help, Thanks.

---

### Post by Ramses de Norre on 2006-05-09
ctrl-alt-F1 will give you a shell, maybe you can login there. Otherwise you'll need to boot in recovery mode.

---

### Post by Hallavej on 2006-05-09
Try to boot inn rescue mode. Hit Esc if you dont see the grub menu at boot. Then select rescue mode. That should give you a "root terminal". Then use chmod to change the permissions back.
edit: ups sorry its called recovery mode as Ramses said.

---

### Post by Katocan on 2006-05-09
Thanks a million I will give this a try.

---

### Post by Katocan on 2006-05-09
How could I create a new user in the terminal?

---

### Post by Googler on 2006-05-09
to add new user in terminal type:
```
useradd *username*
passwd *username* 
```

and it will prompt you for a password , set one

---

