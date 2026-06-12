---
title: "Unable to view .php files in web browser"
date: 2011-01-11
forum: General Help
---

### Post by West201 on 2011-01-11
I've been having a common problem that most users get when trying to view .php files on a web browsers. I feel like I've  tried everything including clearing the cache. This is the read what when typing this commands. Please help

> jesse@jesse-vaio:~$ sudo a2enmod php5
[sudo] password for jesse: 
Module php5 already enabled
jesse@jesse-vaio:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
jesse@jesse-vaio:~$ sudo /etc/init.d/apache2 force-reload
 * Reloading web server config apache2                                   [ OK ] 
jesse@jesse-vaio:~$ 






---

### Post by blakep2 on 2011-01-11
what appears in the screen when you try to view php files?

---

### Post by WorMzy on 2011-01-11
If you're A) getting a blank page, then there's probably an error in your code. If you're B) getting your code, rather than the processed PHP/HTML output, then you're probably viewing the page from the wrong address.

If it's A), try enabling PHP error reporting. Open /etc/php/php.ini in your favourite editor as root (e.g. gksudo gedit /etc/php/php.ini) and change the value of "display_errors" to "On", then restart the apache daemon. Refresh your webpage, and if an error is stopping the page from being processed, it should tell you why.

If it's B), ensure that you're trying to view the page from [http://localhost]("http://localhost"), and not [file:///srv/http/myfile.php]("file:///srv/http/myfile.php"), or whatever.

---

### Post by West201 on 2011-01-11
When ever I use any web browser  it prompts me to instead save. This php file is a test file. The web browser does not display the php file, but instead prompts to save it like this

---

### Post by WorMzy on 2011-01-11
You're accessing the file from the wrong place, and so apache isn't serving the file to you, firefox is simply accessing the file straight from your hard disk. Refer to B) in my last post.

---

### Post by West201 on 2011-01-11
> **WorMzy said:**
> You're accessing the file from the wrong place, and so apache isn't serving the file to you, firefox is simply accessing the file straight from your hard disk. Refer to B) in my last post.

So how do I view other .php files ? sorry I've never worked php in ubuntu/linux. Thanks :)

---

### Post by WorMzy on 2011-01-11
I think you should read through this for starters: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

It's a little out of date, and has some bad commands (don't use "sudo" for graphical commands, use "gksu" or "gksudo" instead), but you should still find it useful.

In short, to get apache to serve you pages, you actually need to tell your browser to talk to apache. You do this by pointing your browser to your PC's loopback address, essentially telling your PC to connect to itself. You can do this by going to [http://localhost/]("http://localhost/"), [http://127.0.0.1]("http://127.0.0.1"), or even [http://jesse-vaio]("http://jesse-vaio").

Now, apache doesn't know about *every* file on your machine; that would be horribly insecure if your server is visible to the outside world. So, by default, it only knows about the files stored in /var/www, so any files that you want to be processed by it should be kept here. The help page I linked you to tells you how you can change the ownership of this folder so that you can add, edit and delete files in this folder easily, and I would recommend that you do this first (check the "Using Apache" section for details). Once you have ownership of the folder, move the files that you want apache to serve to you into it. After that you can access them from the loopback address that I mentioned earlier ([http://localhost/]("http://localhost/")), just type the name of the file after the slash, e.g. [http://localhost/test2.php]("http://localhost/test2.php"), and then apache will receive the request, process the file, and send your browser the HTML output.

---

### Post by West201 on 2011-01-11
> **WorMzy said:**
> I think you should read through this for starters: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

It's a little out of date, and has some bad commands (don't use "sudo" for graphical commands, use "gksu" or "gksudo" instead), but you should still find it useful.

In short, to get apache to serve you pages, you actually need to tell your browser to talk to apache. You do this by pointing your browser to your PC's loopback address, essentially telling your PC to connect to itself. You can do this by going to [http://localhost/]("http://localhost/"), [http://127.0.0.1]("http://127.0.0.1"), or even [http://jesse-vaio]("http://jesse-vaio").

Now, apache doesn't know about *every* file on your machine; that would be horribly insecure if your server is visible to the outside world. So, by default, it only knows about the files stored in /var/www, so any files that you want to be processed by it should be kept here. The help page I linked you to tells you how you can change the ownership of this folder so that you can add, edit and delete files in this folder easily, and I would recommend that you do this first (check the "Using Apache" section for details). Once you have ownership of the folder, move the files that you want apache to serve to you into it. After that you can access them from the loopback address that I mentioned earlier ([http://localhost/]("http://localhost/")), just type the name of the file after the slash, e.g. [http://localhost/test2.php]("http://localhost/test2.php"), and then apache will receive the request, process the file, and send your browser the HTML output.

It worked :popcorn: ! Thanks alot you saved alot of trouble.. Really appreciate your help :)

---

