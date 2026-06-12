---
title: "Wordpress+apache2"
date: 2010-05-15
forum: General Help
---

### Post by Timtro on 2010-05-15
Hi All,

Nothing like a good romp with a web server to make someone feel stupid.

I want to make a sandbox for me to develop a new website+wordpress.

Anyhow, did the usual LAMP setup. I tried the sudo apt-get install wordpress, and it did the same thing that I'm having trouble with now, but I am currently working work a downloaded copy of wordpress.

Anyhoo, I want to start from a theme that's already available and start hacking away. If I go to Appearance > Themes in the wordpress panel, I can upload a zip file, right? Wrong! After I get asked for FTP creds, I get
```

Unable to create directory /var/www/timteatro.com/wp-content/uploads/2010/05. Is its parent directory writable by the server?

```

I've changed the permissions of everything from www on down the tree to 775 with owner root and group 'www-data'. Still no dice.

At one point, I had 777 on www (and recursively down the tree) and STILL NO DICE! What am I doing wrong?

Now, if I 'search' for the theme from the wordpress website, and click install, I get the FTP creds page and then the error
```

Downloading install package from http://wordpress.org/extend/themes/download/... .

Unpacking the package.

Could not create directory /var/www/timteatro.com/wp-content/upgrade/piano-black.tmp

```

---

### Post by kekc_leader on 2010-05-15
May be, (recursively) change the directory permissions?
sudo chmod -R 777 /var/www

Do you use "sudo "... everywhere?

---

### Post by Timtro on 2010-05-15
> **kekc_leader said:**
> May be, (recursively) change the directory permissions?
sudo chmod -R 777 /var/www

Do you use "sudo "... everywhere?

Yes, of course. How would I do it otherwise? I suppose I could set a root password, but I much prefer sudo.

Oh, and I did do it recursively. (-R flag)

Thanks for your reply.

---

### Post by Timtro on 2010-05-15
I should add that I can personally make files in these directories, since I set the group permissions to 7. I can mkdir and get a new dir, or I can touch "HELLO" and get an empty HELLO file.

What user or group is Apache part of?

I'm afraid I know very little about web development. Is it php that's trying to create the file or Apache? Are there permissions to be set within their configuration files?

---

### Post by Timtro on 2010-05-15
I finally seem to have done something that works. I not only changed the group, but the user to www-data, and now it works fine.

I'm sure this was probably obvious to most people, but I have almost no experience with stuff like this.

---

