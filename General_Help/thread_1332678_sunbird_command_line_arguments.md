---
title: "sunbird command line arguments"
date: 2009-11-20
forum: General Help
---

### Post by pythonscript on 2009-11-20
Does anyone know where I could find documentation on command line arguments for sunbird? I've searched on mozilla's site and I keep coming up empty. Thanks!

---

### Post by SteveDee on 2009-11-20
At a terminal type; sunbird --help

Is this what you need:-

steve@steve-laptop:~$ sunbird --help
Usage: /usr/lib/sunbird/sunbird-bin [ options ... ] [URL]
       where options include:

X11 options
	--display=DISPLAY		X display to use
	--sync		Make X calls synchronous
	--no-xshm		Don't use X shared memory extension
	--xim-preedit=STYLE
	--xim-status=STYLE
	--g-fatal-warnings		Make all warnings fatal

Mozilla options
	-height <value>		Set height of startup window to <value>.
	-h or -help		Print this message.
	-width <value>		Set width of startup window to <value>.
	-v or -version		Print Sunbird version.
	-P <profile>		Start with <profile>.
	-ProfileManager		Start with Profile Manager.
	-UILocale <locale>		Start with <locale> resources as UI Locale.
	-contentLocale <locale>		Start with <locale> resources as content Locale.
	-safe-mode		Disables extensions and themes for this session.
  -jsconsole           Open the Error console.
  -subscribe or -url   Pass in a path pointing to a calendar
                       to subscribe to.
  -showdate            Pass in a value for a javascript date
                       to show this date on startup.

---

### Post by pythonscript on 2009-11-20
So sunbird doesn't have all its features scriptable (like exporting certain categories or automatically importing/exporting a calendar)? Thanks!

---

### Post by SteveDee on 2009-11-21
The command options are rather limiting, so I guess your other option is to create your own extension. You will probably get more help by posting on Mozilla forum.

A couple of links I stumbled upon which may be of interest:-
[http://forums.mozillazine.org/viewtopic.php?f=46&t=480640&start=0](http://forums.mozillazine.org/viewtopic.php?f=46&t=480640&start=0)
[http://www-archive.mozilla.org/projects/calendar/faq.html#gui_jar](http://www-archive.mozilla.org/projects/calendar/faq.html#gui_jar)

---

### Post by llamabr on 2009-11-21
I've been scolded for suggesting it in the past, but you might look at the man page.  i don't use sunbird, or have it installed, so I don't know about cli options.  But that's where I'd start.

---

### Post by pythonscript on 2009-12-05
> **SteveDee said:**
> The command options are rather limiting, so I guess your other option is to create your own extension. You will probably get more help by posting on Mozilla forum.

A couple of links I stumbled upon which may be of interest:-
[http://forums.mozillazine.org/viewtopic.php?f=46&t=480640&start=0](http://forums.mozillazine.org/viewtopic.php?f=46&t=480640&start=0)
[http://www-archive.mozilla.org/projects/calendar/faq.html#gui_jar](http://www-archive.mozilla.org/projects/calendar/faq.html#gui_jar)

I'll have to give this a shot; I have quite a few tricks I'd like to work into my sunbird installation, so it looks like creating some simple extensions would give me the flexibility I'm looking for. 

> **llamabr said:**
> I've been scolded for suggesting it in the past, but you might look at the man page.  i don't use sunbird, or have it installed, so I don't know about cli options.  But that's where I'd start.

As mentioned before, the only command line arguments for sunbird (which doesn't come with a man page, much like firefox doesn't come with one) are listed above. I agree, though, that's it normally a good place to start.

---

### Post by nathan.f77 on 2010-04-29
Hi [pythonscript]("http://ubuntuforums.org/member.php?u=851860"),

Did you ever get around to writing a command line extension for Sunbird?
I am pretty interested in automating a sync between my cellphone and google calendar, using Sunbird in the middle.

Please let me know if you want a hand with coding that extension, or if you've found one already made by someone else.

Cheers,
Nathan B

---

