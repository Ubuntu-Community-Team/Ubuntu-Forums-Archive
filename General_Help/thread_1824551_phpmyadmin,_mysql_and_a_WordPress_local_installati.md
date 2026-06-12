---
title: "phpmyadmin, mysql and a WordPress local installation"
date: 2011-08-13
forum: General Help
---

### Post by Dngrsone on 2011-08-13
I am running a fairly fresh Ubuntu 10.04.

I installed LAMP Server, phpmyadmin and set everything up for a local installation of WordPress.  Initially everything worked fine.  I managed to import my old mysql database from a previous installation, and WordPress saw the files fine.

For some reason, the WordPress Blog itself would not show the posts...

At any rate, I added a bunch of posts, basically backfitting posts that had been lost between the last post of the old database and present.

After I added the posts, I wanted to get a current backup of the database.  I called up phpmyadmin and now it can't log into the mysql database, giving me an error "#1045 Cannot log in to the mysql server".  I can log straight into mysql using the same user and password (in a terminal), but phpmyadmin is not cooperating.

Unfortunately, I am not remotely fluent with the mysql commandline.

I tried installing a second WordPress so I can try to fix the whole posts not showing thing, but the new WordPress can't access teh mysql database either.

And yet the original WordPress still works (that is, I can still see and edit the posts in the database...).

Oh, by the way, in troubleshooting the problem, I discovered that the /var/lib/phpmyadmin/config.inc.php file is empty.  I tried removing phpmyadmin and reinstalling and that did not work.


So, *any* ideas why phpadmin can't won't log in?

---

### Post by Dngrsone on 2011-08-13
[IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/doh.gif[/IMG]

Okay, nevermind.... turns out I had my passwords crossed.

I can get into phpmyadmin and I can access the database from another WordPress.

Now all I have to do is figure out what is wrong with my database that won't let the entries appear in the blog.

---

### Post by crook17 on 2011-08-14
could be a permission issue?

---

### Post by Dngrsone on 2011-08-14
I don't think so.  WordPress automatic updates works, which is definitely a permissions issue, at least for the folders, and I can and do access and edit the individual posts.

The blog side just doesn't post the content.  For that matter, the mailer sends out blank emails, now that I think about it...  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

### Post by crook17 on 2011-08-14
ok, if my memory serves me right in phpmyadmin there should be a settings table is there any fields that need to be updated?

if that doesn't work you could try to do a fresh install of the same version as the old word-press and attach the old database to the new installation?

---

### Post by Dngrsone on 2011-08-14
Turned out to be a misbehaving plugin:

Since it is a local installation of WordPress, I use the Post Notification plugin to email my blogs out to my faithful five readers.  Well, one of the settings from the old blog did not match the current configuration of the new installation and it was causing the lack of text.

When trying to get into the settings dialog for that plugin, it caused Apache2 to generate some 8 gigabytes of error logs which crashed my system (I am using a conservative 29.5GB partition for root).

So, I just learned that gnome will not initialize correctly if there is no room on the root partition, and so that solves (several months too late) the problem with my last Ubuntu 10.04 install.  I was able to boot into safe mode, surf over to the /var/logs/apache2 directory and delete the offending error.log and then reboot normally.

Then I went into phpmyadmin, browsed the wp_options table, and discovered the setting that was awry (my custom profile folder was misnamed).  In the process, I also fixed a couple links to the wrong localhost folder, preventing even more misbehavior.

---

### Post by crook17 on 2011-08-14
> **Dngrsone said:**
> Turned out to be a misbehaving plugin:

Since it is a local installation of WordPress, I use the Post Notification plugin to email my blogs out to my faithful five readers.  Well, one of the settings from the old blog did not match the current configuration of the new installation and it was causing the lack of text.

When trying to get into the settings dialog for that plugin, it caused Apache2 to generate some 8 gigabytes of error logs which crashed my system (I am using a conservative 29.5GB partition for root).

So, I just learned that gnome will not initialize correctly if there is no room on the root partition, and so that solves (several months too late) the problem with my last Ubuntu 10.04 install.  I was able to boot into safe mode, surf over to the /var/logs/apache2 directory and delete the offending error.log and then reboot normally.

Then I went into phpmyadmin, browsed the wp_options table, and discovered the setting that was awry (my custom profile folder was misnamed).  In the process, I also fixed a couple links to the wrong localhost folder, preventing even more misbehavior.

Glad it is all working for you now:D

---

