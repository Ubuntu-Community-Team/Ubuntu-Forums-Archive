---
title: "Samba file permissions"
date: 2010-03-10
forum: General Help
---

### Post by Sycron on 2010-03-10
On Tux Box there are two ubuntu users. Fred and Tom. Fred's group is fred, root, etc and have sudo access. Tom's group is just tom, no admin/root access.

On #windoze.box1 Tom have to access samba (authentificating with his Tux Box account details like user:tom, password:imnothome) from Tux Box and copy his journal new entries there. After he copies them he may not view, modify, rename, delete them.

Meanwhile on #windoze.box2 Fred log on samba from the Tux Box and have full access to journal entries.

The folder with journal entries is */var/journal* (owner fred, group fred) and has 660 permissions.

The smb.conf:```
[global]
workgroup = workgroup
server string = Tux Box
security = user
encrypt passwords = yes
socket options = TCP_NODELAY
admin users = fred
hide dot files = yes
share modes = yes
browseable = yes

[tom]
valid users = tom
path = /var/journal
logon path = /var/journal
writeable = yes
browseable = yes
public = yes
printable = no
#i tried with
#force user = tom
#force group = fred
#create mode = 060

[fred]
valid users = fred
path = /var/journal
logon path = /var/journal
writeable = yes
browseable = no
public = no
printable = no
#force user = fred
#force group = fred
#create mode = 660
```

The effect: Tom can copy his journal entries and can't(which is what I want) view, modify, delete but rename them (why?). Fred can just view the journal entries and not modify, delete them.

Any help is appreiated.

---

### Post by kamaji792 on 2010-03-10
I have to say I can see nothing to tell us why your setup is behaving the way it is.

I just wonder about naming shares to the names that would be used if you used the [home] share.

Other than that have you tried:
```
testparm
```

To see if it can see any errors.

atb

---

### Post by Roasted on 2010-03-10
What are the permissions of /var/journal? If you could, go into /var and run ls -l and paste the contents back here.

I'm curious if the parent folder has restrictive enough permissions that wouldn't allow the other user to get into it.

---

### Post by Sycron on 2010-03-10
/var/journal has 660. Tom is ok(it works that part as i want) but Fred has a problem, he have to modify Tom's journal entries and can't do that.

A file posted by Tom has 060, (owner tom, group fred (tom is not member of fred's group)).

If Tom's file has 060 I don't understand why fred can't modify the file as he is member of fred's group.

---

### Post by Roasted on 2010-03-10
Just a thought - instead of having 2 users and forcing the group to each, what if you create one common group and tom/fred be members of? I know that you have fred as a member of tom's group (or vice versa) but in your smb.conf you're forcing two different groups based on the user to the same share.

It's just a thought... I run a group called "samba" that all users are a member of, then I force that samba group on the public share I have on my samba box at home.

---

### Post by Sycron on 2010-03-10
I think it works.
```
[global]
workgroup = workgroup
netbios name = tuxbox
server string = Tux Box
security = user
encrypt passwords = yes
socket options = TCP_NODELAY
admin users = fred
hide dot files = yes
share modes = yes
browseable = yes

[tom]
valid users = tom
path = /var/journal
writeable = yes
browseable = yes
public = yes
printable = no
force group = fred
create mask = 000
directory mask = 000

[fred]
valid users = fred
path = /var/journal
writeable = yes
browseable = no
public = no
printable = no
force user = root
force group = fred
create mask = 600
directory mask = 700
```

Tom can copy files but can't view, rename, modify, delete them.
Fred can view, delete, rename. He can modify the file only if he uncheck the read only checkbox. But if this happens Tom can modify, view. If Fred recheck the read only checkbox, Tom will still have read access to that file. Other than that, it works!

Thanks.

---

