---
title: "Can copy a directory but not files over Samba"
date: 2009-11-02
forum: General Help
---

### Post by bigred1 on 2009-11-02
I have exposed some directories from my Jaunty installation using Samba, giving all possible permissions.

These shared directories have all permissions (*rwxrwxrwx *) and are owned by the primary (and only) user of this Ubuntu machine.

When I copy in a directory of files from a Windows machine over the LAN (no password needed), the directory gets copied but the files in it do not. I am told that there is a permissions error. 

I find that  the successfully-copied directory comes onto the Ubuntu machine with owner *nobody *and group *nogroup*. and permissions rw-rw-rw-

How can I copy entire directories into my Ubuntu machine? I think that this has to do with my permissions.

---

### Post by alphaniner on 2009-11-02
The copied directory doesn't get e**x**ecute permissions, which means nothing can be copied into it.  Not sure why that is happening though.  Did you create the share through Nautilus?  If so, what is the content of the /var/lib/samba/usershares/<shared_folder> file?

---

### Post by bigred1 on 2009-11-02
Thanks. So the question is why execute permissions are not automatically granted for Samba-copied directories.

> **alphaniner said:**
> Did you create the share through Nautilus? If so, what is the content of the /var/lib/samba/usershares/<shared_folder> file?
Yes. 
 
Here is file **/var/lib/samba/usershares/music**

[B]#VERSION 2
path=/home/artemis/Music
comment=
usershare_acl=S-1-1-0:F
guest_ok=y[/B]
 

The two other files in **/var/lib/samba/usershares/**  have identical **usershare_acl** and **guest_ok **lines.

---

### Post by dcstar on 2009-11-02
> **bigred1 said:**
> 
..........
Here is file **/var/lib/samba/usershares/music**

[B]#VERSION 2
path=/home/artemis/Music
comment=
usershare_acl=S-1-1-0:F
guest_ok=y[/B]
 

The two other files in **/var/lib/samba/usershares/**  have identical **usershare_acl** and **guest_ok **lines.

I would not share any folders in the /home tree because the linux security system likes to control the permissions of these.

Try setting up new folders outside of /home and see what happens.

---

### Post by bigred1 on 2009-11-03
I created folder /usr/sambaShare with permissions 777 and shared it fully (all access) through Nautilus. 

The same phenomenon occurred.

---

