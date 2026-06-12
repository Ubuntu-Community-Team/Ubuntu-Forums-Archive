---
title: "Web page design tools"
date: 2006-04-06
forum: General Help
---

### Post by the_tiger on 2006-04-06
I am about to embark on designing my first real webpage. I have only ever used a text editor for simple html pages before and was wondering what WYSIWYG editors in Ubuntu people recommended. Also what other tools do people find useful/invaluable for creating designing their webpages. I am interested in programs to make any aspect of design to coding easier.

Also is this the right part of the forum for such a post?

---

### Post by jenred on 2006-04-06
I really like BlueFish Editor - has everything you need and is fairly simple to use, and I believe the functionality is equal to or better then DreamWeaver -- at least it's easier to use imho.  Gimp for graphics and again as good if not better then Adobe PS.

Go to add application and type in Bluefish to install.  Gimp is included in the default install.

Jen

---

### Post by dragonfyre13 on 2006-04-06
Grab NVU from the repos. This is one of the best editors for WYSIWYG in both linux and windows. It is also based on Mozilla Composer.

Otherwise, you could try something else, like bluefish, or such.

---

### Post by K.Mandla on 2006-04-06
Nvu seems to be the strongest WYSIWYG editor, unless there's another one that has cropped up recently. You can install it with the Add/Remove menu under Applications, or through the Synaptic Package Manager, or by typing this into a terminal ...

```
sudo apt-get install nvu
```
Personally I think it's a bit lean for my purposes. When I want a WYSIWYG editor, I want all the bells and whistles, and Nvu is a bit lacking. It will definitely get the job done, though.

For page coding, I have a tendency to flip-flop between Bluefish and the default gedit. I hear Scite is popular among straight coders too. I can only with PSPad was available for Linux. ...

---

### Post by the_tiger on 2006-04-06
Do NVU and bluefish produce code that would pass the w3c markup evaluation test?

---

### Post by bistro on 2006-04-06
Hi

I've just been looking recently, Bluefish and Quanta seem very usable. I haven't yet found a text editor with database connectivity (I'm used to MM Homesite) which I would value just to avoid wasting time with mis-spelt table names etc.

cssed is a neat little style sheet editor.

---

### Post by K.Mandla on 2006-04-06
Bluefish will, but in my experience that's because it's more of a code editor, which means you can keep tight to the W3C lines. Nvu is more of a WYSIWYG, although you can jump to a code view and edit manually, so it's great for drawing tables and such.

Personally, I [code like a girl]("http://headrush.typepad.com/creating_passionate_users/2006/03/code_like_a_gir.html"), and I find that Nvu's output is a bit sloppy for my taste. And when I found out Bluefish will interface directly with the HTML Tidy tool, it was love at first sight. ... =D>

---

### Post by Ginger The Cat on 2006-04-06
I use Quanta and it's superb. I especially like the Project facilities where you can group a load of files as a project. If I am working on more than one job at the same time I can easily pull up all the right files.

This description is taken from the blurb in Synaptic...

Quanta Plus is a web development environment for working with HTML
and associated languages. It strives to be neutral and transparent
to all markup languages, while supporting popular web-based scripting
languages, CSS and other emerging W3C recommendations.

Quanta Plus supports many external components, debuggers and other tools
for web development, several of which are shipped with the KDE web
development module.

Quanta Plus is not in any way affiliated with any commercial versions
of Quanta. The primary coders from the original team left the GPL'd
version to produce a commercial product.

This package is part of KDE, as a component of the KDE web development module.
See the 'kde' and 'kdewebdev' packages for more information.

Homepage: [http://quanta.sourceforge.net](http://quanta.sourceforge.net)

---

### Post by K.Mandla on 2006-04-06
[QUOTE=bistro]cssed is a neat little style sheet editor.[/QUOTE]
Hey, I hadn't heard of that one. I like it. I'm all about CSS right now. Thanks.

---

### Post by stoeptegel on 2006-04-06
I installed kdewebdev myself, a package with Quanta as an editor and some other tools. 
I think GUI stylish, bluefish belongs more to gnome than quanta though, but they are both great programmes.

WYSIWYG is not supported AFIAK in these two, but there's a previewer and quanta also has tidy support.

---

### Post by dragonfyre13 on 2006-04-13
[QUOTE=the_tiger]Do NVU and bluefish produce code that would pass the w3c markup evaluation test?[/QUOTE]


NVU specifically does. It even has a link where you can check with the official w3c  set, and make absolutely sure.

---

### Post by sprinkles on 2006-04-13
I just tried Nvu - it's AWFUL! I've been using Bluefish which I like, but it's not WYSIWYG.

This is another area Linux is lacking, as there are no decent graphic packages (GIMP is shockingly bad), and no WYSIWYG editors.

---

### Post by aysiu on 2006-04-13
[QUOTE=sprinkles]I just tried Nvu - it's AWFUL! I've been using Bluefish which I like, but it's not WYSIWYG.

This is another area Linux is lacking, as there are no decent graphic packages (GIMP is shockingly bad),[/quote] How is GIMP "shockingly bad"? > and no WYSIWYG editors. Just because you don't like Nvu doesn't mean it's non-existent.

Quanta has been mentioned several times in this thread. Have you tried that?

I've found Quanta to be pretty darn good for WYSIWYG. That said, I don't think people should use WYSIWYG for web design--too much gunky HTML code.

---

### Post by DirtDawg on 2006-04-13
I'm not the hugest Nvu fan myself. The version I tried (on Hoary) reformatted code, even if I wrote it in a different editor, then opened it with Nvu. The reformatted code was awful. Difficult to read with line breaks and tabs where they just didn't make sense. I may have had a screwy copy sinse I've never heard anyone else complain about this feature.  

Anyways, I'm trying to learn CSS now (see: Freakin HARD!) and I've been using [Cream]("http://cream.sourceforge.net/") text editor. I was using Scite before, but Cream totally rulez! :KS 

Unfortunately, as far as Linux is concerned, my experience has been that WYSIWYGs are a little hard to come by.

---

