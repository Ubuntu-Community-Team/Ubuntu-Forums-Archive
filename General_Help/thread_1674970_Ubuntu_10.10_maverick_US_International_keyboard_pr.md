---
title: "Ubuntu 10.10 maverick US International keyboard problems w/ dead keys"
date: 2011-01-24
forum: General Help
---

### Post by take-kun on 2011-01-24
Hello,

I have configured my Ubuntu touse the US International keyboard layout with dead keys and most applications are working fine with this setup, but some of them are not respecting the keyboard I set.

For example, I'm having problems with Skype, Netbeans and some applications I opened using wine. Instead of using my configuration, I can't type accents using the expected combinations (for example, typing the ' symbol and the letter a should yield á, but it is simply not working, or yielding 'a in some applications. 

Little help, anyone? Thanks a lot in advance.

---

### Post by Tamhvm on 2011-04-04
I don't know if this might help you at all, but I think you need to  set a special environment variable for some programs to properly use the right keyboard layout in all graphic programs.
If you're in Ubuntu, open up your Session Manager (System > Preferences > Startup Applications) and add this small task on top of everything else:
```
export GTK_IM_MODULE=xim
```
(you're free to set the name of the command and the description as you like)

This happens because lots of programs depend on GTK libraries to supply them with input, so, well, I think it will solve your problem.

You might also want to check out my *Win US Intl 4 Linux* project at [http://t.tam.x10.mx/en/win-us-intl-4-linux/](http://t.tam.x10.mx/en/win-us-intl-4-linux/) to find a way to mimic the behavior of the Microsoft Windows US - International keyboard layout. (mainly for these problems with 's outputting that weird &#347;, 'r resulting in &#341; or 't not working).

[SIZE="1"]EDIT#1: Edited to update the web address.[/SIZE]

---

