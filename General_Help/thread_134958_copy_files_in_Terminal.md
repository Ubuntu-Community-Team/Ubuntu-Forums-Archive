---
title: "copy files in Terminal"
date: 2006-02-22
forum: General Help
---

### Post by OceanSized on 2006-02-22
How can I copy an image on my desktop to a remote server in the Terminal?

I type "cp *filename*" but then it claims that it cannot access that file, even after I have simply moved it into the terminal with my cursor.

---

### Post by erimar77 on 2006-02-22
```
scp filename user@remoteserver:/path
```

---

### Post by OceanSized on 2006-02-22
I keep getting this message not allowing me to copy the file:

"scp: warning: stat: *filename* (src): no such file (server msg: 'syserr: No such file or directory, file: /home/sdc/Desktop/*filename*')"

Any suggestions? I'm used to WinSCP, but don't use microsoft anymore as of this week. I have a book that would explain all of this for me but I don't have it at the moment. So I'm at a real loss.

---

### Post by RAOF on 2006-02-22
You are typing the name of the file instead of *filename* aren't you?  If it's on your desktop it's full path will be: ~/Desktop/*filename*

---

### Post by OceanSized on 2006-02-22
Of course, I'd just rather use *filename* lol

---

### Post by nanotube on 2006-02-23
if you want a gui frontend a la winscp, install the gftp package. it can handle multiple protocols, including ssh.

---

### Post by jrib on 2006-02-23
you can just use nautilus as well, just go to ``file -> connect to server''

---

### Post by dcstar on 2006-02-23
[QUOTE=RAOF]You are typing the name of the file instead of *filename* aren't you?  If it's on your desktop it's full path will be: ~/Desktop/*filename*[/QUOTE]
And of course, we all know that Linux is case sensitive, don't we......

---

### Post by halfvolle melk on 2006-02-23
Is there a space in "filename"? Eg. "file name". You can 'escape' a space with "\":
cp ~/Desktop/file\ name /path

---

