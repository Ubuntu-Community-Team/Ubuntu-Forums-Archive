---
title: "errors in BleachBit"
date: 2011-09-02
forum: General Help
---

### Post by qwertyjjj on 2011-09-02
I get lots of these errors in Bleach bit GUI.
Does it need to be run as root?
How can I do that from the GUI?

```

[Errno 13] Permission denied: '/usr/share/locale/ca/LC_MESSAGES'
[Errno 13] Permission denied: '/usr/share/locale/ca'
[Errno 13] Permission denied: '/usr/share/locale/fur/LC_MESSAGES/vlc.mo'
[Errno 13] Permission denied: '/usr/share/locale/fur/LC_MESSAGES'
[Errno 13] Permission denied: '/usr/share/locale/fur'
[Errno 13] Permission denied: '/usr/share/locale/pl/LC_MESSAGES/vlc.mo'
[Errno 13] Permission denied: '/usr/share/locale/pl/LC_MESSAGES/lives.mo'
[Errno 13] Permission denied: '/usr/share/locale/pl/LC_MESSAGES/sound-juicer.mo'

```

---

### Post by F.G. on 2011-09-02
it looks like you probably do need to run it as root, which can be done by typing sudo before the command, if you use the terminal.  it's probably a bad idea to make it launch automatically as root.

---

### Post by qwertyjjj on 2011-09-02
Nope, the errors still occur:

```

[Errno 13] Permission denied: '/var/cache/apt/archives/linux-headers-2.6.35-30_2.6.35-30.56_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/lives-data_1.3.10-1_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/linux-image-2.6.35-30-generic_2.6.35-30.56_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/firefox-gnome-support_3.6.21+build1+nobinonly-0ubuntu0.10.10.1_i386.deb'

```

```

': u'delete'}, {'regex': u'^Thumbs\\.db$', 'path': '/home/jason', 'cache': False, 'command': u'delete'}, {'regex': u'^Thumbs\\.db:encryptable$', 'path': '/home/jason', 'cache': False, 'command': u'delete'}]
debug: searches= {'/home/jason': [u'^\\.DS_Store$', u'\\.[Bb][Aa][Kk]$', u'[a-zA-Z]{1,4}~$', u'^~wr[a-z][0-9]{4}\\.tmp$', u'^ppt[0-9]{4}\\.tmp$', u'^Thumbs\\.db$', u'^Thumbs\\.db:encryptable$']}
debug: elapsed time: 5086 seconds
Traceback (most recent call last):
  File "/usr/share/bleachbit/bleachbit/Worker.py", line 242, in run
    self.ui.worker_done(self, self.really_delete)
  File "/usr/bin/bleachbit", line 387, in worker_done
    notify.show()
glib.GError: Unable to connect to server
debug: re-enabling swap
The program 'bleachbit' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 47063 error_code 9 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```

---

### Post by TeoBigusGeekus on 2011-09-02
Try with 
```
gksu bleachbit
```

---

### Post by qwertyjjj on 2011-09-02
> **TeoBigusGeekus said:**
> Try with 
```
gksu bleachbit
```

I run that but it brings up the GUI but doesn;t clean the same things. Seems to list the main core items but not all the extras like Thunderbird, FF, OPera, Emule, etc.

---

### Post by TeoBigusGeekus on 2011-09-02
> **qwertyjjj said:**
> I run that but it brings up the GUI but doesn;t clean the same things. Seems to list the main core items but not all the extras like Thunderbird, FF, OPera, Emule, etc.

Of course it doesn't, unless you've used these apps as root.
Bleachbit should be run as a normal user and as root (with gksu).

For some more info about sudo/gksu, see [here]("http://www.psychocats.net/ubuntu/graphicalsudo").

---

### Post by qwertyjjj on 2011-09-02
Still there:

```

[Errno 13] Permission denied: '/var/cache/apt/archives/thunderbird_3.1.12+build1+nobinonly-0ubuntu0.10.10.1_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libcvaux2.1_2.1.0-2_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libcv2.1_2.1.0-2_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/ecryptfs-utils_83-0ubuntu3.1maverick_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libwebkit-1.0-2_1.2.7-0ubuntu0.10.10.1_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libsox-fmt-alsa_14.3.1-1build1_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/frei0r-plugins_1.1.22git20091109-1.1_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/linux-headers-2.6.35-30_2.6.35-30.56_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/lives-data_1.3.10-1_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/linux-image-2.6.35-30-generic_2.6.35-30.56_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/firefox-gnome-support_3.6.21+build1+nobinonly-0ubuntu0.10.10.1_i386.deb'

```

---

### Post by qwertyjjj on 2011-09-02
> **TeoBigusGeekus said:**
> Of course it doesn't, unless you've used these apps as root.
Bleachbit should be run as a normal user and as root (with gksu).

For some more info about sudo/gksu, see [here]("http://www.psychocats.net/ubuntu/graphicalsudo").

The errors occur whether it#s gksu or as a normal user.

---

### Post by qwertyjjj on 2011-09-04
Any ideas why all these files are locked up regardless of whether I run as root or not?

---

### Post by qwertyjjj on 2011-09-12
yoo hoo :)

---

### Post by Jouke74 on 2011-09-12
As explained there are two 'persons'for which you need to run the program: you as user (no sudo needed) and as root (sudo needed). In both runs Bleachbit will find the same files to delete and unique files to delete. One, either user and root, will sometimes have access to delete the files. Hence in both cases errors will occur as Bleachbit is trying to delete files which only the other user is able to access. 

In case the files are created by a third user (or access rights have been changed) Bleachbit won't be able to delete those without that users consent. So check the rights of those files or delete them manually.

To clean the apt cache you can run: sudo apt-get autoclean.

---

### Post by itagomo on 2012-06-19
from terminal, try:

sudo rm -rf /usr/share/locale/*

will delete all files/folders under locale

we have the same problem .. running BB as root will not look for the files created by 'normal user' (you) .. using BB as 'normal user' will get Permission Denied errors .. crazy :D

---

