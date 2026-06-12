---
title: "Apache Alias &amp; Windows File Server"
date: 2011-02-22
forum: General Help
---

### Post by SwitchLink on 2011-02-22
I have a need to create a virtual directory in Apache for one of my company's internal websites.

I have confirmed that I can create an alias for a local directory:

Alias /vdir/ "/usr/share/somefolder/"

So I would get to this virtual directory by going to [http://server.domain.com/vdir/](http://server.domain.com/vdir/).  But when I attempt to point it to a shared folder on another server:

Alias /vdir/ "//servername/share/"
or
Alias /vdir/ "//servername/share/somefolder/"

Both return the 404 Not Found error, which I would expect if it is not connecting to the share.  I've searched but can't seem to find the correct syntax and I know I am missing something basic.

Can anyone help illuminate me on what I am missing?  I have searched google and these forums but can't seem to locate the exact syntax.  Are there other lines in the config file I need?  Permissions should be no problem the shared is EVERYONE has access (for now).

Thanks!

---

### Post by bodhi.zazen on 2011-02-22
I think you want to look at using apache as a reverse proxy (rather then the alias).

This is a nice overview : [http://www.wlug.org.nz/ApacheReverseProxy](http://www.wlug.org.nz/ApacheReverseProxy)

---

### Post by SwitchLink on 2011-02-23
The reverse proxy is a very elegant solution, thank you.

However, I read that the Alias feature can be used to create virtual directories that point to shared folders on other servers but the documentation did not go into any detail.

One solution I have come up with is mounting the share on linux using samba and then using the alias to create the virtual directory.  However, I'd like to skip the mounting step and just alias it directly.  Can that be done?

---

### Post by bodhi.zazen on 2011-02-23
> **SwitchLink said:**
> One solution I have come up with is mounting the share on linux using samba and then using the alias to create the virtual directory.  However, I'd like to skip the mounting step and just alias it directly.  Can that be done?

You could probably do this, but that is not what the alias feature is designed to do.

IMHO alias is designed for local files, ie serving files from say /usr/local/apache/share as [http://share/](http://share/)

You would, in that example, alias /usr/local/apache/share to /share

If you want to server files from another location, IMHO, a reverse proxy is a much much better option.

If you go with samba you probably need to look at permissions and make sure apache (www-data) can read but not write the shares.

---

### Post by SwitchLink on 2011-02-23
What if I want to server files from another location and that other location is a Windows file server and does not have any web server running on it.  Can I still use the reverse proxy?

---

### Post by bodhi.zazen on 2011-02-23
> **SwitchLink said:**
> What if I want to server files from another location and that other location is a Windows file server and does not have any web server running on it.  Can I still use the reverse proxy?

No, I would move the files to the Linux (Apache) server or rsync them.

---

### Post by SwitchLink on 2011-02-24
Ok, I'm all set then.  Thank you for your help.

I ended up using the fstab to mount the CIFS shares directly into the web root of the virtual website.  I then used authentication to restrict the level of access down to read only.

It's not pretty, but it works.  The website is internal and all of the people that have access to the web server also have access to the shared folder, so not a really big change in in terms of who can access the files.

---

### Post by bodhi.zazen on 2011-02-24
> **SwitchLink said:**
> Ok, I'm all set then.  Thank you for your help.

I ended up using the fstab to mount the CIFS shares directly into the web root of the virtual website.  I then used authentication to restrict the level of access down to read only.

That sounds like a very reasonable solution.

---

