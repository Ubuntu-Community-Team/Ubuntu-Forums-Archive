---
title: "Free online website builder BUT I need the code as well..."
date: 2012-09-13
forum: General Help
---

### Post by suomalainen on 2012-09-13
Ubunteros,

Would anyone know of any online website building tools (WYSIWYG) where I can create a website online and also get the code for the site I create?? 

I can host the website myself thus I need the code?

Thank you!

---

### Post by Lars Noodén on 2012-09-13
Most people that go that route choose a CMS like [Drupal](https://drupal.org/), [Plone](https://plone.org/) or [OpenCMS](http://www.opencms.org/).  Those come with the source code.

If you're just wanting to generate web pages, you could use Bluefish, Amaya or Kompozer and upload them.  What is it that you are looking for in an online version that is not available in the regular tools?

---

### Post by suomalainen on 2012-09-13
Thanks for the reply,

I have tried Bluefish and was under the impression it was WYSIWYG but I didn't see this option.

The drag & drop method is the easiest method for me to work with as I am not an experienced coder or website developer.

I was working with WIX and then soon discovered you gotta have a paying account to get the source code.

I just thought there were online website builders where I can get fancy templates, drag & drop, etc.... Create the website, get the published code and host it myself.

Suomalainen

---

### Post by Lars Noodén on 2012-09-13
Online tools might exist, it's just that I haven't followed them at all.  

[Bluefish](http://bluefish.openoffice.nl/manual/) comes with a fine manual that explains a lot of functions but it does not seem to have preview mode.  So that rules it out for your task.

Just so you know, each browser is going to render the page a little differently depending on factors like configuration, screen size and resolution, typefaces available, window size and aspect ratio, and so on.  So in the web world, claims of WYSIWYG are lies.  If you want hard and fast layout the same on each client's machine, then PDF is about your only option.

But just to get started, you might find [Kompozer](http://www.kompozer.net/) easier than Bluefish.  To go back and forth between the layout preview and the raw HTML code is just the click of a tab.  Or you can transfer the files using SFTP or your file manager such as Nautilus or Dolphin.

---

### Post by Bucky Ball on 2012-09-13
*Thread moved to **General Help***

Reason: Community Cafe is not a support sub-forum. Good luck. ;)

[QUOTE=Community Cafe Description]The Community Chat area is for lighthearted and enjoyable discussions, like you might find around a water cooler at work. Almost any non-tech-support topic may be discussed here.[/QUOTE]

---

### Post by dragonfly41 on 2012-09-13
If drupal is your choice of CMS you can try [www.drupalgardens.com](www.drupalgardens.com) to prototype a web site.

---

### Post by Bucky Ball on 2012-09-13
Just wondering why you want to do it online then download it to your local machine ... if you're hosting it locally (or if you're not) Kompozer is quite good. I use that with the Gimp, Libreoffice for text and whatever other apps I need then paste it altogether and upload to webhost. I can see what it's going to look like without endless uploading and downloading. Just upload the finished one (or close). With Kompozer you can wysiwyg or html or both at the same time. Should be in the repos.

---

### Post by suomalainen on 2012-09-13
I just installed Kompozer and already a tiny problem.

I can only publish directly to a hosting service I already have. I cannot publish to desktop the files.

Why not?

---

### Post by Lars Noodén on 2012-09-13
Click on the icon 'Browse' at the top of the window, that should open up your page in the default web browser.  Is that what you meant?

---

### Post by suomalainen on 2012-09-13
NO.

Why do I have to publish directly to the web hosting server first?

I'd rather save my work by publishing it to my desktop and when the site is completed uploading it all in one go.

---

### Post by Bucky Ball on 2012-09-13
Yep, save the file to somewhere on your local machine as a html file then open it in the browser of your choice. 

From memory you need to give the details of where you want to publish to but not sure if you need to publish until you're ready. Anyhow, just publish a blank index.html and there you go, then start working on it locally, saving and viewing, and when you're ready you only need to hit publish and the blank index.html will be replaced with the one you've worked on.

When you said you were hosting it yourself I wasn't sure if the server was local or not. You are uploading to a web host WAN side?

PS: You don't publish to your desktop. You can save a file and view it on your local machine in a browser (just like saving a web page as a html then opening it without being online) but the concept of 'publishing' a web page is just that; you are publishing it like you would a newspaper, a book or sheet music ... to the outside world and into the public domain.

One other thing is ... how many people have the web address of your website? Do you think anyone is going to see it unless you tell them? It is not easy to get a website near the top of any search engine so wouldn't be too worried. ;)

---

### Post by Lars Noodén on 2012-09-13
As far as publishing all in one go, you should be able to use your file manager for that.  Press ctrl-L or choose the menu File->Connect to Server

The first time a new page is saved, it asks where.  The files I make in Kompozer are saved where I tell it to save, including on the desktop if so designated.  So I'm having trouble duplicating your problem.  I have to admit though that I generally code the XHTML by hand or with the help of Emacs rather than Kompozer.

---

### Post by suomalainen on 2012-09-13
I have web hosting service with an ISP already.

In the past I've used Microsoft Publisher to make web pages(s) and the process was real easy. I could even publish the website to my desktop then use Filezilla to FTP all the files to the web hosting server once I was ready.

As it stands now I must publish directly to the hosting server each time. This means there is real life possibility to have a web site for otheres to see which is half done. Not too nice in my opinion.

Also, I made a test web page and saved it to my desktop but the images I used in the web page I created were not placed into any specific folder.

I don't know for sure, but it appears that if I use and images or documents I link to that I need to first create a folder they are placed into so Komposer know where everything is prior to upload.

Seems rather problematic...

---

### Post by Bucky Ball on 2012-09-13
> **suomalainen said:**
> 
I don't know for sure, but it appears that if I use and images or documents I link to that I need to first create a folder they are placed into so Komposer know where everything is prior to upload.

Correct, and you would then need to store those images and documents in folders online on the web host server and change the code of the online pages accordingly to link to those files else the links would relate to the image/document files you have stored locally. As I mentioned before; who will see your half finished pages unless you tell them the address? They certainly won't come up in a search. I have fully published sites that don't come up in searches two years later. 

You need to make the search engines aware of the new website, there's generally a procedure depending on the engine, before you really get any propagation. In the unlikely event someone does stumble across it, one idea is to publish an index.html saying 'Hi, this is my page' then work on sub-pages which no-one would know existed. E.g. [http://www.mypage.net/behind_the_scenes](http://www.mypage.net/behind_the_scenes). (That is not a real page). Works for me.

---

