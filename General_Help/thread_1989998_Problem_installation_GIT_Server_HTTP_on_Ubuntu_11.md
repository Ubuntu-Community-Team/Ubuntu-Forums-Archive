---
title: "Problem installation GIT Server HTTP on Ubuntu 11"
date: 2012-05-29
forum: General Help
---

### Post by pbonato on 2012-05-29
Hi all,
someone can help me ?
I have installed on my Ubuntu machine the GIT server with Gitolite...it seems to work perfectly with SSH and GIT protocol, I have installed the option GiWeb on Apache2 too...

I am not be able to clone, push, and pull the repository via HTTP protocol...there is a good men ( or woman :-) ) can help me step by step...I am quite novice on Linux and all the info on the web cannot help me...

Thanks for your patiente

---

### Post by pbonato on 2012-05-31
I do not know if this is a big problem and nobady ha a solution :P or nobady read it....:(
 
No wonderful people can help me ???? Please....Thanks

---

### Post by roelforg on 2012-05-31
http is by default readonly.
 
[http://dabayrus.wordpress.com/2011/03/24/howto-setup-git-server-using-smart-http/](http://dabayrus.wordpress.com/2011/03/24/howto-setup-git-server-using-smart-http/)
This'll tell you how to set it up as r/w, there's a typo in there: when he says http.conf he means the apache2 httpd config file (though the file he tells you to edit for modcgi could also be in a file somewhere in /etc/apache2/conf.d).

---

