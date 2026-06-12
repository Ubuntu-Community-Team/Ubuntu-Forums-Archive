---
title: "Running Wordpress on Ubuntu 10.04"
date: 2010-08-07
forum: General Help
---

### Post by LiamG on 2010-08-07
This is a really simple question.

I just installed Wordpress from the Ubuntu Software Center, but I can't figure out how to *run* it. The program hasn't appeared in any of the Applications menus and typing "wordpress" into the console doesn't do anything. Can anyone help?

---

### Post by kiltedcameraman on 2011-12-02
Anyone ever have a solution.  I am in the same boat today.  Everything says it is installed, but no way to launch.

---

### Post by jonobr on 2011-12-02
[Here]("https://help.ubuntu.com/community/WordPress") is a howto on wordpress, 

I figure your around the 

> Now, browse to "http://localhost/wordpress" in your browser to install it (or [http://''wordpress.mydomain.org''/wordpress](http://''wordpress.mydomain.org''/wordpress) if you are using a virtual host). You will be given an initial user named admin and a random password. Write it down. Then login as the admin user and change the password. 
of the document

---

### Post by Ms. Daisy on 2012-01-01
kiltedcameraman, If you're downloading Wordpress from the Ubuntu  Software Center, then you also need to be running a server, which means  that your goal is to host your own webpage?  Therefore I'm guessing that  you launch it from the terminal in your (probably non-GUI) server.  Here's another guide, it's for 11.04 but it may work with some  modifications for 10.04. 

[http://www.varunvats.com/2011/06/wordpress-in-ubuntu-11-04-a-complete-guide/](http://www.varunvats.com/2011/06/wordpress-in-ubuntu-11-04-a-complete-guide/)

Or do you just want to create a blog and have someone else host it? At [wordpress.com]("http://wordpress.com/")  you can create your own blog & they will host the blog for you. Not  sure what your goal is with the blog, but you can upload videos, music,  photos, etc. that way without messing with hosting it yourself.

If you decide to create your own web server, you need to understand that  there are automated bots scouring the web daily and brute force  attacking any server they find. If you set up a server without securing  it, you will get cracked.  See the [server sticky]("http://ubuntuforums.org/showthread.php?t=1046738")  and for a huge amount of info.  I don't know what the required specs  are for running a server, but you'll want to look into that as well. Will your laptop handle a server?

---

