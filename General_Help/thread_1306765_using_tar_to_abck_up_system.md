---
title: "using tar to abck up system"
date: 2009-10-30
forum: General Help
---

### Post by kartal on 2009-10-30
Hi

I am having terrible time here with "tar" command. I did read multiple forums, multiple posts and the help to get this done, without any leading success. 

The main problem is that the backup stops at 4.2 gb so I thought I should split, maybe it helps but I cannot figure out the proper use for the split.


Here is my command line at the moment (This command works without the split option, which stops around 4.2 gb without an error. It looks like it just quits not sure. Here where it stops "/opt/thunderbird/libprldap60.so" and there is no further message in the root termnal.



tar -cvpzf --exclude-from="/home/user/exclude_list.txt" / | split -d -b 3900m - /media/disk/Ubun_split_30Oct.tar.gz

This command says that no such file or folder regarding the exclude_list, which is not true. I tried without quotes as well.

Any ideas?

thanks

---

### Post by lensman3 on 2009-10-30
You are using:

tar -cvpzf --exclude-from="/home/user/exclude_list.txt" /

Instead try:

 tar --exclude-from="/home/user/exclude_list.txt" cvpzf / - | ...

where the last dash means stdout.  The other thing I changed was to move the --exclude in front of the cvpzf.

Also the file that it appears to hang on, is it a "ln -s" file.  I have see errors when wild cards (or wild card like) tend to follow the link and hang. 

Does your backups allow the use of -xdev option.  Where backups stay on the same partition.  The xdev option is main reason I set small partitions, so I can backup!

I use a program called "star" for super-tar for my backups.  You will have to download to install this program. Star has been around since the '80s.

---

### Post by kartal on 2009-10-30
Hi

Thanks for the reply and help.

This does not work for me, very frustrating to be honest.

tar --exclude-from="/home/user/exclude_list.txt" -cvpzf / - | split -d -b 3900m - /media/disk/Ubun_split_30Oct.tar.gz


"tar: -: Cannot stat: No such file or directory
tar: /: Cannot open: Is a directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
"

---

### Post by lavinog on 2009-10-30
the argument after the f is the archive name, you have the root folder in this place.  Try this:
```

tar --exclude-from="/home/user/exclude_list.txt" -cvpzf /media/disk/Ubun_split_30Oct.tar.gz / - | split -d -b 3900m - 

```

---

### Post by kartal on 2009-10-30
> **lavinog said:**
> the argument after the f is the archive name, you have the root folder in this place.  Try this:
```

tar --exclude-from="/home/user/exclude_list.txt" -cvpzf /media/disk/Ubun_split_30Oct.tar.gz / - | split -d -b 3900m - 

```

Hi

Thanks for the suggestion, but that did not work really. It proceeded couple steps and stopped

"tar: Removing leading `/' from member names
tar: Removing leading `/' from hard link targets
tar: /dev/log: socket ignored
tar: /home/user/.gvfs: Cannot stat: Permission denied
^C
"

---

### Post by lavinog on 2009-10-31
what does your exclude list contain?  It looks like you are not excluding everything that you need to exclude.

What type of backup are you trying to do?
Would you be better off making a partition image?

---

