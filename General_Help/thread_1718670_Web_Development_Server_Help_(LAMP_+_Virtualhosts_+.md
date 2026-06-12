---
title: "Web Development Server Help (LAMP + Virtualhosts + SVN + VSFTPD)"
date: 2011-03-31
forum: General Help
---

### Post by a3648416 on 2011-03-31
Hi

i need some help with setting up my web development server on UBUNTU 10.04 LTS. I don't have a domain. And not planing on using one. just simple IP address or free dns address redirect. i heard its possible if u put something like this into your /etc/hosts file on remote location you can open the subdomain of IP. 

```

IP subdomain.localhost
IP subdomain2.localhost
...
..
.

```The idea is to have LAMP server with subversion of web projects. Projects are static/dynamic webpages

So for 1 project -> 3 subdomains:
svn.localhost (last svn revision)
user1.localhost (user1 local subversion checkout probably /home/user1/svn/project)
user2.localhost (user2 local subversion chechkout probably /home/user2/svn/project)

so in webbrowser:

[http://svn.localhost/](http://svn.localhost/)    is the last servers SVN revision of web project

[http://user1.localhost/](http://user1.localhost/)     is the servers local version of user1's web project
[http://user2.localhost/](http://user2.localhost/)     is the servers local version of user2's web project

Generaly there will be 2 users who are editing the same webpage project via FTP and testing it localy on the server so that they don't need to commit it to SVN after every edited line. The Project requieres Apache to test. They commit at the end of the day or when they make some big differance to the page.

i need passworded SVN checkout and update for user1 and user2 the same goes to their FTP access probably vsftpd.

I won't have problems with installing apache,php,mysql,webmin,phpmyadmin,
and subversion, port forwarding.

but i need everything else in details. 
[B]apache virtualhosts configuration
permissions of folders and files[/B]
[B]vsftpd installation and configuration
details on how to connect to FTP and subdomain from remote location if only having the IP of the server without domain name.

[/B]thank you

---

