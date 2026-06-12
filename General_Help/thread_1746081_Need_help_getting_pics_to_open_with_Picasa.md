---
title: "Need help getting pics to open with Picasa"
date: 2011-05-01
forum: General Help
---

### Post by wolfen69 on 2011-05-01
I want Picasa to be the default viewer for my pics. Yes, I've right clicked>properties>open with and picasa is not given as an option. Going to  default media options also does not give me picasa. I don't know where else to look for changing it. Something in gconf-editor perhaps? Thanks for any help.

---

### Post by tredegar on 2011-05-01
Have you installed picasa?

It's not in my 10.04 ubuntu repositories. It looks like it is a google-thing, which means I will not be installing it.

You have to install it before you can use it.

---

### Post by Blasphemist on 2011-05-01
Google quit on picasa for linux a couple years ago. Version 3 is old and still beta. They aren't it developing for linux now.

I now use Shotwell and have come to like it, but I don't do a whole lot other than manage my pictures and picasa web albums. I often use the web access to picasa web albums to upload large numbers of files when I need to.

---

### Post by mc4man on 2011-05-01
> **wolfen69 said:**
> I want Picasa to be the default viewer for my pics. Yes, I've right clicked>properties>open with and picasa is not given as an option. Going to  default media options also does not give me picasa. I don't know where else to look for changing it. Something in gconf-editor perhaps? Thanks for any help.
Happened to be fooling around with - anyway,
Because of the way/where it installs it's likely not to show directly in the properties > open with menu. (though by altering the .deb did get it to here - screen - Picasa with icon

You should however be able to from the properties, just click 'Add' > 'Use a custom command' and enter picasa there. (in screen that the lower case picasa

---

### Post by wolfen69 on 2011-05-01
> **mc4man said:**
> Happened to be fooling around with - anyway,
Because of the way/where it installs it's likely not to show directly in the properties > open with menu. (though by altering the .deb did get it to here - screen - Picasa with icon

You should however be able to from the properties, just click 'Add' > 'Use a custom command' and enter picasa there. (in screen that the lower case picasa

I'm using 11.04 with gnome 3 and my "add" button is grayed out and can't use a custom command.

---

### Post by mc4man on 2011-05-01
> **wolfen69 said:**
> I'm using 11.04 with gnome 3 and my "add" button is grayed out and can't use a custom command.

Don't know anything as yet about gnome3
If can't find anything in gconf or dconf and you want to try altering the .deb I'll post the changes I made and how to  - have on other machine

(basically gave picasa's .desktop a decent Categories= line, added a full MimeType= line, and had the .desktop install to a /share/applications dir.

---

### Post by Blasphemist on 2011-05-01
I'm curious about this. Why do you guys prefer picasa to shotwell? I'm still getting someone used to linux and have them on mint. He was used to picasa in windows and I'm about to convert him to shotwell, at least that is my plan.

---

### Post by mc4man on 2011-05-01
> **Blasphemist said:**
> I'm curious about this. Why do you guys prefer picasa to shotwell? I'm still getting someone used to linux and have them on mint. He was used to picasa in windows and I'm about to convert him to shotwell, at least that is my plan.
I don't - there was[ a thread about]("http://ubuntuforums.org/showthread.php?p=10748903#post10748903") getting picasa into the unity dash, was a bit curious so started by making the .deb a little more suitable.
While that alone wasn't enough it did allow picasa to start showing up in expected places like the r. click - prop. and the main menu

---

### Post by wolfen69 on 2011-05-01
> **mc4man said:**
> Don't know anything as yet about gnome3
If can't find anything in gconf or dconf and you want to try altering the .deb I'll post the changes I made and how to  - have on other machine

(basically gave picasa's .desktop a decent Categories= line, added a full MimeType= line, and had the .desktop install to a /share/applications dir.

Thanks, I would appreciate it.

> **Blasphemist said:**
> I'm curious about this. Why do you guys prefer picasa to shotwell? I'm still getting someone used to linux and have them on mint. He was used to picasa in windows and I'm about to convert him to shotwell, at least that is my plan.

I think it's a really good photo manager/viewer, that's why. Plus, a friend of mine is trying to switch over to linux and the last piece of the puzzle is going to be getting picasa to be the default viewer. He doesn't care for any of the native linux viewers. He has 270,000 pics and needs a robust app for them.

---

### Post by Blasphemist on 2011-05-01
Thanks guys. Just a btw, shotwell import of 5000 pictures is the first thing I've noticed that actually uses the swap.

---

### Post by wolfen69 on 2011-05-01
@mc4man: Thanks for the help, but I got it solved. Here's the workaround: I downloaded Digikam since I heard good things about it. While in it, I went to "open with file manager" and Dolphin opened up. Right clicking a pic in Dolphin gave me the choice of Picasa as default. Now Picasa opens no matter what file manager I'm in. Thanks again.

---

### Post by mc4man on 2011-05-01
Glad you got it... as it turned out here (unity/gnome2/nautilus) the install location was fine
Only needed to add 2 lines to the /opt/google/picasa/3.0/desktop/picasa.desktop.template and it was shown for all the filetypes after install (defined 22 for the h*** of it

---

