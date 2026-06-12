---
title: "sharing folders"
date: 2011-06-01
forum: General Help
---

### Post by dogscoff on 2011-06-01
I have a subfolder in my home folder that I want to make accessible to other users.

I gave the subfolder rwx permissions, and put both users into a group together.I changed the subfolder's group ownership to the new group. I have checked all the above using ls -l and the groups command.

The other user cannot see the contents of the subfolder in question. It says "access denied". Am I doing something wrong?

---

### Post by ruffEdgz on 2011-06-01
Well lets check your work to see where the problem is. Run the following commands so we can help:
```

getent group <group name in question>

ll -d /path/to/directory/in/question/

```
Thanks!

---

### Post by dogscoff on 2011-06-02
OK, here is the result of your commands:

home: x :1003:user1,user2    (I've inserted some spaces to prevent the bulletin board from turning the : x : it into a smiley :x: )

rwxrwx--- 70 user2 home 12288 2011-04-30 00:27 /home/user1/Photos//

and here are the results of "groups user1" and "groups user2":
user1 : user1 adm dialout cdrom plugdev lpadmin admin sambashare home
user2 : user2 fax cdrom floppy audio video plugdev fuse netdev home

and, for good measure, ls -l /home/user1 (I've only included the relevant line)
drwxrwx---  70 user1 home    12288 2011-04-30 00:27 Photos


As you can probably guess, the group I have created for this is called "home". Usernames have been changed to protect the ignorant.

So... where am I going wrong?

---

### Post by dogscoff on 2011-06-05
*bump*

Can anyone help with this? If I'm doing something wrong, can anyone tell me what it is?

If Ubuntu is behaving strangely, could someone else try it out and see if it's just my system or a bug that's common to everyone? I can't believe a bug in something as fundamental as file sharing could have slipped into a main release and I'm the only one who's noticed it.

Running Maverick 64bit.

---

### Post by kerry_s on 2011-06-05
it has to be from the top level folder down. you can't access a sub folder, if you don't have access to the folder its in.

I use the folder sharing on the right click when I'm using gnome, its the easist way to get around all those permission issues.

---

### Post by Morbius1 on 2011-06-05
Maybe it's because it's very late in the day for me but I'm getting confused.

You have a folder: /home/user1/Photos
Owner = user1
Group = home
mode = rwxrwx---

You have another user: user2 which is also a member of the home group.

Everything being equal user2 should be able to view, add to, and delete from that folder. User2 may not be able to edit the individual files within that directory ( that can be fixed ) but user2 can do everything else.

Now if the contents of /home/user1/Photos are all:
owner = user1
direcroty mode = rwx------
file mode = rw-------

Then yes user2 will see nothing.

So what is the output of the following command:
```
ls -al /home/user1/Photos
```It would be helpful if we can see at least the lines ending in "." and ".." and at least one subfolder and one file just so se can all understand the nature of the problem.

---

