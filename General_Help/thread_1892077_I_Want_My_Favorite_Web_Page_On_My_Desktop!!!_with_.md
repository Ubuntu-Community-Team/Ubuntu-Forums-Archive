---
title: "I Want My Favorite Web Page On My Desktop!!! with transparent bg!!!"
date: 2011-12-07
forum: General Help
---

### Post by ohnonot on 2011-12-07
...I've been fiddling with conky for a while and then i got the idea - 

why go through the weary process of filtering a web page (which is a document written in html basically) for information which i then have to tell conky exactly how to format it onto my desktop -

- if instead i could use the formatting provided by html and display the content (Text formatting, icons...) on my desktop straight away. obviously that would need some refining, too, but it would be a starting point.

come on, there must be something out there to achieve this!
afaik conky doesn't understand html.
it uses lua for certain special things, but that seems to be just another language, or is that where i have to look? i am happy with some scripting but i'm not really a programmer.

i've posted on one of the conky weather threads but it drowned in an ongoing discussion, anyway this is not specific to conky or weather scripts, so i just start a new thread...
:grin:
any ideas?

---

### Post by tartalo on 2011-12-07
If yo want this badly you could move to KDE. There is a widget called Web slice that shows a web page or a slice of it inside a resizeable box in your desktop.

[http://vizzzion.org/blog/2011/01/slicing-up-the-web/](http://vizzzion.org/blog/2011/01/slicing-up-the-web/)

---

### Post by BC59 on 2011-12-07
I think Google Chrome OS is doing something like that.

---

### Post by aeiah on 2011-12-07
> **BC59 said:**
> I think Google Chrome OS is doing something like that.

pretty sure chrome os just has chrome in kiosk mode as its desktop environment.


OP - are you just wanting information as it is presented, or are you wanting dynamic content (animations), clickable links etc?

the easiest way would be to take a screenshot of the page and use that as your desktop, or combine it with another image and use that - but you wouldnt be able to click on the links or anything, obviously. the snapshot taking / merging with existing desktop image can be automated.

---

### Post by Habitual on 2011-12-07
I have longed for years for a companion to my embedded terminal.
I just wish it was an embedded Firefox.

I could NOT get conky to put that resource *on* my desktop.

Bummer.

---

### Post by Bobhuber on 2011-12-07
Cairo-Dock Weblets.

---

### Post by hwttdz on 2011-12-07
Couldn't you also just launch a firefox and tell the window manager to skip taskbar, keep it on the bottom, not minimize, set opacity...  I mean you use terminal to make the embedded terminal, why not use firefox to make the embedded firefox.

---

### Post by ohnonot on 2011-12-07
so many answers! thanks! i'll just go through them 1 by 1...
> **tartalo said:**
> If yo want this badly you could move to KDE. There is a widget called Web slice that shows a web page or a slice of it inside a resizeable box in your desktop.

[http://vizzzion.org/blog/2011/01/slicing-up-the-web/](http://vizzzion.org/blog/2011/01/slicing-up-the-web/)
this looks good esp it recognizes the necessity of using only part of the webpage.
but no, i don't want it desperately enough to change to kde.
> **Habitual said:**
> I have longed for years for a companion to my embedded terminal.
I just wish it was an embedded Firefox.

I could NOT get conky to put that resource *on* my desktop.

Bummer.
habitual, i'm not sure i understand, are you refering to something like this:
> **hwttdz said:**
> Couldn't you also just launch a firefox and tell the window manager to skip taskbar, keep it on the bottom, not minimize, set opacity...  I mean you use terminal to make the embedded terminal, why not use firefox to make the embedded firefox.
- this sounds like a good solution, i have some experience with fluxbox, but i can't find it in metacity. is it a big hassle to keep gnome and replace metacity?
also i think some knowledge of firefox - more than i have - to remove menus and everything.
(what exactly is an embedded terminal?)
> **Bobhuber said:**
> Cairo-Dock Weblets.
i have installed this and hooray, i managed to display a webpage straight on the desktop. just like a browser basically. then i downloaded a webpage to a html file and told the weblet to display that - works too! - then i started to delete parts from that file until only the core (what i want) is visible. see screenshot. looks horrible but it's a start. 
though i'm not sure i need the cairo dock itself...

---

### Post by ohnonot on 2011-12-14
cairo-dock eats too much of my resources, and the weblets make it even worse
:(
anyhow i don't need the interaction - i don't want a transparent web browser but just something that is capable of parsing html (it's easy enough to download the pages with curl) and throw it on my desktop.
:confused:

---

### Post by ohnonot on 2011-12-15
html2text

---

