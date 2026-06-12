---
title: "wildcard in /etc/hosts, (*.mydomain.com)"
date: 2010-03-01
forum: General Help
---

### Post by artheus on 2010-03-01
Hey!

I recently stumbled over the problem that I can't use wildcards like *.mydomain.com in the /etc/hosts file, which is very sad.

So I searched the forum and found a post (link below)
[http://ubuntuforums.org/showthread.php?t=437868](http://ubuntuforums.org/showthread.php?t=437868)

Well... Not very much help.. But I made a small script to make it easier to add entries to /etc/hosts. I thought I would contribute this to the forum. (below)

But.. I would really like to know if there is any other way to solve this. Some workaround so I can use wildcards in my hosts file. Or something?

[PHP]
#!/bin/bash

domain=$1;

echo "127.0.1.1" $domain >> /etc/hosts;
echo "127.0.1.1" www.$domain >> /etc/hosts;
echo "127.0.1.1" mail.$domain >> /etc/hosts;
[/PHP]

Not a very big script.. but It helps!

Simple usage:
1. Put this script in a file in eg. your home folder.
2. Make the changes you want.
3. Open terminal
4. Browse to the script folder
5. Make the script executable "chmod +x domainadd", instead of "domainadd" write the name you gave your file.
6. Call script "sudo ./domainadd mydomain.com" change mydomain.com to the desired domainname.

Remeber to run it as sudo! And feel free to make any changes.

Cheers,
Artheus

---

