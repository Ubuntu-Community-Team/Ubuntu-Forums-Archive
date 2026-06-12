---
title: "wordpress/ubuntu"
date: 2011-10-30
forum: General Help
---

### Post by jacknet52 on 2011-10-30
I have a Wordpress website that I uploaded through filezilla. I'm really new: How do I do modifications and testing on my local Ubuntu 11.10 machine using Apache2, Mysql and PhP before switching back to filezilla and uploading my changes to the website? Thanks in advance for all you guys and gals do.

---

### Post by Dangertux on 2011-10-30
You would need to create an exact copy of the site on the local server.

If you're just modifying themes or whatever you won't need to deal with your database and can just copy your wordpress files over to the new server.

However, if you want to make changes to the content, posts, or anything else stored in the database you will have to also make a copy of the database (you can sqldump it) then copy it over and import it to the new server (note this may overwrite whatever is in your existing database)

If you can clarify which it is you're trying to do. Be it edit the theme or something else that doesn't require the db , or actually edit the content prior to posting it I can answer more specifically.

Hope this helps.

---

### Post by jacknet52 on 2011-10-30
@dangertux: Thanks for taking the time to respond. I have a copy of my wordpress blogsite running on my remote server and a copy in my /home/www folder. I have apache2, mysql and PhP on my local box. I'd like to make mods and test before I upload live to my remote server that's serving the web. I'm not sure how I setup my local machine for modifying and testing the website before I upload to go live. When I set up my website I just downloaded a copy of wordpress and installed it to my remote using filezilla and the instructions at wordpress so I never ran it on my local machine. Does that makes sense? Thanks.

---

### Post by Dangertux on 2011-10-30
I understand what you're saying with that, what I'm asking is are you talking about modifications to the posts/pages/etc? Or are you talking about modifications to the templates.

If its just the templates, you can modify the php files in the wordpress directory. If its your actual posted content, when you post the data is stored in a database and is dynamically generated when the page loads using the php files as a template.

If you only copied your webroot with the wordpress files in it, for wordpress to work you will need to create the database for it in mysql on your local machine. You can do this by doing the following

```

mysql -u root -p 

```

You will be prompted for a password this was the MySQL admin password you created when you installed mysql.

```

CREATE DATABASE wordpressdbname;
GRANT ALL PRIVILEGES ON wordpressdbname.* to 'username'@'localhost' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;

```

This will create the database, username and password. The details for what to use for the dbname username and password can be found in your wp-config.php file in the files you copied from your server.

After this you should find that wordpress is now functional on your home server. 

I hope this answers the question as I'm still a little confused about what you're asking.

---

