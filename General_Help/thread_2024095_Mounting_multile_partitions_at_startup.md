---
title: "Mounting multile partitions at startup"
date: 2012-07-13
forum: General Help
---

### Post by Lateralus138 on 2012-07-13
Hello, I am using gnome-session-properties to automatically mount Windows partitions at startup because I have soft links to often used files over there, but it will only let me keep one of them. Every time a create the entry the other disappears. 
I use 
```

/usr/bin/udisks --mount /dev/disk/by-uuid/A*********
/usr/bin/udisks --mount /dev/disk/by-uuid/0*********

```Is it because they are the same commands? I would think that since they are not 100% the same it would allow it. Can someone tell me how this works and/or if there's a work around?

---

### Post by Cheesemill on 2012-07-13
Why not do things properly and put an entry in /etc/fstab for each of the drives you want mounted.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Lateralus138 on 2012-07-13
oh, I didn't know. I googled how to do that and that was the results I came up with from the first 3 links of my query. Thanx though I'll check it out.

---

### Post by Morbius1 on 2012-07-13
I'm all for setting it up in fstab but I'm confused by the original question. It's likely I'm reading it wrong/.

Are you trying to add multiple lines to the same startup job?

Why not create a separate job for each partition instead.

---

### Post by Rebelli0us on 2012-07-13
Just add them to fstab or use a utility like mountmanager to do it for you.

---

### Post by oldfred on 2012-07-13
I like to mount my data partitions and link the folders back into /home, others perfer to use bind.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Lateralus138 on 2012-07-13
> **Morbius1 said:**
> I'm all for setting it up in fstab but I'm confused by the original question. It's likely I'm reading it wrong/.

Are you trying to add multiple lines to the same startup job?

Why not create a separate job for each partition instead.
I did create multiple startup jobs and when I added the second one and restarted my computer it there would only one be one partition startup option like it deleted the first one.

---

### Post by Morbius1 on 2012-07-13
Did you give each one a different name? Like MountC and MountD or did you have the same name?

---

### Post by Lateralus138 on 2012-07-13
D> **oldfred said:**
> I like to mount my data partitions and link the folders back into /home, others perfer to use bind.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Well I do something like this 

```
ln  -s /media/Windowspartition1/users/me/Downloads /home/me/Downloads (I name it "downloads1"
ln -s /media/Windowspartition2/Downloads /home/me/Downloads (I name it downloads 2 etc...)
```and I do the same for Documents and Pictures etc...

---

### Post by Lateralus138 on 2012-07-13
> **Morbius1 said:**
> Did you give each one a different name? Like MountC and MountD or did you have the same name?
Yes I named one Windows Mount 1 and Windows Mount 2. At first I thought because they were similar in name that it didn't work that way, but I changed one name to just "1" and the other to just "2" and it still deleted one of them.

---

### Post by Lateralus138 on 2012-07-13
> **Rebelli0us said:**
> Just add them to fstab or use a utility like mountmanager to do it for you.
 I might use a program eventually, but I like to actually learn how things work before I take the easier route. Helps me to be able to troubleshoot problems if I actually know what's going on. Thanks though, I'll check that mountmanager out. 

I know Windows better than I know the back of my hand and now it's time to master Linux ;p

---

### Post by Lateralus138 on 2012-07-13
Can I assume I can mount different partitions to the same mount point?

```
/dev/sda2 /mnt/windows ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda7 /mnt/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```etc...

---

### Post by Morbius1 on 2012-07-13
No you can not. And I would change those options as well but that's up to you.

[COLOR=Blue]**EDIT**[/COLOR]: I would change them to this if it was my system:
```
UUID=A********* /mnt/WinC ntfs defaults,locale=en_US.utf8,uid=1000,windows_names 0 0
UUID=O********* /mnt/WinD ntfs defaults,locale=en_US.utf8,uid=1000,windows_names 0 0
```You would have to create the /,nt/WinC and /mnt/WinD mountppoints first.

---

### Post by Lateralus138 on 2012-07-13
> **Morbius1 said:**
> No you can not. And I would change those options as well but that's up to you.
Ok so maybe like this:
```
/dev/sda2 /mnt/windows1 ntfs defaults,locale=en_US.utf8 0 2 
/dev/sda7 /mnt/windows2 ntfs defaults,locale=en_US.utf8 0 2
```

Edit:
```
/dev/sda2 /mnt/windows1 ntfs defaults,umask-000,dmask=000,fmask=111,locale=en_US.utf8 0 2 
/dev/sda7 /mnt/windows2 ntfs defaults,umask-000,dmask=000,fmask=111,locale=en_US.utf8 0 2 
```

---

### Post by Morbius1 on 2012-07-13
Sorry, posted with an edit right past you.

Yes, different mount points but I would go back to using uuid's instead of the /dev/sdxy. "ntfs" or "ntfs-3g" are both the same in Ubuntu. And "windows_names" prevents you from adding a file in Linux with a name Windows cannot interpret. And keep the last digit as zero not 2. ANd uid=1000 will make you the owner of the mounted partition not root.

---

### Post by Lateralus138 on 2012-07-13
> **Morbius1 said:**
> Sorry, posted with an edit right past you.

Yes, different mount points but I would go back to using uuid's instead of the /dev/sdxy. "ntfs" or "ntfs-3g" are both the same in Ubuntu. And "windows_names" prevents you from adding a file in Linux with a name Windows cannot interpret. And keep the last digit as zero not 2. ANd uid=1000 will make you the owner of the mounted partition not root.

