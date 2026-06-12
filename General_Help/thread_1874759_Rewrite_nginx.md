---
title: "Rewrite nginx"
date: 2011-11-03
forum: General Help
---

### Post by slurpderp on 2011-11-03
Good evening,
I would like to know how to rewrite a url with nginx correctly

For example: 
I want *[http://domain/?subtopic=herp&derp=this](http://domain/?subtopic=herp&derp=this)* to rewrite to *[http://domain/herp/derp/this](http://domain/herp/derp/this)*

I've tried looking at so many guides with no success

---

### Post by prodigy_ on 2011-11-04
A very simple and untested example:

```
location ~ \?subtopic {
    rewrite subtopic=(.*)&(.*)=(.*) /$1/$2/$3
}
```

However, you really don't want to copypaste this blindly. Consult [nginx wiki](http://wiki.nginx.org/HttpRewriteModule) and write your own rules. If you don't know the syntax of Perl regular expressions, check [Perl documentation](http://perldoc.perl.org/index-language.html) first.

Alternatively you can handle redirects at the PHP level: [http://php.net/manual/en/function.header.php](http://php.net/manual/en/function.header.php)

---

