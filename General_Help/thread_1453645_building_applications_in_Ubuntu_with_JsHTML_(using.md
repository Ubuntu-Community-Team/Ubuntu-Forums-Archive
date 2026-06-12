---
title: "building applications in Ubuntu with Js/HTML (using Webkit?)"
date: 2010-04-13
forum: General Help
---

### Post by willemmulder on 2010-04-13
Hi all,

I'm using Ubuntu for some 2,5 years now, and while I have developed several applications using Delphi on Windows and a lot of web applications, I have not gotten around creating applications on Ubuntu... (except for some testing stuff with Java)

1. How are Ubuntu applications most often created? Requirement: they should be working cross-platform. I'm familiar with Java and Pascal on Windows. I've tried Java on Ubuntu, but it seemed to generate not-so-beautiful-looking-apps and of course requires the JVM, which I would rather avoid.

2. Since my current profession involves mainly programming in HTML/CSS and Javascript (for about 8 years), I wondered whether there was an easy way to have a wrapper around e.g. Webkit that can render a web-application (either just from the web, but preferably serving the pages itself like a simple server)

Hope you can help me creating super apps for Ubuntu! :-)

---

### Post by willemmulder on 2010-04-13
As for the first question, I did some more research and have decided to go with Python, developing with Quickly, in Glade and Gedit...

As for the second question, does anybody know how I can integrate Webkit in Glade?

---

### Post by willemmulder on 2010-04-13
All right, so I got a browser window working! 

All I needed to do was this:

browser = webkit.WebView()
self.builder.get_object("vbox1").pack_start(browser, expand=True, fill=True, padding=0)
browser.show()
browser.open("http://www.fabricasapiens.nl")

in the after init function.
(and of course the 'import webkit' at the very top)

Thus, hereby my two questions are mainly solved... Thanks for listening anyways :) Hope this helps some...

---

