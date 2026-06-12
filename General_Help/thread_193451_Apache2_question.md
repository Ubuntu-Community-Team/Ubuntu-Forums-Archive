---
title: "Apache2 question"
date: 2006-06-10
forum: General Help
---

### Post by horatiub on 2006-06-10
I'm trying to figure out something and I just can't. I have installed apache2 on my Dapper and I'm confused about the config files. I know that the older apache used to use the httpd.conf file and the new version actually uses the sites-available/default file. For some reason, my httpd.conf file still has the Virtual server that I setup in the sites-available/default file. I thought that all the website that you wanna use, should be setup in the default file under sites-available. But every time I try to add a new website, the content of my main virtual gets forwarded onto the new website.

So basically, what's the story with httpd.conf and sites-available/default?

Thank you for your help

---

### Post by scxtt on 2006-06-10
look for an apache2.conf (possibly apache.conf) file ...

slocate (from the terminal) is my fav search tool ... it's basically taken over for httpd.conf ...

---

### Post by horatiub on 2006-06-10
[QUOTE=scxtt]look for an apache2.conf (possibly apache.conf) file ...

slocate (from the terminal) is my fav search tool ... it's basically taken over for httpd.conf ...[/QUOTE]
Ok, I know where apache2.conf is. It's still in etc/apache2 directory with the httpd.conf file. 

So what do I do next?

---

### Post by scxtt on 2006-06-10
what exactly is it you're trying to do w/ "sites-available/default" and the virtual server?

---

### Post by horatiub on 2006-06-10
I would like to add one more website on my server. Right now, I have a default file in the sites-available and this default file has a virtual server setup for domain1.com. Now I just wanna add a domain2.com. I copied all the lines between the virtual host and the </virtualhost>, I edited the directory, the document path, but each time I try to access domain2.com, I get the content from domain1.com. It looks like it's forwarding to my domain2

---

### Post by scxtt on 2006-06-10
ahh, that's something i never messed with, so i can't be much more help (and i don't have apache installed now [no need for it currently]) ... the only generic idea i have is:

have you restarted apache since the changes?

---

### Post by Ixzat on 2006-06-10
Care to share the config files so we can see what the problem could be?

---

### Post by horatiub on 2006-06-10
which files exactly would you need?

---

