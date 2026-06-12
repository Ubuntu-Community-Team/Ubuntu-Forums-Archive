---
title: "Remote login to Moodle."
date: 2009-10-21
forum: General Help
---

### Post by ayenack on 2009-10-21
Hello all.

I'm having a bit of trouble with Moodle. I've got it set up on a server running Hardy Server (fully updated) now I can log in to Moodle on the server but I can't when I try to from a remote host on the same network I get a permission denied screen in Firefox any ideas?

Thanks for any help. ayenack.

---

### Post by ayenack on 2009-10-22
bump.

---

### Post by shairozan on 2009-10-22
Hey there, 

First thing to see is what the permissions on the moodle directory are. I recently set mine up and had to play with the permissions. To check the perms on the file, you can do the following:

> sudo ls -oa /var/www/

If the directory isn't set so that non-owners or the group cannot view it, you will get that. Also, who does it list as owning the directory?

you may want to chown the entire moodle directory to the www-data user and group. This will make sure that apache can own and display everything. You can do this with the following

```

sudo chown -r www-data:www-data /var/www/moodle

```

This assumes your moodle directory is located directly under www. After all of this it won't hurt to go ahead and restart apache as well

```
sudo /etc/init.d/apache2 restart
```

Let me know how it goes!

Thanks,
DJ

---

### Post by ayenack on 2009-10-23
You know I think you're probably right about the permission of the Moodle directory. I was thinking it was a database issue.

Thinking about it when I was researching Moodle and its install I'm sure it mentioned this.

I'll try it out and report back.

Thanks for the help.

ayenack.

---

### Post by ayenack on 2009-10-23
Got Moodle working in the end. Long story how I did it. I put it on an established server running another site and quite a bit of other stuff turns out there was a conflict between  Moodle and the internal site.

What I'm going to do now is put Moodle on an old server and just let it run on its own. Doesn't seem to want to play nice with the way I've got the other server set up.

Thanks for your help though.

ayenack.

---

### Post by shairozan on 2009-10-26
What port were you running moodle off of? I ask because I found out the joys of Moodle the hard way. Moodle is very specific as to what its URL is going to be up front, and you can't change it very easily. 

It makes a number of references to the URL you give it early on in the database, and the only way to change that is to change every reference of it in the database. I had an issue where I had setup a test server internally using its standard IP address. Worked great, hooray!

Then I wanted to make it public facing on port 5000. Changed the public DNS to reference xxx.mydomain.com and all of my links were xxx.mydomain.com:5000. The only issue is that Moodle would never load. What the problem is that internally, Moodle was still trying to use the internal IP address I gave it early on for all of its links. So when you query it externally it's trying to provide the same info. 

I had to re-create the site all together on a new Virtual Machine to get it working :) Hopefully it'll save you some more headaches down the road!

---

