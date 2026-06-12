---
title: "gPHPEdit crashes randomly"
date: 2006-06-06
forum: General Help
---

### Post by ifokkema on 2006-06-06
Hi Guys,

I've done a completely new install of Dapper last Friday. I did bring my home directory, but I don't think that differs much.

gPHPEdit, an IDE specifically for editing HTML/CSS/PHP files, crashes randomly at me. I tried installing the latest Breezy version, but that doesn't help much. I also downloaded the source from the official website and compile that, but no change.

It has crashed on typing code, saving files and switching open files.
Sometimes I can't even work for a couple of seconds, other times I can edit my files for a couple of hours before it crashes.

Does anyone have this also? It looks like there is a package that gPHPEdit relies on that is giving these errors, since the Breezy version worked fine on Breezy.

Thanks in advance...

Ivo

---

### Post by Pejalo on 2006-06-18
I am having this exact same problem with Dapper, using gPHPEdit 0.9.80 (most current version).
If anyone who could help us would like any more information, I'd be happy to provide it.
EDIT: I am using the 32 bit Ubuntu install, just in case that helps.

---

### Post by ifokkema on 2006-06-21
Hmm... I've done some testing, and I think this only happens when I have more than 3 pages open. So far, if limiting my concurrent work to 2-3 pages at most, I've had no problems.
[EDIT]I've just had one file (css) open, clicked the 'open file' icon, and it crashed.... sigh....[/EDIT]

I've been using Screem for a while now, but it has some slight annoyances that make we really want to go back to gPHPEdit. Anyone has any idea what's causing this?

---

### Post by ifokkema on 2006-06-22
Uhm... OK, I take this back: even when working on one or two files, the thing just crashed whenever it feels like it.
Earlier today it crashed when I tried to open a second file, but just now it crashed when just typing in a comment... See attachment. I was just typing at line 374, and then it just crashed on me...

Nobody else using gPHPEdit? No-one else having this with some other editor?

---

### Post by andyjeffries on 2006-06-29
As the author of gPHPEdit (and a new Ubuntu 6.06 user from Gentoo) I'd love to help you track down the problem.

Initially can you try running it through gdb (if gdb is installed), then when it crashes type the command "bt" to get a backtrace of what it was doing at the time.

Or if you prefer I could supply a copy of the current SVN version?

Or maybe it's time for a version bump (there's not that much new, but quite a few bugfixes)....

---

### Post by ifokkema on 2006-06-29
[QUOTE=andyjeffries]As the author of gPHPEdit (and a new Ubuntu 6.06 user from Gentoo) I'd love to help you track down the problem.

Initially can you try running it through gdb (if gdb is installed), then when it crashes type the command "bt" to get a backtrace of what it was doing at the time.

Or if you prefer I could supply a copy of the current SVN version?

Or maybe it's time for a version bump (there's not that much new, but quite a few bugfixes)....[/QUOTE]
Hi Andy!

So you're running Dapper now, too? And you don't have the problem yourself?
I personally think it's a dependency of gPHPEdit which is causing the crash, because I have downgraded gPHPEdit to the version which is on Breezy, but that doesn't prevent it from crashing. Isn't that a clue? It crashes when typing, switching windows, opening files or even when browsing folders in the 'Open' dialog. And not all the time, but too many times to work properly. The biggest annoyance maybe is that when it crashes, it doesn't remember what it had open :S

I've got Breezy at home, and Dapper at work. I'm not getting to work until Monday. Do you still want me to send you a backtrace? I can't decipher that stuff, but if you could take a look at it, that'll be great :)

---

### Post by andyjeffries on 2006-07-02
[QUOTE=ifokkema]Hi Andy!

So you're running Dapper now, too? And you don't have the problem yourself?
I personally think it's a dependency of gPHPEdit which is causing the crash, because I have downgraded gPHPEdit to the version which is on Breezy, but that doesn't prevent it from crashing. Isn't that a clue? It crashes when typing, switching windows, opening files or even when browsing folders in the 'Open' dialog. And not all the time, but too many times to work properly. The biggest annoyance maybe is that when it crashes, it doesn't remember what it had open :S

I've got Breezy at home, and Dapper at work. I'm not getting to work until Monday. Do you still want me to send you a backtrace? I can't decipher that stuff, but if you could take a look at it, that'll be great :)[/QUOTE]

I am running Dapper, I'm a newbie to Ubuntu though so it's a bit of a learning process at the minute.  I don't have the problem myself, but as you can imagine I'm using the bleeding edge version from subversion.

