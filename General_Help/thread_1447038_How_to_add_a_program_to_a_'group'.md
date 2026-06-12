---
title: "How to add a program to a 'group' ?"
date: 2010-04-04
forum: General Help
---

### Post by iMisspell on 2010-04-04
This could very well be a samba problem but i still would like to know if it is possible to add a program to a user group.

Example:
If you want to add a user to a group you would do:
usermod -a -G [group] [username]

Can you do that with a program ?
program_mod -a -G [group] geany

I use Geany as my editor when working with bash scripts.
If im working on a file which is stored on a mounted drive (samba and fstab) i get a bunch of "cifs..." files with the following content in them when i run (F5) the script from Geany.
```

#!/bin/sh

rm $0

"./file_name_im_working_with.sh"

echo "

------------------
(program exited with code: $?)" 		


echo "Press return to continue"
#to be more compatible with shells like dash
dummy_var=""
read dummy_var

```

But if im working with files that are local on my desktops hardrive, these "cifs..." files delete themselves.

So im thinking this is a permissions problem and if i can add Geany to the same group as im logged in it will resolve this problem.

The same thing happens if i go and try an un-tar something which is stored on the mounted drive. I then will un-tar it by sshing to the server.


Any insight would be great.

_

---

### Post by spiderbatdad on 2010-04-04
chown allows you to specify an owner:group for a program. While users can be members of multiple groups, I am not aware of programs having the same capacity. Hopefully someone will correct me if I'm wrong.
Of course programs have permissions for owner/group/other respectively, for example rwxr-xr-x (755), and these permissions can be modified with chmod.

---

