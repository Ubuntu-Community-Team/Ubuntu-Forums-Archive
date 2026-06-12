---
title: "KeyText (Windows Program) for Ubuntu?"
date: 2010-07-06
forum: General Help
---

### Post by GPJones on 2010-07-06
I am trying to move completely to Ubuntu. A few programs stop me from making the break from Windows complete.

There is a Windows program called Keytext. This is for automated text entry and is described on the developer's website:
[www.mjmsoft.com](www.mjmsoft.com)

Does anyone know of a similar program for Ubuntu?

Thanks!

---

### Post by Zorgoth on 2010-07-06
I'm not on a linux machine right now so I cant test this, but a cursory google search reveals something called Snippits; have you investigated it?  Also if there is a way to insert text at keyboard focus from the command line you could configure special keyboard shortcuts or write a script to manage them; I don't know if that is possible or feasible in a short time.

---

### Post by Zorgoth on 2010-07-07
I just found a useful tool called xvkbd (a virtual keyboard with command line options) you can get from the repository.  If you make a bash script as follows:

emacs (or gedit or whatever) ~/keypress1
and make the text
```

#!/bin/bash
xvkbd -xsendevent -text "mytext"

```
and then use
```

chmod +x ~/keypress1

```
to make it executable, you can then bind it to a keyboard shortcut using ccsm or xbindkeys, you will have a keyboard shortcut to input text.  You could make a different shell script for each key binding (which shouldn't take long) or if you know how, make one that takes arguments.

In theory you could even use it to input keyboard shortcuts like Control-Shift-Left followed by Delete to delete the last word, but I do not recommend it as my testing showed that this is unreliable.  But for inputting text this will work perfectly.

---

### Post by greigpj on 2010-07-07
Thanks I appreciate your research.
Perhaps some clever developer would take this on as a project?

Also, I can't find anything like a Clip Book. Is there one?

---

### Post by Zorgoth on 2010-07-07
I hadn't heard of Clip Book before, but looking at what I think it is from googling, maybe you would be interested in glipper, klipper, synergy, or parcellite from the repository?

I found these by searching for "clipboard" in Synaptic Package Manager.  Is this the kind of thing you are looking for?

---

### Post by Zorgoth on 2010-07-07
I actually am thinking of working on this once I get my new computer because the idea is interesting and I'm hoping to be able to extend it far beyond just inserting text (i.e. one could even create a keyboard shortcut to autocapitalize or uncapitalize a word).  I probably would ultimately want to find out how to talk to X directly first though rather than through an intermediary.

However, if all you want is, say, to be able to input your email address or some common email with a keyboard shortcut, you won't need to be a developer to use my current solution.

(I'm not a developer really; I just like to play around)

---

### Post by greigpj on 2010-07-07
Thanks! I would sure appreciate something like that being done.

---

### Post by greigpj on 2010-07-07
I found the clip board program.
I am not a programmer so can't do this.
However, I was wondering if it would be possible to create a clip board with say 10 permanent entries and maybe 5 or so entries that change as you copy them to the clip board.

You would be able to change the permanent entries but the others would be the copy to clip board type and could be overwritten.

Hope that makes sense.

Thanks!

---

### Post by mike555 on 2010-07-08
Perhaps this ...  [http://lifehacker.com/351285/automate-repetitive-typing-with-snippits](http://lifehacker.com/351285/automate-repetitive-typing-with-snippits)  
 ... I haven't tried it .

---

### Post by mike555 on 2010-07-08
or perhaps ' AutoKey " ,it's in package manager.

---

### Post by greigpj on 2010-07-08
Thanks everyone!

I installed AutoKey but it does not show up menu.
Then I though maybe it put it in the panel but no.
I am mystified, I don't know where it went.

After 20 some years of Windows, Ubuntu and Linux remain a bit of a mystery but am not giving up. I just think I may be hi-lighting areas that if altered slightly would be more intuitive.

Besides, going back and forth between Windows and Ubuntu shows the distinct advantage that Ubuntu has in startup/shutdown, and speed. It runs circles around Windows! I could see that immediately and since I want my OS to be able to keep up with my mouse, keyboard and thought process, Linux wins hands down in that department.

---

### Post by Zorgoth on 2010-07-09
Try "Alt-F2" and the ntype autokey

---

### Post by greigpj on 2010-07-09
Thanks that works! And now it does show up under Applications > Accessories.

Now tell me how I can get rid of MSFT Expression Web and hopefully find something that approaches it's functionality. Maybe I should say feature set?

Thanks!

---

### Post by Gibbs on 2010-07-09
> **greigpj said:**
> 
Now tell me how I can get rid of MSFT Expression Web
Thanks!

Use a text editor? I work in gedit but theres plenty of others like Bluefish. 

If you want a WYSIWYG Kompozer does HTML/CSS - I don't think it's very comprehensive but a lot people use text editors or have an interface/CMS on their site for authoring.

---

### Post by quimkaos on 2010-07-09
> **Gibbs said:**
> Use a text editor? I work in gedit but theres plenty of others like Bluefish. 

If you want a WYSIWYG Kompozer does HTML/CSS - I don't think it's very comprehensive but a lot people use text editors or have an interface/CMS on their site for authoring.

also netbeans and cssed editor... komodo edit too
yes i would love something like Dreamweaver in linux...

---