What might be a good idea (for me) is that at the moment it remembers what you had open when you quit, if it did this on every open/save/close it would remember them for if it crashes.  I'll do that in a little bit.

Feel free to send me a backtrace and I'll look in to it from there.  If you have build-essential installed and the gnomeui, gtk and gtkhtml2 dev packages I don't mind sending you a tarball of the latest subversion version.  Of if anyone can point me to an EASY tutorial on how to make a .deb, I'll give that a go.

---

### Post by andyjeffries on 2006-07-03
I tried opening about 30 files at the same time and also got a crash.  I've changed the version of Scintilla used in the Subversion version to the latest one and now it doesn't crash.

I'll do a new release RSN*, but if anyone wants a tarball, let me know.

Cheers,


Andy

* Real Soon Now

---

### Post by ifokkema on 2006-07-03
[QUOTE=andyjeffries]What might be a good idea (for me) is that at the moment it remembers what you had open when you quit, if it did this on every open/save/close it would remember them for if it crashes.  I'll do that in a little bit.[/QUOTE]
That would be great! We've had our share of power outages here as well (new building) and everytime I lost this 'history'.

[QUOTE=andyjeffries]Feel free to send me a backtrace and I'll look in to it from there.[/QUOTE]
I've just worked with a couple of files today, and my attempt to crash it by editing something like 5 files haven't crashed it yet. I'll try again tomorrow :)

[QUOTE=andyjeffries]Of if anyone can point me to an EASY tutorial on how to make a .deb, I'll give that a go.[/QUOTE]
I believe there was a very simple way by using the 'checkinstall' package. From within your source, after ./configure and make, run 'checkinstall'. It should ask you some questions and build a basic .deb package, easy for installing/uninstalling.

[QUOTE=andyjeffries]I tried opening about 30 files at the same time and also got a crash.  I've changed the version of Scintilla used in the Subversion version to the latest one and now it doesn't crash.[/QUOTE]
That sounds great! I guess we won't be having the latest Scintilla in Dapper, so we should compile or package Scintilla as well, right?

---

### Post by andyjeffries on 2006-07-04
[QUOTE=ifokkema]That would be great! We've had our share of power outages here as well (new building) and everytime I lost this 'history'.[/QUOTE]

It's done in the subversion version now.

[QUOTE=ifokkema]I believe there was a very simple way by using the 'checkinstall' package. From within your source, after ./configure and make, run 'checkinstall'. It should ask you some questions and build a basic .deb package, easy for installing/uninstalling.[/quote]

OK, great I'll give that a go.  Thanks for that.

[QUOTE=ifokkema]That sounds great! I guess we won't be having the latest Scintilla in Dapper, so we should compile or package Scintilla as well, right?[/QUOTE]

Nope, gPHPEdit includes the scintilla library in it's tarball (IIRC because there are two "competing" versions of GtkScintilla2 and Debian wouldn't let either one through and unification is difficult).

So in the next release, everything should be fine.

It'll probably be in a couple of weeks (I really need to hammer it for a while first), but it seems all good here :-)

---

### Post by ifokkema on 2006-07-05
Thanks for the fix!
I ran gPHPEdit through gdb, and it crashed (I guess) when pressing F9 to check for parse errors. It stopped responding, the screen doesn't refresh when moving an window in front of it. Gdb says:
```
(...)
[New Thread -1246544976 (LWP 20047)]
[New Thread -1237685328 (LWP 20048)]
[Thread -1246544976 (LWP 20047) exited]
[Thread -1237685328 (LWP 20048) exited]
thread_db_get_info: cannot get thread info: generic error
(gdb) bt
#0  0x00000000 in ?? ()
```
That's it! The new thread/thread exited appear also when opening/saving/closing files and all, so I guess these are normal. But the backtrace is really short. Maybe I just don't get gdb, never used it before :)
Maybe I should use strace, or let Gnome figure out the backtrace? Before, when not using gdb, gPHPEdit crashed and I had the option to inform the developers. It then gave me a backtrace, I think.

Edit: Clearly, I don't understand gdb. I could just type 'continue', and gPHPEdit continues. So it didn't crash after all, I gues...

---

### Post by andyjeffries on 2006-07-05
Try the latest version - [www.gphpedit.org](www.gphpedit.org) - I just released 0.9.91 :-)

---

