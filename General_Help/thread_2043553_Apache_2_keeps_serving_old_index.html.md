---
title: "Apache 2 keeps serving old index.html"
date: 2012-08-16
forum: General Help
---

### Post by Kurir on 2012-08-16
Hi all,

Having an issue with apache2.

Got a web server set up, all seems to be working, but it keeps serving an older version(I've changed it 3 or 4 times today alone) of the index file. While I can get around this easy enough, the client I am doing work for would not know how to do this.

I should note that it serves the updated php files behind it, just not the html page itself.

Any idea why it would be serving what I guess is a cached page, and how I can stop it?

Thanks,

Kurir

---

### Post by LeBurt on 2012-08-16
Kurir, if you're certain this is not caching on the browser side, you could always check if your apache has mod_cache enabled. Normally you wouldn't unless you have activated it manually.

Try:
ls -l /etc/apaches2/mods-enabled/

What do you see in there?

Also, are you using a development framework to publish your pages, something like Symfony or CodeIgniter? Those often have caching of their own.

---

### Post by plugwash on 2012-08-16
Are you positive it's happening on the server and not the client?

In particular make sure your server clock and file dates are all sane. If not then client caching will do really weird stuff.

---

### Post by Kurir on 2012-08-16
I dont see any cache mods on in the list, and I am using CodeIgniter. However this index page is not part of CodeIgniter, only calls an index.php which is part of CodeIgniter.

I don't believe it is client side caching, as I tested it on chrome, my usual browser, and got the problem first, then I tested it on IE, which I dont believe I have used to browse to the site before, and still got the same problem.

I cleared my client side cache and noticed that it now updates to a newer page, but still not the correct page.

---

### Post by Kurir on 2012-08-17
bump

---

### Post by LeBurt on 2012-08-17
Even though it doesn't appear to the source of the problem, I'd still try to clear the CodeIgniter cache.

[http://codeigniter.com/user_guide/general/caching.html](http://codeigniter.com/user_guide/general/caching.html)

---

### Post by Kurir on 2012-08-17
Thanks, it seems to have caught up to itself now, but I can see this becoming an issue if it keeps displaying cached pages instead of the latest, if things are changed, as they usually are in a website

Checking the controllers revealed no trace of the line needed for caching and the one file in the folder does not correlate to the one seemingly being cached. Which begs the question, where is the caching occuring? It seems it must be happening in apache but there doesnt seem to be a cache mod enabled and I havnt told it to enable.

---

### Post by LeBurt on 2012-08-17
I haven't worked with CodeIgniter itself but as these frameworks go, they always manage their own cache so it's not at the apache level. This means that each time a page is requested, the index.php will first check if there is a version of the page already built and serve it rather than building it again. From the link I sent you, you could set an expiry time on cached pages, say for one minute. Everytime you would change the content of that page, you'd have to wait maximum one minute before the new one is built and served. There is probably a place somewhere in CodeIgniter where you can set this value globally for all pages or even disable caching altogether. 

Usually, it's a good thing to keep it on, set a global value of, say, 10 minutes. The rest you can manage individually in your controller if you want a page to expire quicker.

---

