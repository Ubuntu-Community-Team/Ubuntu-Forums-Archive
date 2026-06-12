---
title: "Apache 2 won't let me change default path"
date: 2010-06-27
forum: General Help
---

### Post by chrisd1891 on 2010-06-27
Hey everyone, 

I searched this topic, and I've been trying what people say, as in, to modify the etc/apache2/sites-avaliable/default reference to /var/www to my new path. I'm trying to make a reference to a second hard drive that is not part of the main file system, so I changed all the references to /var/www to /media/HD1/www    and I have set the permissions on the entire hard drive to allow reading, and I still get a 403 forbidden error when I attempt to access my site, everything works when I just use the default path.  I'm using Ubuntu 10.04 with apache2 installed through the package manager...

Any ideas? :confused:  

Thanks in advance

---

### Post by Leppie on 2010-06-28
have you tried to give "execute" permission?

---

### Post by chrisd1891 on 2010-07-28
Thanks for the response, I tried that, by recursively setting everything to rwx by doing chmod -R +rwx on my hard drive, and I also tried it on the folder that contains everything. 

Any more ideas?:confused:

---

