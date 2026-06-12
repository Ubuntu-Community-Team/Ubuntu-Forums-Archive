---
title: "Need a http file sharing application"
date: 2009-08-31
forum: General Help
---

### Post by Midrian on 2009-08-31
I am looking for a HTTP "FTP" server which will allow me to create a user-name and password for users and allow them to upload/download files from/to my server

Preferably something secure (real ip on the net, but behind fw) 
and easy to install/manage

I know I can probably do this with apache, but am not a webdev and not good with http

My leet google searching skills are failing me on this one :) ... can some1 please point me in the right direction?

Thanks

---

### Post by HiImTye on 2009-08-31
try proftpd. you'll need to make sure your router will allow it

you'll also need to make sure that your ISP doesn't block the default port. if it does, try a higher port (I use 65500 because it's easy to remember and nothing else uses ports that high)

to access your server you'll need to ```
[ftp://your.ip:port]("ftp://your.ip/")
``` in a browser or use an ftp program and change the port to whatever port you use (if you changed the default port). if you use the default port then you don't need the ```
:port
``` in the browser

---

### Post by P4man on 2009-08-31
why do you say "http" ? Is that because its needs to be http protocol, or because it needs to be on port 80 (default for http) ?

If its the latter, you can easily run any ftp server, and set it to listen to port 80.

---

### Post by Midrian on 2009-08-31
When I say http I mean that I would like the users to be able to use a browser (IE or firefox) and go to [http://196.22.*.*/webftpwhatever](http://196.22.*.*/webftpwhatever) and use a browser to be able to upload or download....

(ftp is too difficult for some ppl... sheesh)

I have a fixed ip available in a dmz behind a firewall with a ubuntu server available for this purpose

---

### Post by nikhilk on 2009-08-31
> **Midrian said:**
> When I say http I mean that I would like the users to be able to use a browser (IE or firefox) and go to [http://196.22.*.*/webftpwhatever](http://196.22.*.*/webftpwhatever) and use a browser to be able to upload or download....

(ftp is too difficult for some ppl... sheesh)

I have a fixed ip available in a dmz behind a firewall with a ubuntu server available for this purpose

I suggest using apache2 for this purpose.

Initial configuration is not too hard as the documentation is quite good. It is a very secure and fast web server, among the best free servers available, so give it a try.

A bit old but still useful instructions on setting up Apache2 on Ubuntu can be found [here]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html").

---

### Post by Midrian on 2009-08-31
I would prefer not having to go and write my own html pages if possible since that is something which I have very little experience in. 

Any stand alone applications for this purpose?

---

### Post by Ratscallion on 2009-08-31
Ok, urm you could get a free domain from [http://co.cc](http://co.cc) and host it (for free again) from [http://000webhost.com](http://000webhost.com) which first of all has its own file manager, but you can use FileZilla with it (which I do on both Windows and Linux) and find it really good and useful. You'll need to shove an index.php file into every folder, but I think there's some sort of script that can make one, but I don't know php so can't help you there.. sorry.

---

### Post by Midrian on 2009-08-31
Would installing a groupware application like egroupware or alfresco be able to do this?

---

