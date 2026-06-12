---
title: "Problems with Apapche 2 on ubuntu"
date: 2009-10-31
forum: General Help
---

### Post by samibdr on 2009-10-31
Hello,
 
i have a redirection on my htaccess that redirects users from non www to www. i recently had to setup a redirection in htaccess to redirect users to https: for 2 directories i have on my website since they are a login directory.
 
when i added the code in htaccess, the site generated an error. tho code is 
 
```
RewriteEngine On 
RewriteCond %{HTTPS} !=on
RewriteRule ^admin [https://%{SERVER_NAME}%{REQUEST_URI](https://%{SERVER_NAME}%{REQUEST_URI)} [R,L]
RewriteRule ^index/viewbooking [https://%{SERVER_NAME}%{REQUEST_URI](https://%{SERVER_NAME}%{REQUEST_URI)} [R,L]
```
 
then i noticed that when i removed the code that redirects from non www to www, the above code worked. below is the code i use to redirect from non www to www.
 
```

[FONT=Courier New][SIZE=2]RewriteEngine On[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]RewriteCond %{HTTP_HOST} !^www.example.com[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]RewriteRule ^.*$ [http://www.example.com%{REQUEST_URI](http://www.example.com%{REQUEST_URI)} [R=301,L][/SIZE][/FONT]

```
 
could you please advice how can i use these 2 together cos i need them both to be working at the same time.
 
Thanks
Sami

---

