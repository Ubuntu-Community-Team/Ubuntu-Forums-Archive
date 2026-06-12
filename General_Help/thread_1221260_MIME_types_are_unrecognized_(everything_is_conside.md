---
title: "MIME types are unrecognized (everything is considered 'text/plain')"
date: 2009-07-23
forum: General Help
---

### Post by mcpancakes on 2009-07-23
hello all,

It seems my installation has suddenly stopped the 'look at file extension; from there, determine MIME type' process. any file (.jpg, .avi, etc.) has the type 'text/plain' in their Properties window, and as a result, every file attempts to open in gedit. My '/usr/share/applications/mimeinfo.cache' file is still in tact and holds the correct associations for everything.

Any suggestions on how to remedy this?

---

### Post by mcpancakes on 2009-07-30
Anyone? Am I really this unique? :P

---

### Post by CatKiller on 2009-07-30
I've not seen this before, but **man update-mime** says
> 
**DESCRIPTION**
       **update-mime**  updates  the **/etc/mailcap** file to reflect mime information
       changed by a Debian package during installation or removal.

**man gnome-gen-mimedb** says 
> **DESCRIPTION**
       **gnome-gen-mimedb**  Build  the  database  /etc/mime-magic  in  /etc/mime-
       magic.dat, for fast access

Perhaps these will point you in the right direction.

---

### Post by mcpancakes on 2009-08-01
Hm, neither of those have resolved my problem. As far as I can tell, there's sort of a multi-step process:

[LIST=1]
[*] Look at file, determine MIME type
[*] When file is opened, run program associated with MIME type
[/LIST]
It's step 1 that is failing, not step 2. The system knows what to do with each MIME type, it just isn't doing step 1 correctly. That is, it's not assigning files their correct types.

---

### Post by mrog on 2009-08-01
The /usr/share/applications directory should also contain a simlink "defaults.list" which points to "/etc/gnome/defaults.list".

Do /usr/share/applications/miminfo.cache and /etc/gnome/defaults.list have the correct permissions? (-rw-r--r--)
  
You home directory may also contain the following:
~/.local/share/applications/defaults.list
~/.local/share/applications/mimeinfo.cache

You could also try running "sudo update-desktop-database".

---

### Post by mcpancakes on 2009-08-03
```
mcpancakes@desktop:~$ ls /usr/share/applications -l | grep "defaults.list"
lrwxrwxrwx 1 root root    24 2009-04-25 00:07 defaults.list -> /etc/gnome/defaults.list

mcpancakes@desktop:~$ ls /usr/share/applications -l | grep "mimeinfo.cache"
-rw-r--r-- 1 root root 16187 2009-07-16 17:02 mimeinfo.cache

mcpancakes@desktop:~$ ls /etc/gnome -l | grep "defaults.list"
-rw-r--r-- 1 root root 9086 2009-03-18 19:20 defaults.list
```

~/.local/share/applications/defaults.list - non-existent
~/.local/share/applications/mimeinfo.cache - a one-line file ("[MIME Cache]")

```
mcpancakes@desktop:~$ sudo update-desktop-database
[sudo] password for mcpancakes: 
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/x-csrc' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/x-chdr' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/x-copying' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/x-makefile' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' application/x-shellscript' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/xml' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/x-patch' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/x-python' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/html' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/x-authors' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/x-install' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' application/x-php' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/css' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text/x-sql' that contains invalid characters
```

So, those first two files are in order permissions-wise, as is the symlink that points to one of them. The two files in my ~/.local/share/applications directory look suspicious (one is only one line, one isn't even there!).

---

### Post by lvlo on 2009-08-03
I had an issue like yours: [http://ubuntuforums.org/showthread.php?t=868218](http://ubuntuforums.org/showthread.php?t=868218)

Good luck :)

---

### Post by mcpancakes on 2009-08-03
Thank you! I've fixed my issue. Your solution did not quite work for me:

```
$ sudo update-mime-database /usr/share/mime
[sudo] password for mcpancakes: 
Failed to rename /usr/share/mime/text/x-setext.xml.new as /usr/share/mime/text/x-setext.xml , errno: 21
```

I don't think that my /usr/share/mime folder was the issue, anyway (I don't know what to make of that error, either). The solution was one of the following (sadly I didn't check things in an order where I could be certain which of these fixed it):

[LIST][*] reinstalling package 'file'
[*] reinstalling package 'libmagic1'
[*] possibly the above running of 'update-mime-database'[/LIST]
After reinstalling both of those, I ran 'file' on several files, and noticed it was giving me the correct result. I restarted, and things were functioning normally again.

---

### Post by lvlo on 2009-08-03
Anyway good to see that you've solved your problem :)

---

