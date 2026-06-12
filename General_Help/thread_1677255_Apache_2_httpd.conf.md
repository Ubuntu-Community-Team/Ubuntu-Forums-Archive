---
title: "Apache 2 httpd.conf"
date: 2011-01-28
forum: General Help
---

### Post by minerbog on 2011-01-28
Hi All,

Wasn't sure where to post this so hey!! here it is!!

I have tried everything to get this working but I cannot work out why.

Here is my httpd.conf file in apache
```

<VirtualHost *:80>
RewriteEngine On
RewriteCond %{REMOTE_ADDR} ^192\.168\.0\.*$
RewriteCond %{SERVER_PORT} !^443$
RewriteRule ^/(.*) https://my.domain.com/$1 [NC,R,L]
</VirtualHost>

```

The rewrite worked with just checking the server port and redirect to https. But I want it to check to see if the user is on the local lan. If so, abort the rewrite all together as https isn't needed locally.

Many Thanks

Gav.

---

### Post by wormyblackburny on 2011-01-28
Take this for what it is worth, as I am no Apache guru by any means..... So, in your rule it basically says
Condition 1: IP range is IN 192.168.0.X
Condition 2: It is NOT coming in via https
Then > send it to https (rewrite it)

From [http://httpd.apache.org/docs/2.2/rewrite/rewrite_intro.html](http://httpd.apache.org/docs/2.2/rewrite/rewrite_intro.html)
States "When more than one [RewriteCond]("http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html#rewritecond") is specified, they must all match for the [RewriteRule]("http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html#rewriterule") to be applied."

So basically you are saying with your rule to send everything from your local domain that isnt coming in via https needs to be sent to https. You need to do the opposite:

Condition1 : IP range is NOT in 192.168.0.*
Condition 2: Request is NOT on port 443
Then>> Rewrite it to https

<VirtualHost *:80>
RewriteEngine On
RewriteCond %{REMOTE_ADDR} !^192\.168\.0\.*$
RewriteCond %{SERVER_PORT} !^443$
RewriteRule ^/(.*) https://my.domain.com/$1 [NC,R,L]
</VirtualHost>

---

### Post by minerbog on 2011-01-28
> **wormyblackburny said:**
> 
From [http://httpd.apache.org/docs/2.2/rewrite/rewrite_intro.html](http://httpd.apache.org/docs/2.2/rewrite/rewrite_intro.html)
States "When more than one [RewriteCond]("http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html#rewritecond") is specified, they must all match for the [RewriteRule]("http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html#rewriterule") to be applied."

So basically you are saying with your rule to send everything from your local domain that isn't coming in via https needs to be sent to https. You need to do the opposite:


Ahhhh, I did not know this!! What I'm really after is if the user is on the local domain then use without https, but if the user is remote force https.

If both have to match to get a result then I'm going about it all wrong :)!

What I would love to use is a if statment!
```

if (%{REMOTE_ADDR} = 192.168.0.*) {
//then do nothing
} else {
RewriteCond %{SERVER_PORT} !^443$
RewriteRule ^?(.*) https://my.domain.com/$1 [NC,R,L}
}
```
Don't suppose this is possible with apache??

Thanks

Gav.

---

### Post by wormyblackburny on 2011-01-29
I'm not sure on that one Gavin. Since it's a conf file, I doubt it will accept any kind of bash scripting or programming language. Either way, I'm pretty sure what i wrote above should suffice. The only thing it is missing is:

what if you have a local machine that for some reason **IS **coming in on 443.... then it meets neither condition. In that condition, you would want the local machine booted back on to 80. 

Like I said, I'm no Apache guru, but I wonder if it's possible for you to just write another set of conditions and put it right after the first set that could act like an "else" statement and address that one loophole.... I bet you can, but probably have to be really careful in case it is possible for something to meet BOTH sets of conditions, in which case it would be telling it to do two different things at the same time... :( That would be no bueno!

---

### Post by v8YKxgHe on 2011-01-29
```
**<VirtualHost *:80>**
RewriteEngine On
RewriteCond %{REMOTE_ADDR} ^192\.168\.0\.*$
RewriteCond %{SERVER_PORT} !^443$
RewriteRule ^/(.*) https://my.domain.com/$1 [NC,R,L]
</VirtualHost>
```

How can it ever be port 443 when this virtual host is for port 80?

---

### Post by minerbog on 2011-01-30
> **AlexC_ said:**
> ```
**<VirtualHost *:80>**
RewriteEngine On
RewriteCond %{REMOTE_ADDR} ^192\.168\.0\.*$
RewriteCond %{SERVER_PORT} !^443$
RewriteRule ^/(.*) https://my.domain.com/$1 [NC,R,L]
</VirtualHost>
```

How can it ever be port 443 when this virtual host is for port 80?

Isn't it beacause the inbound port for the host is port 80. Then it forces 443 because its not on 443?? Or would it be best to create a virtual host on port 443? But then surely anyone connections coming for port 80 would then be refused??

NB. I quite new to apache configuration!!!! :)

---

### Post by wormyblackburny on 2011-01-31
I dunno, but it seems to me that you may as well just push all the traffic to 443. Why have intranet traffic 80 and external traffic 443?

---

### Post by minerbog on 2011-05-27
I know its a late reply but the idea was to save server resourses by having local traffic only use the less intense http protocol, but after some reasearch and benchmarking the difference isn't really worth me worrying about! If the load was greater than it is maybe, but for now its all on port 443.

Thanks.

---

