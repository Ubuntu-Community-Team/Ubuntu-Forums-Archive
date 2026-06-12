---
title: "Spell checker thinks I'm from other side of pond"
date: 2009-09-21
forum: General Help
---

### Post by FunkyRes on 2009-09-21
Shiretoko browser.
Ubuntu Jaunty.

mpeters@mpeters-ubuntu:~/bin$ echo $LANG
en_US.UTF-8

Language Preferences are also sent to English/United States.

However, if I type color (amongst other things) it suggests I spelled it wrong, wanting me to use colour.

Surely I'm not the first, but googling this issue so far has only found be gedit bugs.

How do I fix this?

---

### Post by hawthornso23 on 2009-09-21
Where are you typing color - what application.

---

### Post by sisco311 on 2009-09-21
Right Click -> Languages -> English / United States 

for some reasons English / United Kingdom is the default :shock:

:-\"

---

### Post by t0p on 2009-09-21
> **sisco311 said:**
> Right Click -> Languages -> English / United States 

for some reasons English / United Kingdom is the default :shock:

:-\"

Right-click on what?  I'm afraid your instructions are not clear.

The OP said he wants to set the language in Shiretoko, ie Firefox-3.5.  The only language settings I can find in Firefox-3.5 is under **Edit > Preferences > Content > Languages** but I think the OP said he's already set that to English United States.  So where is this other language setting please?  (I'd also like to know because I want to do the reverse to the OP - ie change setting *to* English UK.)

---

### Post by soggydoggy on 2009-09-21
How odd, usually we in the UK have the opposite problem where "colour" is corrected to "color" by default!
Does Shiretoko have independant language settings?
Also, check what language your keyboard is set to, this is seperate from the region settings.

---

### Post by sisco311 on 2009-09-21
Sorry, I wasn't clear enough.

The OP wants to set the language of the spell checker.

> **t0p said:**
> Right-click on what?

On any input text field (i.e. the forum's text editor).

[img]http://www.upload3r.com/serve/210909/1253536717.png[/img]

---

### Post by t0p on 2009-09-21
> **sisco311 said:**
> Sorry, I wasn't clear enough.

The OP wants to set the language of the spell checker.



On any input text field (i.e. the forum's text editor)

Thank you.

---

### Post by t0p on 2009-09-21
> **sisco311 said:**
> Sorry, I wasn't clear enough.

The OP wants to set the language of the spell checker.



On any input text field (i.e. the forum's text editor)

Thank you.  

Strangely, the only dictionary installed in my Firefox-3.5 was the US English one.  I had to install the British English Dictionary.  But you say that the British English Dictionary is the default one in US downloads of Firefox-3.5?  Or is that only the ones that are in the repos? (I got mine from [getfirefox.com]("http://getfirefox.com"), which forwards to a UK mirror when you browse to that url from the UK)

---

### Post by sisco311 on 2009-09-21
> **t0p said:**
> Thank you.  

Strangely, the only dictionary installed in my Firefox-3.5 was the US English one.  I had to install the British English Dictionary.  But you say that the British English Dictionary is the default one in US downloads of Firefox-3.5?  Or is that only the ones that are in the repos? (I got mine from [getfirefox.com]("http://getfirefox.com"), which forwards to a UK mirror when you browse to that url from the UK)

I'm *testing* Karmik. I got mine from the ppa repos (daily build):
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa")

```
firefox --version
Mozilla Firefox 3.5.4pre, Copyright (c) 1998 - 2009 mozilla.org

```

---

### Post by FunkyRes on 2009-09-21
Thanks.

It's set English_AU by default.

Which is weird, because in browser preferences, it is set to English/United States.

I set it to en_US. Wonder why it doesn't inherit from $LANG ??

---

