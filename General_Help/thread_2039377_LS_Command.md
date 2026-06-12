---
title: "LS Command"
date: 2012-08-08
forum: General Help
---

### Post by matimont on 2012-08-08
Hi,

I run ls -l on one of my sites Public_html in my VPS and get user and group as 916, what that means?

Shouldn't I see the users and groups that own the files? I don't see any user 916 in the system.

Thank you!

---

### Post by rukiaEnix on 2012-08-08
Check at /etc/passwd for what user is the UID 916.

Also please post the result of ls -l

---

### Post by matimont on 2012-08-09
Here's the ls -l extract:[FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916 287705 Aug  6 14:17 error_log[/FONT]

[LIST]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916    397 Mar  8 21:42 index.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916  16899 Mar  8 21:42 license.txt[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   9735 Mar  8 21:42 readme.html[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]drwxr-xr-x  2 916 916   4096 Mar  8 21:42 Scripts[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   4268 Mar  8 21:42 wp-activate.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]drwxr-xr-x 10 916 916   4096 Mar  8 21:42 wp-admin[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916  40272 Mar  8 21:42 wp-app.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916    274 Mar  8 21:42 wp-blog-header.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   3982 Mar  8 21:42 wp-comments-post.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   3265 Aug  7 22:26 wp-config.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   3573 Apr 23 04:28 wp-config-sample.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]drwxrwxrwx  7 916 916   4096 Aug  8 20:07 wp-content[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   2684 Mar  8 21:42 wp-cron.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]drwxr-xr-x  9 916 916   4096 Mar  8 21:42 wp-includes[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   1997 Mar  8 21:42 wp-links-opml.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   2578 Mar  8 21:42 wp-load.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916  27695 Mar  8 21:42 wp-login.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   7777 Mar  8 21:42 wp-mail.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916    413 Mar  8 21:42 wp-pass.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916    334 Mar  8 21:42 wp-register.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   9913 Mar  8 21:42 wp-settings.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916  18545 Mar  8 21:42 wp-signup.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   3702 Mar  8 21:42 wp-trackback.php[/FONT]
[*][FONT=Symbol]·         [/FONT][FONT=&quot]-rw-r--r--  1 916 916   3266 Mar  8 21:42 xmlrpc.php[/FONT]
[/LIST]
                                                          
I also checked in the Etc/Passwd file and there's no such user ID (916)...

thanks!

---

### Post by Vaphell on 2012-08-09
i'd chown these files. I think they are assigned id=916 somehow but since it doesn't translate to a known user, things are left as they are and ls shows 916.

---

### Post by albandy on 2012-08-09
It seems that theese files came from a tar.gz created by user 916. 
When you extract a tar file using sudo or the root user, the file owner are set the same as from the system where the files were copied.

Or you deleted user 916.

---

### Post by matimont on 2012-08-09
That's correct, I did create a tar on another server, then copied using the wget command to my VPS and extracted the files.

What should I do, change the group/users permissions? Everything seems to work fine, it is a Wordpress instalation, however, one of the plugins is giving me an error when trying to activate it: "you don't have permissions to access this page". Do you think that could be the reason?

thank you!

---

### Post by rukiaEnix on 2012-08-09
Yes, better change user and group to a user and group that you have in that server.

---

### Post by matimont on 2012-08-09
What would be the command to run in a terminal if I want to change all the public_html files and folders group/user?

thanks!

---

### Post by rukiaEnix on 2012-08-09
Like this:

```

chown *user*:*group* -R */dir/public_html*

```

---

