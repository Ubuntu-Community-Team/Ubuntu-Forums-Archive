---
title: "/home backup"
date: 2010-08-21
forum: General Help
---

### Post by smarmytime on 2010-08-21
Hi guys - I just installed Ubuntu 10.04 on my pc. I'm not exactly new to linux; I used Mandrake as my sole os on my home PC for several years. But that was some time ago, and it seems I've forgotten a great deal. Also, some things are just different, as one might expect.

Now, I absolutely hate to admit this, but it seems I've forgotten how to back up my home directory...or at least I've forgotten what the output tar is giving me means. Here is what I'm typing in on the command line:


smarmy@smarmy-desktop:~$ sudo tar -cf home.tar /home/smarmy

And here is what I'm getting:


tar: Removing leading `/' from member names
tar: /home/smarmy/.config/google-chrome/SingletonSocket: socket ignored
tar: Removing leading `/' from hard link targets
tar: /home/smarmy/.cache/google-chrome/Cache: file changed as we read it
tar: /home/smarmy/.dropbox/command_socket: socket ignored
tar: /home/smarmy/.dropbox/iface_socket: socket ignored
tar: /home/smarmy/.gvfs: Cannot stat: Permission denied
tar: /home/smarmy/home.tar: file is the archive; not dumped
tar: Exiting with failure status due to previous errors
smarmy@smarmy-desktop:~$ 


Now, I get that the chrome cache file changed, which is no big deal, that's certainly not something I'm concerned with, as far as backing my system up goes. But I'm not sure about the .gvfs. Some light reading has led me to believe that nothing is actually stored under it, so it's no big deal that it's not being backed up, correct? 

The line that really concerns me is the last one. It's exiting with failure status - so that means that my backup has failed? If I were to try to untar this to use a backup of my /home, would it not work correctly? Is there a more appropriate command that I could use other than what I did use?

Thanks for any help or guidance.

---

### Post by WorMzy on 2010-08-21
I think the problem is that you're trying to create the backup file in the folder that you're trying to backup. Try making the backup in /home or on another partition.

---

### Post by vdawg on 2010-08-21
This is what I used to use to backup my system, hope it helps!

```
tar -cvvzf /home/snoop/snoop.tar.gz /home/snoop/ --totals --ignore-failed-read -X /home/snoop/exclude
```

---

### Post by _0R10N on 2010-08-21
Well, the message about removing leading `/' from member names comes out because you're specifying the source folder with its full path. Try this:
```

cd /home
sudo tar -cf /tmp/home.tar smarmy

```That should do the trick.

As for the error concerning the gvfs directory access' denial, that's because the folder has only permission for the owner. No permission is usually given to group and others. Make sure you're logged in as smarmy.

---

### Post by _0R10N on 2010-08-21
I've just tried to back up my ".gvfs" folder into a tar file (with sudo) without any trouble/complains. So I guess you've been trying to back up your files logged as another user.

---

### Post by smarmytime on 2010-08-21
Thanks for the tips, guys. 

@vdawg - that looks closest to what I used to use, thanks for that!

@_0R10N - I'm the only user on this box, so I can't be logged in as anybody else. Thanks for the tip, though - another way to handle the problem is always good.

---

