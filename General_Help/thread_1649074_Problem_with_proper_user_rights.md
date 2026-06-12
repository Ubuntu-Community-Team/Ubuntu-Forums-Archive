---
title: "Problem with proper user rights"
date: 2010-12-19
forum: General Help
---

### Post by Maurice Krielaart on 2010-12-19
Hello all,

I'm new to Ubuntu and wish to use the system in combination with Apache/mySQL/phpMyAdmin. I managed to get phpMyAdmin working for now. Also mySQL database seems to work.

Only problem is Apache2. I can start the server and it is working. However in the folder /var/www/ where all site files are stored, I can not edit anything.

I have been reading about **sudo nautilus** which did allow me to change administrator rights for the folder, but still I do not get it working to display other than the default index.html page.

Is there a manual or quick solution for me so I can use apache with Ubuntu?

Thanks in advance,
Maurice

---

### Post by i_dont_know_what_im_doing on 2010-12-19
I don't know if this is the "proper" method, but I just made a folder named "test" inside /var/www/, then changed the owner of that folder from root to my username, and set up my files in there. Then you can access that by going to localhost/test.

I think that somewhere in the apache configuration files, (/etc/apache2/) you can change the document root to something other than /var/www/, but I haven't tried that.

---

### Post by efflandt on 2010-12-19
Just do:

```
cd /var/www
sudo mkdir whatever
sudo chown somebody whatever
```Then user "somebody" can edit files in /var/www/whatever/

If you want to make it easer for "somebody" to find that from their home directory you could also make a symlink in their home directory:

```
sudo ln -s /var/www/whatever /home/somebody/whatever
```

---

