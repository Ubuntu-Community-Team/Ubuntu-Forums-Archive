---
title: "Cannot Open Folders"
date: 2012-02-17
forum: General Help
---

### Post by Forrest38 on 2012-02-17
Hello All,

Problems similar to mine have been posted about on the forum but none seem to match mine exactly, and none of the solutions suggested so far to me have been successful so here it is:

I just installed Linux today on my PC(I switched over from windows 7 after getting a critical virus on my computer) and I transferred about 50 gigs worth of files into a sub-folder of the "Home" folder. At first, I was able to access/use the files like normal, but when I tried to log in after my first login I found that whenever I clicked the "Home" folder the computer would be unresponsive and never fully successfully open the Home Folder. Instead both Nautilus and the Folder I was trying to open would take up huge amounts of my computer resources and I would have to force shut them down using "Htop". Trying to open up the "Trash" folder gets me a similar reaction. I have no idea how to open up a single file stored in the "home" folder or its subfolders.

I was also unable to open the folder using gnome-open /home*/username*/. When I do I get the following error:
(nautilus:7142): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Thanks for any suggestions

---

### Post by ld.4lpha on 2012-02-17
Do you have Samba installed/enabled?

Can you open files via the terminal?

What are the current permissions on your files?

---

### Post by Bucky Ball on 2012-02-17
What release are you using???

---

### Post by Forrest38 on 2012-02-18
I am using Ubuntu version 11.1, I do not have samba and it appears I have read/write permissions for all my files under my username

---

### Post by ld.4lpha on 2012-02-18
What happens if you try to open a file via the terminal?

For example, 

```
gedit /path/to/textfile
```

---

### Post by Forrest38 on 2012-02-18
I am beginning to think this might have to with permissions: when I tried to open a file with VLC using :

~$ >VLC *filepath.flv* 

I received a message saying "Permission Denied".

I was however, able to go into the folder from VLC and then play the file(which I just figured out I could do). I also can use other programs that open files(such as openoffice) and then open files that way. it is certainly a workaround for now, but it is annoying to not have direct access.

---

### Post by ld.4lpha on 2012-02-18
In your terminal try:

```
chown -R {yourUsername} /home/{yourUsername}
```

If that fails, try with sudo.

After you've taken ownership of everything in your home directory, see what happens with Nautilus.

---

### Post by Forrest38 on 2012-02-19
using both the regular user mode and sudo when I typed in:

chown -R {username} /home/{username}

I receive the same error:

chown: cannot access `/home/{username}/.gvfs': Permission denied

If I try and select my "home" folder nautilus continues to simply take up resources and I have to force quit the home folder

---

### Post by ld.4lpha on 2012-02-19
Weird.

Can you do

```
sudo chmod -R 777 /home/{username}
```

---

### Post by Forrest38 on 2012-02-19
> **ld.4lpha said:**
> Weird.

Can you do

```
sudo chmod -R 777 /home/{username}
```

nope, same "Permission Denied" error. Could this have anything to with the fact I transferred a large amount of files from windows to my computer?

---

### Post by flemur13013 on 2012-02-19
Try 
```
$ sudo -i 
```
then the chmod.

---

### Post by AnWi on 2012-02-19
Got a related problem!

All of a sudden my shared NTFS partition is now ReadOnly! This happened after running Update manager yesterday!
Reboot don't help. Root cannot change permission.

Please help!

---

### Post by Forrest38 on 2012-02-19
Nautilus seemed to be having troubles dealing with all the files I had transferred over, so I found a more permanent work-around. Now I am using Thunar as my file manager and I have no trouble navigating/manipulating my folders. So I guess it is solved

---

### Post by ld.4lpha on 2012-02-19
Glad it's working for you.  

Something is definitely screwy there; you might want to figure out the underlying issue so it doesn't manifest itself in some other way in the future.



LD

---

### Post by Bucky Ball on 2012-02-19
That's great Thunar is working for you, but just wondering if you were actually putting in *your* username with the other instructions from earlier??? For example:

```
/home/frank
```... where 'frank' is your username, rather than entering:

```
/home/{username}
``` ;)

---

