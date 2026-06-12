---
title: "Macros to generate text in X applications"
date: 2011-10-24
forum: General Help
---

### Post by vilwarin on 2011-10-24
Dear Forum,

I've been looking around the internet and forum threads for a way to basically generate predefined text in any X-application by using a keyboard shortcut.

Example: ctrl+alt+a should paste my address to the currently active window.

I've tried xbindkeys with xvkbd
I've tried xbindkeys with xmacroplay

But both don't really work. Sometimes some crippled text appears, like 1/3 of the text recorded in the macro, resp. given to xvkbd. Most of the time no text at all appears. 

Using the commandline the solution is simple. Just let xbindkeys call "echo predefined text" will work fine. But I'd really like to have such functionality for X-applications (e.g. browser forms).


I am sure some of you have configured their system to have some kind of functionality like this. Could you share, how you managed it?

Thanks,
vilwarin

---

### Post by gsmanners on 2011-10-24
The way I move text around is by selecting it in one app, switching to another app and pressing the middle button on the mouse. Works every time. :D

I can't promise this will work absolutely with the keyboard, though. Not unless you install some kind of clipboard manager (and that depends on your desktop manager).

---

### Post by vilwarin on 2011-10-26
thanks, but that's not really what I am looking for. 
I'd like to produce some predefined text on a key board shortcut.
e.g. pressing ctrl+alt+h produces "Hello World" on the active screen, given it allows for text input.

---

### Post by coldraven on 2011-10-26
Maybe this would help
[http://linuxtidbits.wordpress.com/2008/02/22/command-line-to-clipboard/](http://linuxtidbits.wordpress.com/2008/02/22/command-line-to-clipboard/)
You could launch  the script from a keyboard shortcut then press the middle mouse button to paste your text. maybe :)

---

### Post by vilwarin on 2011-10-31
thank you cold raven,
but I finally found a solution, where you can save the middle-mous-click:

[CENTER]Autokey[/CENTER]

Ubuntu Sources: autokey-gtk

It does exactly what I want. I can choose an arbitrary keyboard shortcut to paste/produce text in the active window. Even more I can define certain text sequences like "qwerty" that will automatically be replaced by a certain predefined text (e.g. my address). 

Tutorial:
[http://saravananthirumuruganathan.wordpress.com/2010/04/14/autokey-linux-utility-for-text-substitution-hotkeys-and-desktop-automation/](http://saravananthirumuruganathan.wordpress.com/2010/04/14/autokey-linux-utility-for-text-substitution-hotkeys-and-desktop-automation/)

Great Tool.
Thread Solved/Closed!

---

