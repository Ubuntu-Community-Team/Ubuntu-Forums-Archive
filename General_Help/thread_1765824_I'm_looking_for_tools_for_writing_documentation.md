---
title: "I'm looking for tools for writing documentation"
date: 2011-05-23
forum: General Help
---

### Post by metalf8801 on 2011-05-23
I'm looking for a text editor, word processor, or another kind of program that makes it really easy to make it look like some of the text is inside of a terminal. So that it is very obvious what text is a command and what text is a description. 

Also a template that does this would work to. 

Any suggestions would be great!

Thank you
Dan

PS In case it matters I'm setting up a server and I want to document each step that I take.

---

### Post by HermanAB on 2011-05-23
Howdy,

Play with the fonts.

The usual way is to select a Courier Monospace font for terminal text and Times New Roman or a Freedom Serif Font for regular text.

---

### Post by metalf8801 on 2011-05-23
> **HermanAB said:**
> Howdy,

Play with the fonts.

The usual way is to select a Courier Monospace font for terminal text and Times New Roman or a Freedom Serif Font for regular text.

Yeah thats what I've been doing. I was just hopping there was a better way. I really like how the online Ubuntu server documentation looks [https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html) 
While it doesn't exactly look like a terminal it still obvious whats a command and what isn't. Does anyone know if I can do that with a Latex editor like LyX or do I need to use HTML?

---

### Post by dragonfly41 on 2011-05-23
If you view source of that page .. you'll see this for example

```
<span class="command"><strong>sudo ufw enable</strong></span>
```so use HTML style sheets .. e.g. class="command"

[EDIT]

perhaps look at Scribus.

---

### Post by metalf8801 on 2011-05-23
> **dragonfly41 said:**
> If you view source of that page .. you'll see this for example

```
<span class="command"><strong>sudo ufw enable</strong></span>
```

so use HTML style sheets .. e.g. class="command"

Ok well unless anyone has an better or even just different idea that will have to work 

Thank you to everyone who replied 
Dan

---

### Post by dragonfly41 on 2011-05-23
Well you can also apply styles (terminal type style) in OpenOffice word processor .. or Scribus (it's in Synaptic Package Manager).   Then publish as PDF.

But if you're building a server you may as well use css.

---

