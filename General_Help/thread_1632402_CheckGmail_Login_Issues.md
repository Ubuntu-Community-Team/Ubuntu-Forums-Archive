---
title: "CheckGmail Login Issues?"
date: 2010-11-27
forum: General Help
---

### Post by andonato on 2010-11-27
Anybody having problems lately? I was getting the 404 error and so I ran update. Now I am getting the "Incorrect username" window and can't log in. Using the -no_cookies option works, but with reduced functionality. The terminal shows the following:

> Use of uninitialized value in substitution (s///) at /usr/bin/checkgmail line 3306.
Use of uninitialized value in substitution (s///) at /usr/bin/checkgmail line 3299.
Use of uninitialized value in concatenation (.) or string at /usr/bin/checkgmail line 927.
Unable to find gmail_ik ... full message text won't work :(


Any ideas?

---

### Post by kerry_s on 2010-11-28
have you tried "gm-notify" it's much more dependable.

---

### Post by Absorbed on 2011-09-08
For some reason I woke up today and CheckGmail won't login. I can login via the web. If I run CheckGmail in a terminal, no error messages come up when I cannot login.

I cannot see any posts by other people having the same problem today. Is there anybody out there?

I will switch to another Gmail checker is necessary, but I'm used to CheckGmail so I'd rather not.

---

### Post by polki@mac.com on 2011-09-09
Same here, user is correct and so is the password. No error messages when started in terminal, just the login window popping up again. On mouseover: "Error: Unauthorised"

It's been like this for a few weeks on my computer. Sure, there are alternatives, but I would like to use CheckGmail as I prefer its functionality.

---

### Post by Absorbed on 2011-09-09
A solution that works for me is to do "checkgmail -no_cookies", but it limits the functionality.

From here: [http://ubuntuforums.org/showpost.php?p=11232528&postcount=8](http://ubuntuforums.org/showpost.php?p=11232528&postcount=8)

---

### Post by webcomm on 2011-09-16
"limits functionality" is an understatement.  With the no_cookies approach, very little functionality is available.  You have to click "check gmail" just to see if you have new email, so it doesn't really function as a notifier at all.

This is not the fault of the various notifier apps but more likely the fault of frequent changes at gmail.

Essentially, as of this writing there is no gmail notifier that works in ubuntu (at least not in natty w/ the classic desktop, which is what I have).

---

### Post by webcomm on 2011-09-20
GmailWatcher is working for me in natty:

[http://www.webupd8.org/2010/09/gmailwatcher-gmail-notifier-especially.html](http://www.webupd8.org/2010/09/gmailwatcher-gmail-notifier-especially.html)

---

### Post by MyR on 2011-09-21
Fix here: [http://linuxdeal.com/how-to-fix-checkgmail](http://linuxdeal.com/how-to-fix-checkgmail)

---

### Post by itsjustarumour on 2011-09-23
> **MyR said:**
> Fix here: [http://linuxdeal.com/how-to-fix-checkgmail](http://linuxdeal.com/how-to-fix-checkgmail)

Excellent, worked for me.

:-)

---

### Post by Feenix217 on 2011-09-29
Woot! It worked for me too! Ubuntu 10.10!

Feenix


> **itsjustarumour said:**
> Excellent, worked for me.

:-)

---

### Post by maya123ca on 2011-10-04
Thanks to Jan Jurgus and Linuxdeal.com and MrR. I have been struggling to find a solution to this problem for months.

---

