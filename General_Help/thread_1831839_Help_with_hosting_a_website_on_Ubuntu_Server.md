---
title: "Help with hosting a website on Ubuntu Server"
date: 2011-08-23
forum: General Help
---

### Post by b0j on 2011-08-23
OK, so I want to host a website on my Ubuntu Server. I will buy a domain  name as soon as I know how to host a website. I have a few questions: 
1) Can I host a website without Apache (or similar), just Ubuntu Server?
2)  If the answer to the above question is yes, how do I do that? I am  fairly sure there is a folder (that I probably need root access to view  and I know how to do gain root access) but I have no clue where I would  find that folder.
3) Finally, there is a Terminal command called  chmod and from what I have been reading, you use it to change who can  view that file (I may be wrong about this). I was wondering what chmod I  have to use to make files public or private, etc.

Thanks for any help/support,
B0J

---

### Post by papibe on 2011-08-23
1. Yes, you can host a web server without Apache. But you will need a http/web server, not just the Ubuntu Server ([nginx]("http://en.wikipedia.org/wiki/Nginx") for example).

Regards.

---

### Post by b0j on 2011-08-23
> **papibe said:**
> 1. Yes, you can host a web server without Apache. But you will need a http/web server, not just the Ubuntu Server ([nginx]("http://en.wikipedia.org/wiki/Nginx") for example).

Regards.
OK, thanks for the help. And I assume that there is some documentation on how to use it?

---

### Post by papibe on 2011-08-23
Lately it has became very popular to install LAMP (Linix Apache MySQL PHP), so there's more information and tutorials about that.

If you go the nginx way, you'll have look for much sources of information and support than the forums. For example, after a quick google search I found [this]("http://library.linode.com/web-servers/nginx/installation/ubuntu-10.04-lucid") tutorial.

Hope it helps,
Regards.

---

### Post by crazyness003 on 2011-08-24
I'm no expert here, but this is my take on your questions:
Ubuntu Server is an Operating System, not a web server. Like Papibe mentioned, nginx is a good alternative. Lighttpd is another web serve you may want to give a shot. I'm sure there's a plethora of web servers out there, but the point is, you need one installed onyour Ubuntu OS in order to host pages to the web.

As for chmod, it basically changes the file/folder permissions. It's used to 'lock out' other groups or users on your local machine. Chmod along with Chown are used to keep files safer from listing, viewing and most importantly, editing. Relating to your situation, if you run a web server, there are an insane number of parameters used to configure what is viewable to the public and what is not.

One thing you need to understand is that when someone 'hits' your site, they use your web server to view whatever file you want them (or dont want them to view). So, you need to look at it in that respect. Your web server is the "web-surfer's" gateway to your filesystem. Thus, limiting your web server's permissions, limits the web-surfer's permissions.

For file permissions, I highly recommend you read up on it extensively. If you dont 100% understand how it works, you may end up compromising your system, or in opposite effect not give permission to host anything to your web server. 
Just keep one thing in mind: NEVER allow your file that you host to have chmod of 777, unless you EXPLICITLY want to. This give EVERYONE the right to modify and execute that file.

Hope this kinda sheds some light to your question. Again, I'm not an expert, but I've been poking in this for about two years now. So, I feel kinda comfortable.

---

### Post by Wim Sturkenboom on 2011-08-24
I strongly suggest that you play with it (at home) before you actually use it for hosting.

I'm personally not in favor of the approach for standard installs. LAMP will serve files from /var/www which is theoritically a 'stupid' place; the 'var' directory is for pseudo temporary stuff (logs, spool) in my opinion, not for permanent stuff like websites (and mysql databases).

So I suggest that you place your website somewhere in your home directory and point the webserver's document root to there (read up on *_document root_* if you use apache; don't know what it is called in other httpd servers).

Only disadvantage is that your httpd server can't write there; lots of users don't have a need for that but if you have to allow the httpd server to write in there, you can make a dedicated subdirectory in your website (document root) where apache can write (I use ACL for that, something else that you need to read up on if you want to use it), a chmod in combination with chown will also do.

Good luck.

---

