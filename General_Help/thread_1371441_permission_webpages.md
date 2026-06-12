---
title: "permission webpages"
date: 2010-01-03
forum: General Help
---

### Post by PoetaVV on 2010-01-03
Dear all,

nice to meet you :)
I just aquired a new server on which i installed ubuntu 8.04 lts and lamp

i then installed ftp module and next step will be the mail feature.

Unfortunately i'm totally new to linux/unix style of life but i'm in urge to move my actual webpages to the new server for various reasons.

I'm going mad to solve this problem :

I created under /home a user called poeta and created a public_html
so it comes to :
/home/poeta/public_html/

in this directory i have copied my forum.

Then i go on the browser and open the pages to try the installation (using vbulletin forum) but it gives **403 forbidden access**.

I uploaded everything with the user root using ftp

how can i manage not to chown -R everything all the time?

I tried using the user poeta with the ftp but it does not allow me to create folders, that is why i uploaded the data with the user root.


Other question,
how to i create a newlevel.myweb.com sub level?
Where do i copy the files? I need to create a folder under /html_public/newlevel/?
And where i tell apache that that folder redirects to newlevel.myweb.com and not myweb.com/newlevel?

Sorry for my poor english :/

Thanks and best regards,

Simon

---

### Post by mörgæs on 2010-01-04
Does this help:

[http://httpd.apache.org/docs/2.0/howto/public_html.html](http://httpd.apache.org/docs/2.0/howto/public_html.html)
[http://www.brennan.id.au/13-Apache_Web_Server.html#users](http://www.brennan.id.au/13-Apache_Web_Server.html#users)

Maybe a good idea is to change your title to something with 'Apache' to attract attention.

---

