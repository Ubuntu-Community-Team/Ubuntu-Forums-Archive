---
title: "wget works... just not with this URL..."
date: 2009-08-06
forum: General Help
---

### Post by thaitang on 2009-08-06
Hi Gang,

I have read some previous posts regarding wget, but found nothing to address my particular problem.

I have a URL that wget just doesn't seem to recursively grab a site's webpages from.. the comand I am using is:
```
wget --wait=5 --limit-rate=20K -r -p -U Mozilla http://www.wsu.edu/~brians/errors/errors.html
```

I have never had a problem grabbing pages from a site before with this command, but this site (included in the command example) grabs the index.html page and then quits.

I tried another random sites and the command works fine. Any ideas what this website is doing to stop recursive downloads or an option that is needs, but that I might not be including?

appreciate it, there are a lot of links to click on to grab what I need from this site, so I hope wget can do it for me.

cheers,
tt

---

### Post by slakkie on 2009-08-06
> 
       Wget can follow links in HTML and XHTML pages and create local versions of remote web sites, fully recreating the directory structure of the
       original site.  This is sometimes referred to as "recursive downloading."  While doing that, Wget respects the Robot Exclusion Standard
       (/robots.txt).  Wget can be instructed to convert the links in downloaded HTML files to the local files for offline viewing.


And that site has a robots.txt disallowing all useragents..

---

### Post by Johnny B on 2009-08-06
i don't know why its not downloading recursively, but why not try:
> while true ; do sleep 5 ; wget --wait=5 --limit-rate=20K -r -p -U Mozilla [http://www.wsu.edu/~brians/errors/errors.html](http://www.wsu.edu/~brians/errors/errors.html) ; done

---

### Post by thaitang on 2009-08-06
```
And that site has a robots.txt disallowing all useragents..
```
Ok, all is right in the universe once more. Thanks for pointing me in the right direction. I just turned off robots option in /etc/wgetrc and I am pulling down those website pages as we speak.

I never ran into a site with a robot.txt file before. Thanks again.

cheers,
tt

---

