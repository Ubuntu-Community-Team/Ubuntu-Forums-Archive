---
title: "User/permissions issue, affecting new folders + PHP sessions"
date: 2012-04-09
forum: General Help
---

### Post by elliotpo on 2012-04-09
Hello,

I'm installaed a LAMP stack on a linode and uploaded a web site.  
Things are working pretty well.  

However, when I try to use a multiple file uploader that makes a directory before moving uploaded files in there, the new-created directory is owned by a strange unix user.  I did make the user, but they should have nothing to do with new files.  

The containing folder -- as the entire web directory -- is owned by www-data:www-data.  
The user I log in as for public key purposes is a different user.
Then this other user winds up owning the moved files and I can't access them through PHP.

So, I deleted the problematic user.  
Apache wouldn't reboot, I got this:
apache2: bad user name ${APACHE_RUN_USER}

And my PHP sessions wouldn't work either.

It turns out this user owns sessions, for some reason.  But nothing else.

When I check: nothing runs as this user and this user owns nothing but the sessions and the new folders made by mkdir() or move_uploaded_file.  
But I can't delete them or things break.

Any ideas as to what might be happening?

Also:  I have to set the permissions to 777 on the web folder (owned, again, recursively, by www-data:www-data.  I'm not really live yet so I figured I'd sort that out soon, but I'm wondering if the two problems are related?

I apologize if I'm leaving out crucial information, or if this is a terribly Nooby question.
I appreciate the time anyone might take with it--

Thanks so much,
Elliot

---

