---
title: "ubuntu server - wget fail to get this file?"
date: 2011-05-13
forum: General Help
---

### Post by chuawenching on 2011-05-13
Hi everyone,

I am using Ubuntu Server 10.04.2 LTS 32 bits.

I need to download this file via

wget [http://www.theopensourcerer.com/wp-content/uploads/2011/04/openerp-server](http://www.theopensourcerer.com/wp-content/uploads/2011/04/openerp-server)

and save as openerp-server (no extension)

and when I do that, it will save the html source of this page instead of the actual plain text. That's not what i want.

However, if I try to download this instead

wget [http://www.theopensourcerer.com/wp-content/uploads/2011/04/openerp-server.conf](http://www.theopensourcerer.com/wp-content/uploads/2011/04/openerp-server.conf)

it works. I assume the latter has extensions than the earlier one.

Any help? coz the server has only terminal.. not sure how to grab that file.

Thanks.

---

### Post by chuawenching on 2011-05-13
any help please?

---

### Post by chuawenching on 2011-05-25
yeah it is working now, not sure why. I try again and it worked fine :( maybe it didn't download properly last time. Thanks anyway.

---

### Post by Habitual on 2011-05-27
alternate method:
```
curl "http://www.theopensourcerer.com/wp-content/uploads/2011/04/openerp-server" -o openerp-server
```

check dir where you ran that command for openrp-server file.

---

### Post by doas777 on 2011-05-27
I think adding .config to the end may not have worked as well as it appears. the opensourcerer defaults 404 errors (page not found) to a page that says "sorry, no posts were found", and I am afraid the file you downloaded may be this one. 
if you 'cat' it, does it start with '#!/bin/sh' ? if it does, then you are good to go. if not, try habitual's curl command. if all else fails, it;s just a text file, so you could copy it down now while you are booted with a browser, and transfer the file to the server instead of downloading it with wget or curl.

as for why its happening, the reason, is rather complicated, but it comes down to how a HTTP server knows what you are asking it to do.
http's most basic client command is 'GET </file/path.ext>'
when you use wget to well, web GET a file, the server receives the request and determines what you want to do. an HTML document is a static text document, so the server responds by sending you a bytestream containing the text of the file, and indicates via MIME type, that your file is an html document. your browser then "reads" the file and renders it according to the browsers html spec.

when you request an application file like .php/.aspx/.jsp etc, the server detects the type of the file you have asked for and executes an appropriate "Handler". an ASPX/PHP handler will compile and execute a program that renders and creates an html document, and returns it, much the same way that a regular html works, but this time the document is not static. 

when you download a file, the MIME type tells your PC what to do with it. if the MIME type is incorrectly set in a response the client computer won't get instructions on what to do with the file, so it just downloads it as text and attempts to display it, because thats the default option. if you don't indicate what handler you need, the handler never fires and thus does not get the opportunity to set the MIME type, so instead of the file you wished to download and save as bytestream, you get the text contained in the file.

---

