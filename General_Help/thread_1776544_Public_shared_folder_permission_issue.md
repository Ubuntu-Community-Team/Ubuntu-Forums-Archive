---
title: "Public shared folder permission issue"
date: 2011-06-06
forum: General Help
---

### Post by legendbb on 2011-06-06
Hi, Guy,

How to set a folder any user can write to and the same file can be overwrite by others.

I have to set up a tftp server, which sets up /tftpboot/, I've set the folder to have mod 777 and owner nobody.

Anyone can write to the folder, but my problem is if if someone write a file in this folder, as /tftpboot/user1.file.
This file has owner:group user1:user1, another user is not able to overwrite the the same file without sudo.

Is there kind of mother setting of a folder, which automatically changes ownership of it's contents? Or in other word, let folder contents to inherit folder properties. AUTOMATICALLY!, not every time manually # chmod -R 777 /tftpboot/ and # chown -R nobody /tftpboot/

Side experimental note: Looks like if I do once # chmod -R 777 /tftpboot/ and # chown -R nobody /tftpboot/
As long as I don't switch user and write file to the /tftpboot/ folder, or log out, I can overwrite the file and file's ownership won't change to user:user


Thanks,:KS

---

### Post by Apollo87 on 2011-06-07
Hello, 

I'm not too sure if what you want to do is possible.  But another solution is this:

Set the group of the folder tftpboot to be a newly created group.  Then, turn on the sgid bit for that directory:

```

chmod g+s /tftpboot

```

This will make it so any file created under that directory will have the same group as the directory itself.  So when any user creates  file, it will be in the same group.  So all you need to do after that, is add all of the users to that one group.  Everyone should then be able to write / read the files in that directory.

---

### Post by legendbb on 2011-06-07
Great thank to your knowledge,

Just add a side notes, I feel might be useful for google search,

after setting sgid, mv a file will still keep it's GID, cp a file in the sgid directory works.

---

