---
title: "evince fails to open pdf external links in non-gnome system"
date: 2010-07-17
forum: General Help
---

### Post by a.sarkar on 2010-07-17
Dear All,

Evince in non-gnome systems is unable to open external link.
The error msg it shows is

```
Unable to open external link
The specified location is not supported.
```

I have already googled it, however it only says it is a bug, without any solution available.

Evince in gnome systems however work just fine.
Is there any way evince can use sensible-browser to open 
external links?

P.S. Pls don't tell me to use Acrobat reader :D

---

### Post by a.sarkar on 2010-07-17
Forgot to mention, that epdfview has an open to choose the 
web-browser. Is something like this possible for evince?

---

### Post by a.sarkar on 2010-08-02
Finally got external links to work in evince in non-gnome systems. Install the following packages

```
sudo apt-get install libgnomeui-0 gconf-editor
```

This will install some other gnome related packages 
as well. The installation size of all these packages is about 28MB. To change the default browser run the command
"gconf-editor" in a terminal (without the quotes) and then go to

```
/desktop/gnome/url-handlers/http
```

There edit the command entry to the browser of your choice.
Example: Change
```
firefox %s 
```
to 
```

chromium-browser %s

```
Do the same for 
```
/desktop/gnome/url-handlers/https
```

Done. 

I wish it was a little bit easier than this. 
I mean just to get the external link of evince working one has 
to install 28MB of additional stuff???

But, I am happy that at least it's working now.

---

