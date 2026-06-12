---
title: "remove uTorrent 3.0 server"
date: 2011-09-12
forum: General Help
---

### Post by anc123 on 2011-09-12
hi,
   I am completely new user to Linux using Ubuntu 11.04.
   I have recently installed uTorrent server 3.0 and have no clue of how to remove it.
   It is using my 8080 port I want to completely remove it.
   Plz help uninstalling it.

   Thanx in advance.

---

### Post by TeoBigusGeekus on 2011-09-12
How did you install it?

---

### Post by anc123 on 2011-09-12
I downloaded it in the form of tar.gz and unpacked it.
It contained a file called utserver, I just did a double click.
After this it got installed at [http://localhost:8080/gui](http://localhost:8080/gui).

---

### Post by ubudog on 2011-09-12
Try:
```
sudo apt-get purge utserver
```

Also, can you post the output of:
```
which utserver
```

---

### Post by TeoBigusGeekus on 2011-09-12
Do you still have the tar.gz archive?
Perhaps it contains an info, or readme, or whatever file with instructions for installation and uninstallation.

---

### Post by ubudog on 2011-09-12
> **TeoBigusGeekus said:**
> Do you still have the tar.gz archive?
Perhaps it contains an info, or readme, or whatever file with instructions for installation and uninstallation.

+1

The README file normally has instructions.

---

### Post by anc123 on 2011-09-12
"sudo apt-get purge utserver" gives :
Unable to locate utserver

I've checked the docs, it contains two pdf files with nothing of uninstallation in its table of contents.

One more thing, when I double clicked utserver, I file named "settings.dat" was created in the same folder.
I even moved the entire folder to trash, but the server is still running.  :(

---

### Post by TeoBigusGeekus on 2011-09-12
Can you post us a link to the archive?

---

### Post by anc123 on 2011-09-12
here it is

[http://www.utorrent.com/downloads/complete?os=linux](http://www.utorrent.com/downloads/complete?os=linux)

---

### Post by ubudog on 2011-09-12
Permanently delete it from the trash.

Post the output of:
```
ps ax | grep utserver
```

---

### Post by papibe on 2011-09-12
If you downloaded it from the utorrent site ([here]("http://www.utorrent.com/downloads/linux")), it doesn't have an install or uninstall. You just unpack it, run it from the terminal, and access it from the browser.

To uninstall it, close the web ui, stop utserver (Control+C), and delete all related files.

Hope it helps,
Regards.

Note: if you double click utserver instead of running it on the terminal, you may need to kill it:
```
$ killall utserver
```

---

### Post by anc123 on 2011-09-12
After completely deleting it from trash, and using your command, the outut is:

2014 ?        Sl     0:41 /home/anchit/Softwares/uTorrent/utorrent-server-v3_0/utserver
 8930 pts/0    S+     0:00 grep --color=auto utserver

---

### Post by ubudog on 2011-09-12
Ok, now do:
```
kill -9 2014
```

And the server should be gone!

---

### Post by anc123 on 2011-09-12
I got it solved...
I completely removed the folder and did
$ killall utserver

thanks to all
thanks for help

---

### Post by ubudog on 2011-09-12
Great!

---

