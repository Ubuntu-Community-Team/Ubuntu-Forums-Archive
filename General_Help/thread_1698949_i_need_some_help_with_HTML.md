---
title: "i need some help with HTML"
date: 2011-03-03
forum: General Help
---

### Post by cain071546 on 2011-03-03
I have been trying to teach myself some html
but most of the tutorials are so dry i cant concentrate long enough to read them

I normally do minor tech support for friends and fam
it was suggested i make a webpage but i dont know html

I think i need to start over cuz i used a HTML generator 
and i dont think its as organized as it could be

all i really need now are some images maybe a banner 
ive been lookin at how to add images to my html
but im having issues getting it positioned 

and most of my text is on the left of the page

dont laugh i like to consider my self quite computer literate 
but im a horrible noobin when it comes to HTML

im not looking to build a site, just a simple webpage
i got some help here earlier but it was mostly links to more Tuts

anything helps thanx

[http://mrgreenpcsupport.zxq.net/](http://mrgreenpcsupport.zxq.net/)

please dont laugh

---

### Post by Smart Viking on 2011-03-03
html is very easy actually when all you are aiming for is just a simple site.

You insert an image with the "img" tag.
If you have your html document in /var/www/lala.html, and your image in /var/www/images/image.jpg, then you would use <img src="images/image.jpg"> and it would show up in your page. html is something you, or I at least find like something that you learn best by playing and failing, the fail rate can be very high but thats ok because you just search around and eventually you'll find what you need, and then you might remember until next time or at least find it faster next time.

---

### Post by Verbeck on 2011-03-03
you can use the 'div align' attribute to possition the image
eg;
<div align="center"> <img src="http://ubuntuforums.org/images/misc/ubuntulogo.png"></div>

---

### Post by jwcalla on 2011-03-03
Generally many HTML generators are evil.  Though the old-school Netscape Composer used to work reasonably well.

Your thing is spaced wrong because it's using non-breaking spaces to provide the justification.  Ideally you'd just want your text and then you'd let the browser do the formatting.  You can set the justification alignment with an HTML tag or attribute (I forget which... like < center > or something).

Though what you really really really really want to do is install a content management system like WordPress and install a really slick, free theme.  It's pretty easy to setup and customize and it takes most of the HTML and CSS guesswork out of the equation.

---

### Post by cain071546 on 2011-03-03
i was hoping that someone would look at what i have all ready
and then make some suggestions 
yes i have the image i want in images/
i know how to add it to the tag
but im having probs spacing/organizing it plus all my text is on the left side

---

### Post by cain071546 on 2011-03-03
thanx jwcalla

do they have wordpress for ubuntu?
ill look into it 
thanx

---

### Post by jwcalla on 2011-03-03
> **cain071546 said:**
> thanx jwcalla

do they have wordpress for ubuntu?
ill look into it 
thanx

Wordpress certainly does run on linux (it's mostly PHP)... you have to install it on the web server.  Most popular domain hosts have a setup guide for it.  It requires PHP and a MySQL database to manage the content.

---

### Post by cain071546 on 2011-03-03
ok im using Zymic as my host ill check it out

---

### Post by mastablasta on 2011-03-03
good tutorials: [http://www.w3schools.com/](http://www.w3schools.com/)
 
you can also use google's blogger for the same/similar effect as wordpress. maybe it is a bit easier since you don't need special host. 
 
Another very simple one to set up a portal is Joomla. though it's again ment more for dynamic pages i made a simple static page with it.

---

