---
title: "Site like www.appnr.com"
date: 2010-07-16
forum: General Help
---

### Post by haitman on 2010-07-16
I am from Iran 
My question about how [www.appnr.com](www.appnr.com) Site is a site I plan to design this site I like the ability to install software on Ubuntu have the

---

### Post by WorMzy on 2010-07-16
This looks like an advert. Do you have a question regarding Ubuntu, or do you need help with XHTML/PHP/Javascript/etc?

If you have a Ubuntu question, make sure to ask it in a clear way so we don't misunderstand you.

If you need website building help, check out [w3schools]("http://w3schools.com/").

---

### Post by haitman on 2010-07-17
I'm going to build a site like appnr.com
But I do not know how I put the software that the user click the button to install programs on your system to install

---

### Post by Penguin Guy on 2010-07-17
[COLOR="Green"]Applications -> Ubuntu Software Center[/COLOR]

---

### Post by WorMzy on 2010-07-17
Are you looking for "What You See Is What You Get" (WYSIWYG) website development software? For example something, like the Windows-based software Dreamweaver?

If that's what you meant, then there's a few different ones available to you. Amaya, Kompozer, and Quanta Plus are probably the three most common; so have a look in the Software Centre or Synaptic for these and try them all out.

I personally use gedit, which is basically just a text editor. You make the best websites by getting down and dirty with the code. ;)

Gedit is installed by default, you won't need to install it.

---

### Post by lsk3993 on 2010-07-17
If I understand correctly, the question is about making a button on a website that allows users to install programs. NOT making the website itself...
This is a screenshot of appnr so you can see what the OP is asking. See the little green install buttons? I think that's what he wants on his site.

[IMG]http://www.ubuntugeek.com/images/appnr.png[/IMG]

---

### Post by WorMzy on 2010-07-17
The website doesn't load for me, so I didn't realise it was that kind of site.

Still, it's easy to get that sort of functionality, just create an anchor tag with the href as an "apt://" address. Synaptic will take care of the rest.

e.g.
```
<a href="apt://gedit">Install gedit</a>
```
[Install gedit]("apt://gedit")

---

