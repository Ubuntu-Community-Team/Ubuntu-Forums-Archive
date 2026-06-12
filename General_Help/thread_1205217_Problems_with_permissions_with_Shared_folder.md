---
title: "Problems with permissions with Shared folder"
date: 2009-07-05
forum: General Help
---

### Post by Ifaistos on 2009-07-05
I have a HD, 120GB which is mounted at /home/myloginname/120GB.
I have installed SAMBA, and have shared it on the LAN under the name: ubuntu120GB

My windows machine has full access to that folder/HD.

It can write/delete files and directories.

I created a file and a directory from my Windows machine to make sure it can.  The problem is that I can't delete the file nor the directory when I am on the Linux machine!! It says that the owner is noone.

Strange thing is that I can delete the file and the directory from my windows machine.

I know that I can : 
chown -R to that specific folder and make it my own.  But I don't want to be doing this every time someone decides to make a folder in the HD and I want to delete it.

is there any way I would have full access to anything that a remote user is doing in my own 120GB folder/HD?

I hope I didn't confuse you...

Thanks everyone :-)

---

### Post by Ifaistos on 2009-07-05
bump..

---

### Post by loomsen on 2009-07-05
Depending on your filesystem... You say your windows machine is able to access it, so I assume you're using ntfs or fat as FS. 
Both lacking the ability to handle permissions...

---

### Post by Jebtrix on 2009-07-05
Open nautilus goto /var/lib/samba/usershares
Each file in here corresponds to a share created with nautilus

Post the contents of the share in question to see if anything is screwy.

---

### Post by synapsys on 2009-07-05
> **loomsen said:**
> Depending on your filesystem... You say your windows machine is able to access it, so I assume you're using ntfs or fat as FS. 
Both lacking the ability to handle permissions...

Not true... ntfs can 'handle' permissions.

---

### Post by Jebtrix on 2009-07-05
What are the permissions for the shared folder in linux? Did you share from Nautilus or manually with samba?

One thing to try
chmod g+s <sharedfolder>
This ensures that all files will be created with the group that owns the directory. 

Make sure you the user your logged into linux is a part of that group.

In smb.conf (or /var/lib/samba/usershares/<sharename> ) try adding

force create mode = 0660
force directory mode = 0770

---

### Post by Jebtrix on 2009-07-06
I was able to easily reproduce this same problem. After a bunch of fiddling here is what works.

gksudo gedit /etc/samba/smb.conf

under [global] section add:

```
force user = <yourusernamehere>
force group = <yourusernamehere>
create mask = 770
force create mode = 0770
force directory mode = 0770
directory mask = 770
directory security mask = 0000
directory security mode = 777
force directory security mode = 770
```

Adding all that isn't overkill, without each setting it won't work as expected. Unfortunately using "usershare allow full config = yes" and editing the /var/lib/samba/usershares/<sharename> does not work, it has to be in smb.conf. 

Restart samba after editing smb.conf
```
sudo /etc/init.d/samba restart
```

Cheers.

---

### Post by Ifaistos on 2009-07-06
wow Jebtrix :-)

Thank you for all the time you've invested.
I will try it out, as soon as I go back home, on my Linux Machine.

Thanks again

---

