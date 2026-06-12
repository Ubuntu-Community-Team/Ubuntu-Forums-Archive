---
title: "Building a website"
date: 2010-09-08
forum: General Help
---

### Post by Moonsavior on 2010-09-08
Hi,

My specs:
Ubuntu 
Release 9.10 (Karmic)
Kernel Linux 2.6.31-14-generic
GNOME 2.28.1

Memory 2.8 GiB
Available Disk Space 200 GiB

   I'm trying to build a website and am currently at the point of learning how to build a web page using HTML tags. I tried to substitute Open Office Word Processor for notepad to hand type the HTML tags and test them on the Firefox browser but the codes are not being read at all by Firefox to make the text appear as wanted. Can someone please help me figure this out? What am I missing?

Thanks

---

### Post by Naitsirhc Hsem on 2010-09-08
use gedit. open office might change the formatting.
Applications > Accesories > Text Editor
create new page.html

---

### Post by JohnHeikkila on 2010-09-08
Do the HTML manually. Quanta Plus is good if you want to make the page purely.

---

### Post by utnubuuser on 2010-09-08
Screem is also a good html editor, but like Naitsirc Hsem said, gedit does a wonderful job of editing html.

For your information, HTMl is very basic, and not worth spending a lot of time on,  CSS and PHP is what you're after for "web-design".

Your basic html page looks like this: <html><head><title></title></head><body><div><p>this is the content of the page which should be styled with CSS</p></div></body></html>

Save this file as whatever.html and you can open it in a web-browser.  
Styling things through html is almost totally depracated.  So long as you know the above, and that the rule for tags is "first in - last out, you should move on to CSS instead.

---

### Post by deserthowler on 2010-09-08
> **Naitsirhc Hsem said:**
> use gedit. open office might change the formatting.


I agree, other than I just happen to like Emacs.
Check your pages to see if they are compliant at the w3c site.

Earl

---

### Post by Moonsavior on 2010-09-08
> **utnubuuser said:**
> Screem is also a good html editor, but like Naitsirc Hsem said, gedit does a wonderful job of editing html.

For your information, HTMl is very basic, and not worth spending a lot of time on,  CSS and PHP is what you're after for "web-design".

Your basic html page looks like this: <html><head><title></title></head><body><div><p>this is the content of the page which should be styled with CSS</p></div></body></html>

Save this file as whatever.html and you can open it in a web-browser.  
Styling things through html is almost totally depracated.  So long as you know the above, and that the rule for tags is "first in - last out, you should move on to CSS instead.

Thanks for your reply and to all others...I started using Quanta Plus as suggested. About CSS, I'm familiar with the basic HTML tags, when using CSS is OK to use Quanta Plus and its CSS feature (which appears to be semi-manual, like button click instead of code input) or should I use a complete manual editor for CSS?

---

### Post by keithpeter on 2010-09-08
> **Moonsavior said:**
> About CSS, I'm familiar with the basic HTML tags, when using CSS is OK to use Quanta Plus and its CSS feature (which appears to be semi-manual, like button click instead of code input) or should I use a complete manual editor for CSS?

I suppose that depends on you

a) You want to get pages made, a job done - use Quanta's tools, the code will always be in the css file for later on...

b) You want to learn the basic principles that underlie html/css/javascript - then you work with CSS code

I learned what little I know by 'reverse engineering' Web sites I liked. I copied down the files, and went through the code until I understood it. It was easier a decade ago :-)

[http://diveintohtml5.org/](http://diveintohtml5.org/)

A free web book on HTML5 and the latest things...

---

