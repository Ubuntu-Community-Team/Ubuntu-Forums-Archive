---
title: "How to download an entire website using wget?"
date: 2009-09-10
forum: General Help
---

### Post by djeyewater on 2009-09-10
I want to download a copy of a (local) website using wget (I only need the actual webpages, not images, css etc.). I tried using```
wget -r http://www.photosite.com/
```This created a folder named 'www.photosite.com', and inside that folder was a file called 'index.html', which was the index/home page of my website. But it didn't download any of the other pages.

The links in the page that wget doesn't seem to be following look like this:[HTML]<a href="/"><img src="http://static1.photosite.com/images/Logo.png" alt="logo" /></a>
        <ul id="topNav">
            <li><a href="/photos">Photo Library</a></li>
            <li><a href="/search">Search</a></li>
            <li><a href="/contact">Contact</a></li>
            <li><a href="/blog">Blog</a></li>
        </ul>[/HTML]

The output from wget was```
--2009-09-10 21:53:33--  http://www.photosite.com/
Resolving www.photosite.com... 127.0.0.1
Connecting to www.photosite.com|127.0.0.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/xml]
Saving to: `www.photosite.com/index.html'

    [ <=>                                   ] 2,460       --.-K/s   in 0.008s  

2009-09-10 21:53:33 (290 KB/s) - `www.photosite.com/index.html' saved [2460]

FINISHED --2009-09-10 21:53:33--
Downloaded: 1 files, 2.4K in 0.008s (290 KB/s)

```

Can anyone help me to get wget to download all the pages from the site? (I want to try and use [swish++'s httpindex]("http://swishplusplus.sourceforge.net/man/httpindex.pdf") to create a search index of the site, and this uses wget).

Thanks

Dave

---

### Post by tgalati4 on 2009-09-10
static1.photosite.com is not the same as [www.photosite.com](www.photosite.com), unless you have named it so in your /etc/hosts file.

Not sure if wildcards will work:

wget -r [http://*.photosite.com/](http://*.photosite.com/)

---

### Post by djeyewater on 2009-09-10
static1.photosite.com is named in my hosts file, though I'm not concerned with downloading files from there. 

I want wget to download the pages /photos, /search, /contact, /blog, and any other pages (on the same domain) that those pages link to.

Thanks

Dave

---

### Post by StuartN on 2009-09-10
> **djeyewater said:**
> I want wget to download the pages /photos, /search, /contact, /blog, and any other pages (on the same domain) that those pages link to.

Try adding -H to permit spanning hosts (and -l to limit the depth!) in case wget does not recognize the link as being the same domain.

---

### Post by djeyewater on 2009-09-11
> **StuartN said:**
> Try adding -H to permit spanning hosts (and -l to limit the depth!) in case wget does not recognize the link as being the same domain.

Thanks for the suggestion, but I'm still only get the index page downloaded when I do ```
wget -r -H -l 2 http://www.photosite.com/
```

Dave

---

### Post by P4man on 2009-09-11
Perhaps try httrack?
[http://www.httrack.com/](http://www.httrack.com/)

Its in the universe repo's.

---

### Post by StuartN on 2009-09-11
> **djeyewater said:**
> Thanks for the suggestion, but I'm still only get the index page downloaded

I have tried a couple of URLs and get just my own site with -r and (very nicely) just a robots.txt for most of the sites I have linked to. Try another site to see if the problem is with this one site or with the command.

---

### Post by djeyewater on 2009-09-11
> **P4man said:**
> Perhaps try httrack?
[http://www.httrack.com/](http://www.httrack.com/)

I've installed that, but it doesn't seem to download anything at all (I tried it with and without the trailing slash on the domain name)```
djeyewater@rusty-ubuntu:~/Stuff$ ~/apps/httrack/bin/httrack http://photosite.com/ -O ./photosite.com -K
Mirror launched on Fri, 11 Sep 2009 11:54:01 by HTTrack Website Copier/3.43-7+libhtsjava.so.2 [XR&CO'2008]
mirroring http://photosite.com/ with the wizard help..
Done.photosite.com/ (0 bytes) - -5
Thanks for using HTTrack!
```
I'm not sure whether piping httrack's output into Swish++'s httpindex program would work either (httpindex is designed to have the output of wget piped into it).

Dave

---

### Post by djeyewater on 2009-09-11
> **StuartN said:**
> I have tried a couple of URLs and get just my own site with -r and (very nicely) just a robots.txt for most of the sites I have linked to. Try another site to see if the problem is with this one site or with the command.

I've just tried wget -r with a different site, and it definitely works okay. I wonder why it doesn't work with my site though (lack of file extension on the urls would be my guess, but I don't think there's anything technically wrong with urls that don't end with a trailing slash or file extension)?

Dave

---

### Post by tgalati4 on 2009-09-11
You would have to look at the source code for wget.  It's quite possible that wget looks for htm or html extensions to follow the recursion tree.  I'm not familiar with all of the w3c standards, but I bet naming URL's with *.html is part of the standard.

[Markup Guidelines]("http://www.w3.org/MarkUp/#guidelines")

Otherwise, wget would have to perform a MIME file typing for each file it encounters before it grabs it and recurses on it.

Of course you could run it through the w3c validator and it would spot problems.

---

