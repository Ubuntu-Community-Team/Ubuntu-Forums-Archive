---
title: "How to upload SSL crt file securely to server?"
date: 2011-12-26
forum: General Help
---

### Post by houmank on 2011-12-26
Hi,

I have switched from IIS7.5 to Apache2 and Ubuntu. Its a new world to me. :D

I am in process of enabling SSL on Apache2. I have created a csr on the Apache2 and submitted it to my provider and received two CRT files.

Now how do I get these two files to the server securely? Its kind of paradox, as I don't have a webbrowser on ubuntu server (logged in through cygwin). Therefore I can't download the crt files there directly from GoDaddy's website.

What is the recommended way to do this? Secure FTP? 

Sorry I am new to Linux, a clear explanation or pointing to tutorials would be highly appreciated.

Many Thanks,
Houman

---

### Post by houmank on 2011-12-26
Ok I have found a way. It is possible to transfer files simply through SSH.

Well simply...

This should have copied my file over

**scp -v gd_bundle.crt [email]ubuntu@107.21.xxx.xxx[/email]:/home**


But it still says:

[B]Permission denied (publickey).
lost connection[/B]

Any idea what I should do?

I use cgywin. Many Thanks

---

### Post by 2F4U on 2011-12-26
No write access to /home? Maybe try copying to /home/your_user_name?

---

### Post by houmank on 2011-12-26
Yes that worked many thanks. :)

---

