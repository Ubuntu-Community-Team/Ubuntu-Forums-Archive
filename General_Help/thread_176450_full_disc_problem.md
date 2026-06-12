---
title: "full disc problem"
date: 2006-05-14
forum: General Help
---

### Post by ephman on 2006-05-14
hello,

all of a sudden i went from having 20gig free to 93mb.  something ate up a whole lot of space all of a sudden.  i'm wondering if there'sa any command i can use that will help find the largest file on my computer.  i have a sneaky idea it might be just one large file.

thank you much,
ephman

---

### Post by tonyr on 2006-05-14
The brute force way is in a terminal:
```

cd /
sudo ls -lR | sort +4r | head

```

Another way is with the **find** command, also in a terminal:
```

sudo find -P -size +10M -ls

```

In this case th +10M means "greater than 10 megabytes". You can use 
whatever number you want, and use G for Gigabytes.  See **man find**
for more details about the **-size** option.  Both of these do a full directory
tree search on the whole disk, so it could take a while.

If you are looking for a gui based tool to do this, I don't know if there is one.

---

### Post by tonyr on 2006-05-14
[QUOTE=tonyr]
If you are looking for a gui based tool to do this, I don't know if there is one.
[/QUOTE]

I lied.  It is **kfind** in Kubuntu.  I'm not sure if there is one in Ubuntu (Gnome),
but if there is it might be named **gfind** or **gnofind**.  I'll look around.

---

### Post by ephman on 2006-05-15
hi,

i tried both the commands you suggested, and everything seems to look normal.  but it's impossible, i lost 20gig of space.  any other help would be really be welcomed. 

thanks,
ephman

---

### Post by kaamos on 2006-05-15
This will get you a little space
```
sudo apt-get clean
```
and this should get you some info where all the space is going to:
```

cd /
sudo du -hc --max-depth=1
```
You can change folders and vary the max-depth to get further results.

---

### Post by nanotube on 2006-05-15
hmm, well, first thing to do is compare the amount of free space that command df returns (just run "df"), with the output of command "sudo du -sk /", which counts up the total size of all the files. if there is a discrepancy there, then it's not any 'files' that ate up the space, but something funny going on with your partitions.

edit: and by the way, of course, if this is happening on a separate partition, such as /home, you would do put /home into du -sk, instead of /. :)

---

### Post by tonyr on 2006-05-15
It's also possible that the 20G is distributed over several files.  **kaamos's** 
suggestion to do **sudo apt-get clean**  gets rid of all the package files
in **/var/cache/apt/archives** where ALL of the downloaded update packages
get stashed, accumulating forever unless you do housekeeping.  Another candidate
is **/var/log** where all of the system log files live.   Sometimes things going nasty in
you system generate a lot of output in several log files at the same time.  

What apps/programs do you use?   When you say **suddenly**, was it
a matter of minutes, or overnight, or several hours, or right after boot,
or what?  What commands/utilities are you using to monitor disc space?

---

### Post by ephman on 2006-05-15
hi,

thanks.  pieced all your suggestions together and found the 2 hidden files causing all my grief.

ephman

---

### Post by nanotube on 2006-05-15
so, out of curiosity... what were they?

---

### Post by anakiki on 2006-05-19
[quote=nanotube]hmm, well, first thing to do is compare the amount of free space that command df returns (just run "df"), with the output of command "sudo du -sk /", which counts up the total size of all the files. if there is a discrepancy there, then it's not any 'files' that ate up the space, but **_something funny going on with your partitions _** .

edit: and by the way, of course, if this is happening on a separate partition, such as /home, you would do put /home into du -sk, instead of /. :)[/quote] 
I think i do have this "something funny going on with partitions" situation here, and I would like to know more about it... Just to make it easier, here are the outputs: (As I understand, the two red numbers should be equal... )

```

root@ubuntu:/# du -sk /
du: `/proc/1372/task': No such file or directory
du: `/proc/1372/fd': No such file or directory
[color="Red"]4142824[/color] /
root@ubuntu:/# df
Filesystem  1K-blocks  Used    Available   Use%  Mounted on
/dev/hda5   5534416      [color="Red"]3730156[/color]   1523128     72%     /
tmpfs       253020       0         253020      0%       /dev/shm
tmpfs       253020       13536     239484      6%    /lib/modules/2.6.12-10-amd64-generic/volatile

```

---

### Post by jones_jj on 2006-05-19
ephman, very curious what were you doing to cause your problem?  It sounded almost like a coredump of some kind happened to me.  Do you do any programming?

To everyone else, thanks for all the tips on how to clean up a drive.

---

### Post by ephman on 2006-05-20
hi,

i imported a large media file into kino, and was converting it to something else.  i killed the app, and forgot about the file.  duh!  since the file was hidden i couldn't find it.  i didn't even know it was associated with this action i took.  so the help here was great, helped narrow down where this was.

thanks,
ephman

---

### Post by sinkxdie on 2006-05-20
Edit: i don't know how to delete a post.

---

