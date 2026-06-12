---
title: "Wordpress site messed up..."
date: 2012-02-08
forum: General Help
---

### Post by tony360 on 2012-02-08
I am not sure if this is the correct forum, it does say general. I installed WP on my 11.10 server yesterday and installed a great looking theme. from within my lan at home i can access it and it looks great. no issues using my private lan ip to access the site.
 
however, i opened up port 80 on my FW and when I access it from work it looks like crap. the images are missing, the page is white and the layout is totally messed up. Tried to insert a screenshot but the post won't allow me to for some reason.
 
any ideas?
 
the site loads EXTREMELY slow as well. I know that this is not a permissions issue as I can see it just fine and admin the site from within my lan.
 
Thanks for any help in advance
 
Tony

---

### Post by Dngrsone on 2012-02-08
Actually, it does sound like a permissions issue-- try adding whatever your internet guest user name to the same group that owns your WordPress install.

For my local install, I found that I had to change ownership and group to allow autoupdate to work; for example,

```
sudo chown -R www-data /var/www/MyBlog
sudo chgrp -R www-data /var/www/MyBlog 
sudo chmod -R 775 /var/www/MyBlog

```

---

### Post by tony360 on 2012-02-08
Thanks for your reply,

I had already run the sudo chown -R www-data /var/www/wordpress yesterday, before that nothing worked anywhere at anytime.  Lots of documents on how to set up wordpress on Ubuntu, but everyone of them are a fail for me because not one of them tells you these permissions are required post-install.  
 
Same issue is occuring after running the suggested changes.  the following is a getfacl from the wwww root and from the wordpress dir.  Thanks again!

getfacl /var/www
getfacl: Removing leading '/' from absolute path names
# file: var/www
# owner: www-data
# group: www-data
user::rwx
group::r-x
other::r-x


getfacl /var/www/wordpress
getfacl: Removing leading '/' from absolute path names
# file: var/www/wordpress
# owner: www-data
# group: www-data
user::rwx
user:tony:rwx
group::r-x
mask::rwx
other::r-x

 
thoughts?

---

### Post by Dngrsone on 2012-02-08
Man, I don't really know.  It took me months of research to get the local install working right, and then make a checklist so I can migrate it to a new machine; I never looked into hosting it on particularly my own.

Something is keeping your remote user from seeing the graphics; so it seems to me that there is either a permissions problem, or a linking problem-- the remote user can't find the relevant files.

---

### Post by gunksta on 2012-02-10
I am also having problems with a new WordPress install. But, what is odd is that I'm not having your problem at all. To me, your problem sounds like a slow outbound connection. If it was a port issue, I would think you would be unable to get anything. If it was a permissions problem, browsing locally should yield the same result.

I would test this by making a html page by hand with some pictures and browsing to it. I predict it will be find locally but won't load correctly from outside because of the slow upspeed of the connection. I think your browser is partially timing out.

---

### Post by Dngrsone on 2012-02-11
> **gunksta said:**
> I am also having problems with a new WordPress install. But, what is odd is that I'm not having your problem at all. To me, your problem sounds like a slow outbound connection. If it was a port issue, I would think you would be unable to get anything. If it was a permissions problem, browsing locally should yield the same result.

I would test this by making a html page by hand with some pictures and browsing to it. I predict it will be find locally but won't load correctly from outside because of the slow upspeed of the connection. I think your browser is partially timing out.

I see what you did, there.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/naughty.gif[/IMG]

You have a good point, though-- if the throughput is limited on the outgoing pipe (which is often the case on household internet packages), then it certainly could be just a problem of getting the data out to the client computer.

---