### Post by ifokkema on 2006-07-06
[QUOTE=andyjeffries]Try the latest version - [www.gphpedit.org](www.gphpedit.org) - I just released 0.9.91 :-)[/QUOTE]
SUPER!
I've compiled it and ran `sudo checkinstall` to build me a .deb package. Running it now, will let you know how it's doing :)

Thanks again!

---

### Post by Cred on 2006-07-10
> **ifokkema said:**
> SUPER!
I've compiled it and ran `sudo checkinstall` to build me a .deb package. Running it now, will let you know how it's doing :)

Thanks again!

Care to put the deb online? The random crashes are annoying.

---

### Post by ifokkema on 2006-07-10
> **Cred said:**
> Care to put the deb online? The random crashes are annoying.
This is the .deb I created from the source using checkinstall:
[http://www.ifokkema.nl/gphpedit-0.9.91_0.9.91-1_i386.deb](http://www.ifokkema.nl/gphpedit-0.9.91_0.9.91-1_i386.deb)

It hasn't crashed on me yet!
Replace All still is acting weird (doesn't crash like before but hangs on 100% CPU). Also, just one small new thing - selected text appears with a yellow background and I can't seem to change this. It's hard to clearly see the selected text.

Anyway, I'm all happy since this version doesn't seem to crash on me ;)

---

### Post by Cred on 2006-07-11
> **ifokkema said:**
> 
Anyway, I'm all happy since this version doesn't seem to crash on me ;)

Thank you so much! It definetly is far more stable, no crashes in the four hours I've been using it.

---

### Post by andyjeffries on 2006-07-11
> **ifokkema said:**
> This is the .deb I created from the source using checkinstall:
[http://www.ifokkema.nl/gphpedit-0.9.91_0.9.91-1_i386.deb](http://www.ifokkema.nl/gphpedit-0.9.91_0.9.91-1_i386.deb)

It hasn't crashed on me yet!
Replace All still is acting weird (doesn't crash like before but hangs on 100% CPU). Also, just one small new thing - selected text appears with a yellow background and I can't seem to change this. It's hard to clearly see the selected text.

Can you send me the file and terms you're searching/replacing (email is fine my name at gphpedit dot org).  I promise I won't publicise the file, just use it for debugging the problem.

Don't forget to pester someone to update it in backports/Edgy :-)

---

### Post by andyjeffries on 2006-07-11
> **Cred said:**
> Thank you so much! It definetly is far more stable, no crashes in the four hours I've been using it.

That's great :-)

---

### Post by ifokkema on 2006-07-11
> **andyjeffries said:**
> Can you send me the file and terms you're searching/replacing (email is fine my name at gphpedit dot org).  I promise I won't publicise the file, just use it for debugging the problem.
Thanks, I've just send you the file and the list of things that I did to reproduce the crash/100% CPU usage.

---

### Post by Bobbafett on 2006-09-17
Hello all,
I successfully installed gphpedit 0.9.91 from source... if I type in 'gphpedit' at the terminal I get the app running and was able to create some php documents ... the only problem is that I didn't get the "gphpedit" icon/option anywhere under the Applications menu, did I missed something or do I need to add it manually? if so, how? I am using Ubuntu 5.10.

Thanks ;)

---

### Post by ifokkema on 2006-09-17
I've built a .deb from source, and it got the entry in the menu, but that's Dapper. I know Dapper also has a menu editor (Alacarte), but I don't think that's in Breezy.

You can always just add a custom app launcher to your panel...

---

### Post by Bobbafett on 2006-09-17
Hi,
Yes, I added a launcher to the panel and another to the desktop, but I was wondering if there is a way to get it into the Applications menu :p

---

### Post by Bobbafett on 2006-09-20
Got it! First I noticed that without doing anything the gPHPedit icon was added to the Applications/Programming the next time I restarted the laptop, cool :cool: 
Also I found the "Applications Menu Editor" utility under Systems Tools that does exactly what I was looking for :tongue:

---

### Post by ifokkema on 2006-09-20
Ah great! Probably then logging out and back in would have been enough for getting it in the menu, but the editor is great to have, too.

---

### Post by Bobbafett on 2006-09-24
Hopefully a change to the selected text background color can be squeezed in the next release, it is hard to see the selected text in my not-so-great laptop display :p

---

### Post by ifokkema on 2006-09-24
True, somehow the newly selected text is highlighted yellow in the latest release. Only when you select some other text in some other program and you return to gPHPEdit, it's the familiar grey again.

---

