---
title: "server software"
date: 2010-08-30
forum: General Help
---

### Post by grandshreyan on 2010-08-30
Hi there I am new for this forum.
I am trying to built a server for my home use. I installed ubuntu server 10.04. and I don't know how to setup that server work. Because I have 0 knowledge on using commands. Is there any server software that come with GUI. 
If anyone can help me please help
Thanks

---

### Post by Autodidact on 2010-08-30
What kind of server do you need?

Apache, a commonly used web server, is already on your system. 
Open Firefox and point it to: [http://localhost/](http://localhost/) (or your IP address)

The root folder for apache is /var/www/.
Place you desired files in there (and remove the index.html file).
Then reload the page in Firefox, the files should show up now.

No command line needed for this.
This way you can run simple static webpages or share files.

---

