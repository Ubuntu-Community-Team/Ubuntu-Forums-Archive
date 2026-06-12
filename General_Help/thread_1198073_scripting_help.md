---
title: "scripting help"
date: 2009-06-27
forum: General Help
---

### Post by waydownsouth on 2009-06-27
First up, not sure if this the right place, but, if a mod wants to shift it to a better place then please do.

The problem I am faced with is as follows:
I'm currently working on a project of setting up an online web catalogue.
I have over 400 files (jpeg's & pdf's) to upload to this site.
The site has no facility for bulk uploads via FTP nor via the web interface.
According to the creator of the sites software, the only way to get these files to propagate to the database correctly is to go about it one by one via the web.
this involves:

clicking on a link to upload a new resource (page refresh)
browsing for the file to upload (page refresh)
giving a name to the resource (we'll be naming the same as the file name) selecting a couple of check boxes and clicking upload (page refresh once the transfer is complete)
& then repeat this several... ](*,)hundred... ](*,)times... ](*,)

As you can imagine, having to babysit each individual upload will be a hugely time consuming, mind numbing experience

My question,
what is going to be the best way to automate this process? scripts or otherwise?
Any ideas and advice on this would be hugely appreciated as I'm a bit of a newbie to scripting and stuff. I am quite prepared to learn, but, have no idea as to where to start.

Thanks in advance

---

### Post by HermanAB on 2009-06-27
Howdy,

You need a combination of Expect, Perl and Wget.

After a few hundred debug cycles you should have it down pat and then you can  do your few hundred uploads at the click of a single button.

It won't save you any time, but it will likely be less mind numbing.
;)

---

### Post by waydownsouth on 2009-06-27
Hi, thanks for the response.

I'm currently looking at a windows program called iMacros which may do what I'm after (still looking into that though).
But, thought I'd ask some people more experienced than I as to how they might do it.

Either way I've got some reading to do, hopefully might learn something too...

---

### Post by siryuhan on 2009-06-27
This is very easy to implement in Python with mechanize.

[http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)

---

### Post by waydownsouth on 2009-06-27
Hi, thanks for the link,

Some more reading to add to the list...
Re Python, is there a good site that anyone can recommend to help get started in learning about it?

---

### Post by siryuhan on 2009-06-27
> **waydownsouth said:**
> Hi, thanks for the link,

Some more reading to add to the list...
Re Python, is there a good site that anyone can recommend to help get started in learning about it?

[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

---

