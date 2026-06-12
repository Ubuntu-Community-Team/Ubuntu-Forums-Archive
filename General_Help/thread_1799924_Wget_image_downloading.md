---
title: "Wget image downloading"
date: 2011-07-08
forum: General Help
---

### Post by andrewcow on 2011-07-08
Hey
So I am trying to download a bulk of images off a site that has both open areas and areas that need a password. I have managed to use 
>  wget -r -l inf -A gif, jpg, png [http://URL.com](http://URL.com)
on the open part of the site but can't get it working for the password part. It has a page where you put in a password (no user name tho. Not sure why. I have told the guy who manages the page millions of times to change it) which then takes you to a page only accessible with the password with all the image albums. I would then go into each album and get the URL. The problem is, if you put the URL of an album into a browser, even if you are logged in on a different tab, it will take you to a security error page. 

I have tried using --password and --password-html and --password-ftp with no avail. I was hoping someone could help:) I really don't want to save all the pictures by hand:(

---

### Post by Habitual on 2011-07-08
--password='myPassword' (with ticks)?

---

### Post by andrewcow on 2011-07-08
:( Nope didn't work. Thanks tho:):) I have no idea how they do the authentication. Its really strange. I think the issue is it always somehow links back to the password given on the first page so it does not give you a chance to enter it again...if you get what I mean:(

---

