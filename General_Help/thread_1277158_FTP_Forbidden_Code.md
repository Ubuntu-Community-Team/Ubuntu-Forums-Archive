---
title: "FTP Forbidden Code"
date: 2009-09-28
forum: General Help
---

### Post by sdlynx on 2009-09-28
Hi guys,

I'm having a little problem with setting file permission codes on my server.  I need a file to be 640 (readable by owner, but forbidden to the public), and I set it as that and it reads as that, but the public can still read it.  Thoughts?

SDLynx

---

### Post by saulgoode on 2009-09-28
Are you sure? The following file has permissions set to 640 (and produces a 403 error).

[http://flashingtwelve.brickfilms.com/Temp/test.txt]("http://flashingtwelve.brickfilms.com/Temp/test.txt")

---

### Post by sdlynx on 2009-09-28
Yeah, I'm sure.  This file is set to 640:
[http://mylifeisnerdy.co.cc/style.php](http://mylifeisnerdy.co.cc/style.php)
but it still is viewable. (Note there's no actual output for that page)

---

### Post by v8YKxgHe on 2009-09-29
Permissions are quite meaningless without knowing who is the owner and group. All you've done is set the permission to that file to 0640, so if the webserver is running as the owner of that file, or is in the same group - of course it'll have access.

---

### Post by sdlynx on 2009-09-30
Ah, that might be it.  I tried setting group to 0 as well but it was still viewable.  Obviously, owner could not be set to 0.  Since I am not the admin of the server, I guess there's nothing I can do.  I know that a 640 folder is acting as forbidden though.

---

### Post by v8YKxgHe on 2009-09-30
Assuming Apache web server which allows the use of .htaccess of similar name, why not just deny access to that file? Or, why is this even in your document root if you don't want people to have access to it? Keep it outside of the document root.

---

### Post by sdlynx on 2009-09-30
> **AlexC_ said:**
> Assuming Apache web server which allows the use of .htaccess of similar name, why not just deny access to that file? Or, why is this even in your document root if you don't want people to have access to it? Keep it outside of the document root.

Ah, good point.  How do I go about doing this with the .htaccess file?

---

