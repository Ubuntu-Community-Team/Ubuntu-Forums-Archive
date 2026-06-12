---
title: "How do you give the &quot;Hidden&quot; attribute to a file in Ubuntu??"
date: 2010-11-09
forum: General Help
---

### Post by victorhugo289 on 2010-11-09
Is there a command similar to MS-DOS's 'attrib'?? to hide the file??

---

### Post by efflandt on 2010-11-09
In *nix systems, filenames that begin with a dot are considered hidden unless you specifically display them (by using the **-a** switch for **ls**, or Ctrl+H in nautilus.

If you want to totally hide files from other users, put them in a directory and give the directory 700 permission ( drwx------ ).  For a directory the x bit is required to do a directory listing, and r is needed to read files.  So if group and others have no read or x permission, they will not be able to see or read any files in that directory.  See **man chmod**.  Although, that would not necessarily hide files from people who are allowed to do unlimited things as root using sudo.

---

### Post by victorhugo289 on 2010-11-10
Thanks. I noticed there was already a thread about this, but I thought it was a little unsolved, what you say about the 700 permission is really interesting. And also I'm gonna check 'chmod' right away.

---

### Post by WorMzy on 2010-11-10
You can also hide files by creating a text file called .hidden in the same directory as the files you want to hide. In this text file write the names of the files you want hidden, one name per line. Save the file and refresh your file browser (F5), and the file should become hidden.

---

### Post by victorhugo289 on 2010-11-10
@WorMzy, I'll give it a try, thanks!

---