"windows_names"? not sure what part you're talking about and uid=1000? What part is that?

This is what I have so far
```

UUID="AA8EE2508EE2149B /mnt/part1 ntfs-3g defaults,locale=en_US.utf8 0 0
UUID="0C6249226BC6107F /mnt/part2 ntfs-3g defaults,locale=en_US.utf8 0 0

```

---

### Post by Morbius1 on 2012-07-13
One of us need to slow down ):P

My recommendation was this:
```
UUID=A********* /mnt/WinC ntfs defaults,locale=en_US.utf8,uid=1000,windows_names 0 0 
UUID=O********* /mnt/WinD ntfs defaults,locale=en_US.utf8,uid=1000,windows_names 0 0
```
Note on umask, dmask, and fmask: dmask and fmask are components of umask. Don't use all three at the same time.

---

### Post by Lateralus138 on 2012-07-13
> **Morbius1 said:**
> One of us need to slow down ):P

My recommendation was this:
```
UUID=A********* /mnt/WinC ntfs defaults,locale=en_US.utf8,uid=1000,windows_names 0 0 
UUID=O********* /mnt/WinD ntfs defaults,locale=en_US.utf8,uid=1000,windows_names 0 0
```Note on umask, dmask, and fmask: dmask and fmask are components of umask. Don't use all three at the same time.

Ok I think I am getting it

```

UUID="AA8EE2508EE2149B /mnt/part1 ntfs defaults,locale=en_US.utf8,uid=1000,windows_names 0 0
UUID="0C6249226BC6107F /mnt/part2 ntfs defaults,locale=en_US.utf8,uid=1000,windows_names 0 0

```as for umask I read this:

"ntfs/vfat = permissions are set at the time of mounting the partition  with umask, dmask, and fmask and can not be changed with commands such  as chown or chmod. I advise dmask=027,fmask=137 (if you user umask=000 all your files will be executable). More permissive options would be dmask=000,fmask=111."

so if I want to be able to execute files on the windows partition I should just use umask=000 alone like this:

```

UUID="AA8EE2508EE2149B /mnt/part1 ntfs defaults,locale=en_US.utf8,uid=1000,windows_names,umask=000 0 0
UUID="0C6249226BC6107F /mnt/part2 ntfs defaults,locale=en_US.utf8,uid=1000,windows_names,umask=000 0 0

```?

---

### Post by Morbius1 on 2012-07-13
This is kind of confusing but yes a "umask=000" will make all folders and files executable. But "umask=000" is how an ntfs partition will mount natually so it isn't needed. That said it's best to keep it in fstab as you have done just as a reminder of how you mounted it.

There is one more tiny thing though:
> UUID=[COLOR=Red]**"**[/COLOR]AA8EE2508EE2149B 
 UUID=[COLOR=Red]**"**[/COLOR]0C6249226BC6107FGet rid of those quote marks in front of the first character of your UUID

---

### Post by Lateralus138 on 2012-07-13
> **Morbius1 said:**
> This is kind of confusing but yes a "umask=000" will make all folders and files executable. But "umask=000" is how an ntfs partition will mount natually so it isn't needed. That said it's best to keep it in fstab as you have done just as a reminder of how you mounted it.

There is one more tiny thing though:
Get rid of those quote marks in front of the first character of your UUID
Awesome thanx, now I have a better understanding of it all. That quotation mark was a typo I think and kept there from copying and pasting, but thanks for pointing it out, I did know that, but might have missed it. 

Thanx to everyone for all of your help.

---

### Post by Morbius1 on 2012-07-13
Just make sure you have created the /mnt/part1 and /mnt/part2 directories first. And if you run the following command it will test for errors and if there are none mount the partition without requiring a reboot:
```
sudo mount -a
```If there are problems it's best to find them before a reboot.

---

### Post by Lateralus138 on 2012-07-13
> **Morbius1 said:**
> Just make sure you have created the /mnt/part1 and /mnt/part2 directories first. And if you run the following command it will test for errors and if there are none mount the partition without requiring a reboot:
```
sudo mount -a
```If there are problems it's best to find them before a reboot.

Yep yep, I already created and checked, and but always good to double check.

---

### Post by Morbius1 on 2012-07-13
Id still like to know why this didn't work:
> /usr/bin/udisks --mount /dev/disk/by-uuid/A********* 
/usr/bin/udisks --mount /dev/disk/by-uuid/0*********I have in the past done something similar using a different mechanism:
gvfs-mount -d `readlink -f /dev/disk/by-uuid/A*****`, set up multiple startup entries and as I remember it worked. I'll have to play with this when I have more time. Doubt I will ever use it but you never know.

---

### Post by Lateralus138 on 2012-07-13
> **Morbius1 said:**
> Id still like to know why this didn't work:
I have in the past done something similar using a different mechanism:
gvfs-mount -d `readlink -f /dev/disk/by-uuid/A*****`, set up multiple startup entries and as I remember it worked. I'll have to play with this when I have more time. Doubt I will ever use it but you never know.
Yeah I'd like to know too. I kept trying to make 2 entries with different names over and over again and it would keep deleting one of them. I am pretty sure it was deleting the the very first entry though I wouldn't quote me on that. As for the fstab way I have done it and rebooted and they both boot just fine and fully functional. Now that I've created my new mount points I now have to re-link al of my soft links because they were originally mounted in media.

---

