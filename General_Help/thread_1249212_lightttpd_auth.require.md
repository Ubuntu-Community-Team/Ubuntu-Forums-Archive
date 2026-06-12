---
title: "lightttpd auth.require"
date: 2009-08-25
forum: General Help
---

### Post by domiNATE on 2009-08-25
Hey guys.

I'm trying to use my installation of lighttpd for a combination of a website and a web interface for rtorrent.

I've set up my lighttpd.conf so that, anybody can access my website, but when they try to access /rtorrent (for the web interface) it requires a password.

```
$HTTP["url"] =~ "^/rtorrent" {
auth.backend = "plain"
auth.backend.plan.userfile ="/home/lighttpd/lighttpdpassword.txt"
auth.require = ( "/rtorrent" => (
"method" => "basic",
"realm" => "Password protected area",
"require" => "valid-user"
))
}
```When I try to access /rtorrent, I am prompted to enter a username and password. I then proceed to enter the username and password as stored in /home/lighttpd/lighttpdpassword.txt, but it doesn't accept it. Instead, I get a 401 error.

I have spent the last 3 hours trying to get this working, and thought it might be time to consult the ubuntu forums.

Any help is appreciated. Cheers.

---

