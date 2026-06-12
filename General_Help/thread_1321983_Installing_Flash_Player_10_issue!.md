---
title: "Installing Flash Player 10 issue!"
date: 2009-11-10
forum: General Help
---

### Post by KennyGJE on 2009-11-10
I get a error everytime I try! Here's a screenshot!

[IMG]http://i36.tinypic.com/jl5qid.png[/IMG]

---

### Post by KennyGJE on 2009-11-10
Also this happends when I try another way I saw on YouTube:

[IMG]http://i35.tinypic.com/2iql66u.png[/IMG]

---

### Post by trpnblies7 on 2009-11-10
Have you tried installing the plugin from Synaptic instead of a .deb file? The current version is in the repositories, I believe.

---

### Post by KennyGJE on 2009-11-10
> **trpnblies7 said:**
> Have you tried installing the plugin from Synaptic instead of a .deb file? The current version is in the repositories, I believe.
No I havent, can you please leave a link?

---

### Post by JugglinPhil on 2009-11-10
> **KennyGJE said:**
> No I havent, can you please leave a link?
It is not a link, you go to System => Administration => Synaptic Package Manager, enter your password and type 'flashplugin' in the search bar. Install whatever it comes up with I'd say.
The first error you get means there's a package missing, so go to synaptic as described above and search for whatever you nedd ('libnspr4-dev' in your case), check it and choose install, then click apply.

---

### Post by KennyGJE on 2009-11-10
> **JugglinPhil said:**
> It is not a link, you go to System => Administration => Synaptic Package Manager, enter your password and type 'flashplugin' in the search bar. Install whatever it comes up with I'd say.
Do you mean this way? Leaves me the same problem over and over again :(
[IMG]http://i35.tinypic.com/5o6vjr.png[/IMG]

---

### Post by KennyGJE on 2009-11-10
> **JugglinPhil said:**
> It is not a link, you go to System => Administration => Synaptic Package Manager, enter your password and type 'flashplugin' in the search bar. Install whatever it comes up with I'd say.
The first error you get means there's a package missing, so go to synaptic as described above and search for whatever you nedd ('libnspr4-dev' in your case), check it and choose install, then click apply.
Wops, it seems I misunderstood, here's what happened, when i searched flashplugin thing, I didnt find anything, then i searched for the missing file and I found this, but it seems to allready be installed or something:
[IMG]http://i37.tinypic.com/xoodp4.png[/IMG]

---

### Post by JugglinPhil on 2009-11-10
What architecture do you use, 32bit or 64bit? Try downloading whichever one you need from the official site ([http://get.adobe.com/de/flashplayer/](http://get.adobe.com/de/flashplayer/)) and try install them.

Also would you mind loading up your screenshots as thumbnails? Having them right in your post makes the thread pretty messy..

---

### Post by KennyGJE on 2009-11-10
> **JugglinPhil said:**
> What architecture do you use, 32bit or 64bit? Try downloading whichever one you need from the official site ([http://get.adobe.com/de/flashplayer/](http://get.adobe.com/de/flashplayer/)) and try install them.

Also would you mind loading up your screenshots as thumbnails? Having them right in your post makes the thread pretty messy..
Im not sure, I think I got 32bit, where can I chuck that? Sorry for the scr sht:P Just saves me alot of writing..

---

### Post by JugglinPhil on 2009-11-10
Well what cd did you download to install it, 32 or 64? Go to System => Administration => Software Sources and see what it says about the cd at the bottom. There should be either something about 32 or 64 in the name..
You can still post your screenies, just use the 'attach file' option instead of putting them right in your text.

---

### Post by JugglinPhil on 2009-11-10
Nice you marked it solved, did you get it to work?

---

