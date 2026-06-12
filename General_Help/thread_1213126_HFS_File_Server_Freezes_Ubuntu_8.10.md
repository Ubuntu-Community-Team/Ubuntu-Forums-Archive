---
title: "HFS File Server Freezes Ubuntu 8.10"
date: 2009-07-14
forum: General Help
---

### Post by Lingonet on 2009-07-14
Hello!

I just stumbled upon this sweet sharing client and downloaded the .exe-file for Wine. On Wines website, they have tested it with no problem. I though have a problem. When I started it for the first time it worked good, I added a file and could go on the url on Firefox. Then I added another file and pressed the file on the program, that wasn't good. First the program turned grey, then the mouse started to lag and I couldn't do a thing, I couldn't navigate, not press anything, not even the panels. Finally Ubuntu forced the program to close and everything turned out normal. I tried to open it again and the same thing happened! Before this happened I saved a save-file as hfs.ini to the registry as in Windows, could it have anything to do with that?

What is this problem and how do I solve it?

I appreciate help!

Thank you!

-Lingot

---

### Post by SlugSlug on 2009-07-14
> **Lingonet said:**
> Hello!

I just stumbled upon this sweet sharing client and downloaded the .exe-file for Wine. On Wines website, they have tested it with no problem. I though have a problem. When I started it for the first time it worked good, I added a file and could go on the url on Firefox. Then I added another file and pressed the file on the program, that wasn't good. First the program turned grey, then the mouse started to lag and I couldn't do a thing, I couldn't navigate, not press anything, not even the panels. Finally Ubuntu forced the program to close and everything turned out normal. I tried to open it again and the same thing happened! Before this happened I saved a save-file as hfs.ini to the registry as in Windows, could it have anything to do with that?

What is this problem and how do I solve it?

I appreciate help!

Thank you!

-Lingot

humm, thats great for windows but why not set your self a bit more security up and get apache running on HTTPS - loads of guides and how to's..

---

### Post by Lingonet on 2009-07-14
> **SlugSlug said:**
> humm, thats great for windows but why not set your self a bit more security up and get apache running on HTTPS - loads of guides and how to's..

Now I didn't really get that. What would help the freezing with setting up security on the HTTPS?

-Lingot

---

### Post by SlugSlug on 2009-07-14
> **Lingonet said:**
> Now I didn't really get that. What would help the freezing with setting up security on the HTTPS?

-Lingot

Sorry, I was recommending using apache instead of that win app, you can do a lot more with one being HTTPS which will encript the data between you and the downloader the other would be a more secure access to the shared files.

---

### Post by Lingonet on 2009-07-14
> **SlugSlug said:**
> Sorry, I was recommending using apache instead of that win app, you can do a lot more with one being HTTPS which will encript the data between you and the downloader the other would be a more secure access to the shared files.

I don't understand what you're talking about. The problem is that the program freezes, stops, that doesn't have anything to do with security.

Thanks!

---

### Post by SlugSlug on 2009-07-14
> **Lingonet said:**
> I don't understand what you're talking about. The problem is that the program freezes, stops, that doesn't have anything to do with security.

Thanks!

I was suggesting you use apache instead of HFS Server

- you will be happy you did !

---

### Post by SlugSlug on 2009-07-14
the inital setup is real easy but from there you can keep adding to it / learning more... here is a kinda guide into it... [http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html](http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html)

google will help you out with a load of stuff about it!!

---

### Post by Lingonet on 2009-07-15
> **SlugSlug said:**
> I was suggesting you use apache instead of HFS Server

- you will be happy you did !

You were right! I became happy! Now I use Apache with the configuration tool Rapache on a HTTP-server!

Thank you! This is much better than HFS!

-Lingot

---

### Post by Lingonet on 2009-07-15
> **SlugSlug said:**
> the inital setup is real easy but from there you can keep adding to it / learning more... here is a kinda guide into it... [http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html](http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html)

google will help you out with a load of stuff about it!!

Now I already have one problem:

I have the server running and I tried to connect from another computer but it didn't work. Why is this? I connected in Firefox but it told me that the server couldn't be found.

Thank you!

---

### Post by SlugSlug on 2009-07-15
> **Lingonet said:**
> Now I already have one problem:

I have the server running and I tried to connect from another computer but it didn't work. Why is this? I connected in Firefox but it told me that the server couldn't be found.

Thank you!

If your connecting from another pc over the internet you will need to forward port 80 (or 443 if HTTPS) from your router to your PC

A nice walkthrough is at [http://portforward.com](http://portforward.com)

---

### Post by Lingonet on 2009-07-15
> **SlugSlug said:**
> If your connecting from another pc over the internet you will need to forward port 80 (or 443 if HTTPS) from your router to your PC

A nice walkthrough is at [http://portforward.com](http://portforward.com)

I tried to forward both ports but it didn't work.

I have set apache up with the url [http://127.12.34.56]("http://127.12.34.56") on port 80, but I can only go on it on the Ubuntu-PC.

Thank you!

---

### Post by SlugSlug on 2009-07-15
> **Lingonet said:**
> I tried to forward both ports but it didn't work.

I have set apache up with the url [http://127.12.34.56]("http://127.12.34.56") on port 80, but I can only go on it on the Ubuntu-PC.

Thank you!

Dnt mean to sound funny here, but are you connecting to using your external IP (found here [www.whatismyip.com](www.whatismyip.com))

If you can connect locally using your internal address then It does seem like a port forward issue.

unless you have put some security on it so its only allowing certain IP address?

---

### Post by Lingonet on 2009-07-15
> **SlugSlug said:**
> Dnt mean to sound funny here, but are you connecting to using your external IP (found here [www.whatismyip.com](www.whatismyip.com))

If you can connect locally using your internal address then It does seem like a port forward issue.

unless you have put some security on it so its only allowing certain IP address?

When I'm trying to connect with my ISP-IP (ex. 213.00.000.00) and type it in Firefox I get directed to my router for some reason. This IP-adress 127.12.34.56 was given to me by HFS when I used that, I don't know why.

Thank you!

---

### Post by SlugSlug on 2009-07-15
> **Lingonet said:**
> When I'm trying to connect with my ISP-IP (ex. 213.00.000.00) and type it in Firefox I get directed to my router for some reason. This IP-adress 127.12.34.56 was given to me by HFS when I used that, I don't know why.

Thank you!

right OK ,  the 213. one is what you need to use if connecting to home from over internet, thats the one to use but if your local then stick to localhost

you could also visit [http://www.dyndns.com/](http://www.dyndns.com/) create a free account and get an address like [www.some-name-here.webhop.net](www.some-name-here.webhop.net) and that will point to your 213. address

you should also put dnydns login details in router...

---

