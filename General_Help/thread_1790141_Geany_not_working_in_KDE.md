---
title: "Geany not working in KDE?"
date: 2011-06-24
forum: General Help
---

### Post by GrantStoner on 2011-06-24
I just switched to Kubuntu, and although I'm loving it, I'm missing some of my favorite tools - most of which I've found alternatives for. I've read that Geany IDE should run fine on KDE, but when I install and try to launch, it just hangs. The icon bounces around by my cursor like it's loading, and window switcher in the task bar shows it trying to load. And then after about 10sec it just stops - and my screen stares back at me. Here's the output when I try to run it via Konsole:```
grant@L1NUX:~$ geany
Segmentation fault
grant@L1NUX:~$
```
If for any reason Geany is broken with KDE now, does anyone suggest a better general purpose IDE? All the ones I've found are specific (or at least geared towards) one programming language.

---

### Post by iclestu on 2011-06-24
> **GrantStoner said:**
> I just switched to Kubuntu, and although I'm loving it, I'm missing some of my favorite tools - most of which I've found alternatives for. I've read that Geany IDE should run fine on KDE, but when I install and try to launch, it just hangs. The icon bounces around by my cursor like it's loading, and window switcher in the task bar shows it trying to load. And then after about 10sec it just stops - and my screen stares back at me. Here's the output when I try to run it via Konsole:```
grant@L1NUX:~$ geany
Segmentation fault
grant@L1NUX:~$
```If for any reason Geany is broken with KDE now, does anyone suggest a better general purpose IDE? All the ones I've found are specific (or at least geared towards) one programming language.

Kdevelop?

---

### Post by iclestu on 2011-06-24
although surely you can still use geany with KDE if thats you preference. I dont know enough to know what to suggest to make it work but surely it is compatible?

---

### Post by GrantStoner on 2011-06-24
It's geared towards C/C++. I did try it though last night. And it was decent. But it looks like it just uses Kate with more additions - and Kate is just a super-text-editor in my opinion. Not to mention, it doesn't auto-indent or tab correctly. That's what irritated me the most about it - it just adds a few spaces and your code doesn't come out looking as clean.

---

### Post by GrantStoner on 2011-06-24
> **iclestu said:**
> although surely you can still use geany with KDE if thats you preference. I dont know enough to know what to suggest to make it work but surely it is compatible?
That's what I thought. I looked around and a few others had the same error, but it had something to do with the Oxygen theme for gtk apps. I changed it to Raleigh - and although now every gtk app is pure ugly, Geany still won't launch.

---

### Post by iclestu on 2011-06-24
> **GrantStoner said:**
> It's geared towards C/C++. I did try it though last night. And it was decent. But it looks like it just uses Kate with more additions - and Kate is just a super-text-editor in my opinion. Not to mention, it doesn't auto-indent or tab correctly. That's what irritated me the most about it - it just adds a few spaces and your code doesn't come out looking as clean.

I think this is a settings issue. Kate can do pretty much whatever you tell it to.

I dont code a lot but i do use Kile extensively (which, as u probably know, is based on Kate but for LaTeX) and it took me a fair bit to get it set up the way I wanted with autoindents autocompletes etc. The config settings are a bit of aminefield but worth persevering with (i guess complex settings is just the cost of high configurability). 

It may be worth persevering and perhaps check out the documentation?

---

### Post by GrantStoner on 2011-06-24
I will probably end up giving KDevelop another shot. I was just hoping for a more general-purpose IDE. Maybe Emacs is what I will default to in the event I can't stand KDevelop or find a suitable answer for Geany.

Thanks for the help.

EDIT: Oh yeah! I just read an article describing the death of general-purpose IDEs. Thought it was humorous - not reality. Oh well. :/

---

### Post by iclestu on 2011-06-24
> **GrantStoner said:**
> I will probably end up giving KDevelop another shot. I was just hoping for a more general-purpose IDE. Maybe Emacs is what I will default to in the event I can't stand KDevelop or find a suitable answer for Geany.

Thanks for the help.

EDIT: Oh yeah! I just read an article describing the death of general-purpose IDEs. Thought it was humorous - not reality. Oh well. :/


You know you can get plugins for all sorts of other languages for kdevelop too?? Might suit your needs? 

My pleasure entrirely, although im not at all sure I have been of help! Sounds like you have a good bit more experience of these things than i do. Hope you get a solution that suits you...

---

### Post by GrantStoner on 2011-06-24
Yeah, Geany has plugins too. But it comes with a lot of defaults that I find myself having to download as extras on other IDEs. I just found out about Code::Blocks too - may give that a try as well.

---

### Post by Erik1984 on 2011-07-11
I want Geany to work as well, exactly the same problem. I found an ugly (literally) workaround here [http://lists.suse.com/opensuse-bugs/2011-05/msg00542.html](http://lists.suse.com/opensuse-bugs/2011-05/msg00542.html) 

go to Settings > Application Appearance > GTK+ Appearance and change widget style from oxygen-gtk to Raleigh. Now Geany starts up really fast like on Gnome, but looks like a Windows98 program :P The worst part is that this also affects other GTK+ applications (like in my case Sonata). edit: By install the theme qtcurve and applying that as widget style Geany looks more acceptable on Kubuntu.

---

