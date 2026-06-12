---
title: "Trouble opening MS Office files on Windows share"
date: 2011-11-13
forum: General Help
---

### Post by aetherius0 on 2011-11-13
For work, we have a Windows share so everyone can access files and edit them. For some reason, LibreOffice will not open the files from the server, but it will if I copy them to my local machine. That doesn't do me much good though if I can't edit things on the server. Any ideas on how to fix this?

---

### Post by clausrei on 2011-11-13
Is it possible, that you didn't take the file permission into account ?

Open a terminal --> navigate with the commands "cd /, cd ~, ls , ls -l" to the folder where your shared document are.

Type in :      ls - l
( this will show you the file permission for that folder )

Type in : sudo chmod 777 -R "filename"
 (This will set free the file permission to read and write for this folder and -R stands for recursive, which will set the read and write permission for all its content files as well. )

Next  --> type in your Superuser password.
Next  --> type "ls -l"  again to see that your file permission has changed


More information can be found here: [https://help.ubuntu.com/community/FilePermissions ]("https://help.ubuntu.com/community/FilePermissions")

It is a bit unfamiliar on the beginning I now, but it is very important. Windows , for example is very prone to malware, because it doesn't have a sensitive file permission system in place.

---

### Post by Mark Phelps on 2011-11-14
Just so you know, LibreOffice, like the previous Open Office, doesn't handle the new MS Office XML file formats (i.d., docx) well.

When it does open them (it can't always do that), it often doesn't display them properly.

So, be prepared to encounter problems using LibreOffice on the new Office file formats.

---

### Post by aetherius0 on 2011-11-14
I'm not at all surprised. Any idea of how well Office 2010 works through Wine?

---

### Post by Mark Phelps on 2011-11-14
> **aetherius0 said:**
> I'm not at all surprised. Any idea of how well Office 2010 works through Wine?

Yes -- it doesn't!  It took CodeWeavers three years to get Office 2007 even working half-way decently.  And by then, Office 2010 was already out.

Attempting to use Wine with Office 2010 is basically a waste of time.

---

