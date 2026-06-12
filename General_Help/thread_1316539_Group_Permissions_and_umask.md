---
title: "Group Permissions and umask"
date: 2009-11-06
forum: General Help
---

### Post by hurgh on 2009-11-06
Hi All,

I have a question, and I cant seem to find an answer, despite a lot of searching. Maybe I am not searching for the correct terms.

I have a user on my system with a group, and no login (/bin/false)

The username and group are: motion:motion (used for the "Motion" package).

I added my main user to the motion group so that I can view all the stuff in the home dir (where the clips etc are stored). I would also like to be able to delete these from motion's home dir, but for me to do this, I need the group permissions to have read and write access (as oppose to the default read only).

I can chmod the correct permissions and then I am able to do what I want, but each time a new file/dir is created below motion's home dir, the default permissions are set which means that I cant delete them from my normal account.

I know I could modify umask to make it work, but I dont want to make the change system wide, I just want to change the value for the motion user.

Can someone please point me in the direction of some doco, or give me a quick example on how i can do this.

Thanks

-Hurgh-

---

### Post by madverb on 2009-11-06
[http://en.wikipedia.org/wiki/Setuid#setgid_on_directories](http://en.wikipedia.org/wiki/Setuid#setgid_on_directories)

---

### Post by delcypher on 2009-11-06
Hmm tough one. I'm not exactly sure how to do that either but I have a few suggestions:

1. You could change the umask setting in /etc/profile which is the global umask setting for everyone. I have a strong feeling this won't work however because the file /etc/profile needs to read by bash. If your user never runs bash (it has no useful login shell) then the umask will never be set. In that case I'm not sure where linux get's the umask from

2. A quick glance through documentation brought up something that might help you. There's a package called libpam-umask which is a library for PAM which does stuff with authentication.

Once you have the library installed look at
```
man pam_umask
```

It suggests you can set the umask setting by adding a line to /etc/pam.d/login

I'm not sure if this will let you do it per user though, maybe?
```
session optional pam_umask.so motion umask=0002
```
I'm not sure. I think this along the right track but I'm not quite sure how to use PAM or any of it's modules.

Maybe look for some PAM documentation?

Hope this helps.

I'll follow this thread because I'd like to know how to do this too.

---

### Post by hurgh on 2009-11-06
Thanks both of you for your suggestions.

delcypher, I did read that in a file on the system, but I didnt realise that pam was a package. I will have a bit more of a look into that.

Also, I do remember reading something on the internet about acl which I assume is another package. I might follow up on that too.

What do other people do in this situation? Where more than 2 or more users need to have full access to files in a "shared" group dir?

Thanks

-Hurgh-

---

### Post by delcypher on 2009-11-06
Had a further look into it. I'm guessing initial umask settings come from this file.
```
/etc/login.defs
```. If you want pam_umask umask setting to come into affect them you may have to comment out the umask line (don't quote me on this.. I'm not completly sure if this is necessary)

After reading the manual ([http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_umask.html]("http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_umask.html")) for pam_umask more carefully I think you would want this line in your /etc/pam.d/login
```
session optional pam_umask.so
```
The man page says it will look at the GECOS field for the user concerned ([http://en.wikipedia.org/wiki/Passwd_%28file%29]("http://en.wikipedia.org/wiki/Passwd_%28file%29")) in /etc/passwd for the umask setting (if you don't set umask= in /etc/pam.d/login). So I think you would need to add a umask=022 entry to your motion user as well.

I believe the command to add this entry to your user would be, but I'm not 100% sure so don't blame me if I've got it wrong!
```
sudo chfn -o umask=0022 motion
```

It would be good if someone more knowledgible than me commented on this as I don't know much about linux administration.

---

### Post by hurgh on 2009-11-06
Hi All,

I just thought I would reply and let you know how I went.

delcypher, I really appreciate you help on this. I didnt end up using pam_umask as from reading about it, I didnt know if my user would work ok with it as they dont have a shell.

I came across a few articles about ACL and that ended up doing what I needed.

Here are some quick details that I found out along the way.

1. ACL's need to be compiled into the kernel.
2. The file system you want to apply acl's to needs to be mounted with the ACL option (in /etc/fstab)

ACL's can apply permissions on a directory and allow any sub directories to inherit the settings also. You can give very granular control of permissions down to the user or group. Once an ACL has been applied to a dir or file, it is worth noting that ls -l does not reflect the true dir permissions, and it is worth using getfacl to see the permissions.

Some useful man pages:
man setfacl
man getfacl

I am no ACL expert, but if there are any questions, I will try and answer them.

Thanks again for the help.

-Hurgh-

---

