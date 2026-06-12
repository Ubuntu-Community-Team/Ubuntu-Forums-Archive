---
title: "Debian - setting up a virtual ftp"
date: 2009-08-10
forum: General Help
---

### Post by Cardale on 2009-08-10
Sorry did know what forum to put this in move if its in the wrong one thanks.

I wanted to set-up a virtual ftp account for a home folder and I only want files that the user has uploaded to be visible.  I only want these files in one folder though and can't have them in separate folders.  So pretty much multiple users will have access to this one main folder, but only be able to see their files.  How should I accomplish this? any suggestions?

---

### Post by Cardale on 2009-08-10
bump

---

### Post by Cardale on 2009-08-10
It would be I think less resource intensive if I could just upload them to that directory instead of having to maybe automate a shell script or use a **move_uploaded_file **from php.

Which would take up more resources? php move file? shell script? ftp access?

---

### Post by Cardale on 2009-08-10
bump

---

### Post by hessiess on 2009-08-10
You shouldn't bump your thread so soon.

Have one user account per user, chmod all files so they can only be read by that user and get PHP running as a CGI app using suexec. Use SFTP instead of FTP.

---

### Post by Cardale on 2009-08-10
Thanks elaborate on php cgi? Why?

---

### Post by hessiess on 2009-08-10
> **Cardale said:**
> Thanks elaborate on php cgi? Why?

You need to get PHP running as the user that owns the files, not the user which Apache is running as. Running PHP as the apache user means that all users can read each outers files as they must be readable by the Apache user. Running PHP as a CGI/Fast CGI app is the simplest way to do this.

---

### Post by Cardale on 2009-08-10
Ahh I see what your saying.  Thanks for the input.  I found another reasonable way to get it done.  Thanks.

---

