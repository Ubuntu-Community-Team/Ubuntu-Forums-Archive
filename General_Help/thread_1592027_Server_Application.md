---
title: "Server Application"
date: 2010-10-10
forum: General Help
---

### Post by ki4jgt on 2010-10-10
I'm looking to host my website from my computer without losing my computer. I was wondering if there was a simple server hosting app like runBASIC for Ubuntu. RunBASIC has a linux build but it costs 60 dollars. I've seen so many windows programs that allow you to host a website from your IP address, yet only be a window in your open programs. that I'm wondering why doesn't Ubuntu have one?

---

### Post by Neezer on 2010-10-10
> **ki4jgt said:**
> I'm looking to host my website from my computer without losing my computer. I was wondering if there was a simple server hosting app like runBASIC for Ubuntu. RunBASIC has a linux build but it costs 60 dollars. I've seen so many windows programs that allow you to host a website from your IP address, yet only be a window in your open programs. that I'm wondering why doesn't Ubuntu have one?

won't LAMP do that? It may eat up bandwidth if you're trying to surf the web or something else on that computer, but i'm pretty sure it runs in the background....or is this not what you're after?

---

### Post by ki4jgt on 2010-10-10
I can't find it in the Repos. I've upgraded to 10.10. I'm wanting something with a GUI though, something I can see instead of having to issue this command to see how this is going or that command to see what's up here. Like I said, I've found several windows programs like this, but all the linux ones seem to be terminal based.

---

### Post by hrickh on 2010-10-10
> **ki4jgt said:**
> I can't find it in the Repos. I've upgraded to 10.10. I'm wanting something with a GUI though, something I can see instead of having to issue this command to see how this is going or that command to see what's up here. Like I said, I've found several windows programs like this, but all the linux ones seem to be terminal based.
You'll want to look for Apache (web server) and mysql-server (database, if needed) in the repositories.  They're there.

Then go here for Webmin: [http://www.webmin.com/](http://www.webmin.com/) and grab the debian file to install. You'll have a GUI to manage it.

R.
==

---

### Post by ki4jgt on 2011-07-12
> **hrickh said:**
> You'll want to look for Apache (web server) and mysql-server (database, if needed) in the repositories.  They're there.

Then go here for Webmin: [http://www.webmin.com/](http://www.webmin.com/) and grab the debian file to install. You'll have a GUI to manage it.

R.
==

What is Webmin's default user and pass?

---

