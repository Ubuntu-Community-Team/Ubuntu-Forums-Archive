---
title: "Computer Janitor - which version  in 10.04?"
date: 2011-07-15
forum: General Help
---

### Post by grey1beard on 2011-07-15
This is a bit weird, but in thinking about cleaning up my hdd, which has a single install of 10.04/EMC2 on it, I took my first look at Computer Janitor.
When it opened, it seemed amazingly basic, in fact just two panes with no indication of what the few entries were indicating.
The "About" tag  in the Help menu indicated that it was version 1.13.3, but Synaptic tells me that version 1.14.1 is installed.
A bit of reading in the Forum suggests that this is not highly thought of, anyway, so I shall leave it alone.

As I'm currently having other issues with this installation, and am about to do a clean install, I thought I'd drop this pebble in the pond, and learn a bit more before my next turn around. :)

So if anyone has any thoughts, I'd be happy to read them.

John

---

### Post by mike555 on 2011-07-15
I recommend staying clear of computer janitor , it will mess things up . I used it and had to reinstall......

---

### Post by flipper T on 2011-07-15
+1 for that

computer janitor is so awful its being dropped for 11.10

use bleachbits instead

---

### Post by grey1beard on 2011-07-16
> **grey1beard said:**
> .......
A bit of reading in the Forum suggests that this is not highly thought of, anyway, so I shall leave it alone.......

Thanks guys, but as you see, I am aware.
I'm looking to increase my knowledge base, not use the program !

John

---

### Post by flipper T on 2011-07-16
ok i'm confused / a bit dim

what is your question ?

---

### Post by matt_symes on 2011-07-16
Hi

> **flipper T said:**
> ok i'm confused / a bit dim

what is your question ?

That makes two of us then ;)

@OP. What's your question ?

Kind regards

---

### Post by grey1beard on 2011-07-16
Er, I thought the title of the thread might be sufficient clue ;)
Perhaps I should have asked "Which version _should_ I have"

> The "About" tag in the Help menu indicated that it was version 1.13.3, but Synaptic tells me that version 1.14.1 is installed.
If I've got 1.13.3, as per the appearance and the About tag, but Synaptic reports that I have 1.14.1, this would seem to my untutoured brain a little odd.

> So if anyone has any thoughts, I'd be happy to read them.

John

---

### Post by Linux_junkie on 2011-07-16
Quite simply look under the Help menu at the About option and that will tell you which version has been installed.

For the record I too have 10.04 and have Computer Janitor version 1.13.3 but I have never used it (might remove it) as per what others have said about it.  I don't trust this app when it tells me that libdvdcss2 is not needed on my system when in fact it is needed to allow me to watch my collection of DVD's.

---

### Post by grey1beard on 2011-07-16
Linux_junkie -

> Quite simply look under the Help menu at the About option and that will tell you which version has been installed.

Grey1beard -

> The "About" tag in the Help menu indicated that it was version 1.13.3, but Synaptic tells me that version 1.14.1 is installed. 

Notice anything ?

---

### Post by grey1beard on 2011-07-16
I'll try and spell it out as simply as I can.

I open Janitor.
The gui is very basic.
I click on Help/About.
1.13.3 is installed.

I go to Synaptic Package Manager.
1.14.1 is installed.

A query comes into my mind.
If I wish to remove this, let me go to Ubuntu Software Center.
I go there, and it tells me that Janitor is installed, but shows me the Window of 1.14.1.
Question - If I tell the software center to remove Janitor, what will happen if two parts of the 10.04 installation have different ideas as to what version of Janitor is installed ?

Isn't that a question worth pondering ?
**I have no intention of doing anything**, but I would like to know what others, more experienced than I, think.

I hope that I have now made myself clear.

---

### Post by Dave_L on 2011-07-16
I just downloaded computer-janitor_1.14.1-0ubuntu2_all.deb from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) (a very useful web page).  Then I extracted the contents of the .deb with Archive Manager (File Roller), and used grep to search for "1\.13\.3".  The result:

```
usr/share/computerjanitor/computerjanitorapp/__init__.py:VERSION = "1.13.3"
```

So the explanation is that version 1.14.1-0ubuntu2 has a bug; it contains the wrong verson number internally. I.e., synaptic is correct.

---

### Post by grey1beard on 2011-07-16
Hi Dave.
Thanks for the info and the link.
Not sure I'm up to speed on your last sentence, though.
Are you saying that my Synaptic is reporting 1.13.3 as 1.14.1 ?
That would certainly explain why I seem to have the more primitive gui when I open my copy.
However, why does the Software Center also seem to indicate the later version by showing the more advanced window of 1.14.1 in the "more info" link ?

Is this due to the same "bug" you mention ?

John

---

### Post by Dave_L on 2011-07-16
Synaptic and Software Center are correct. Computer Janitor version 1.14.1 is installed.

The file within Computer Janitor that it uses to show its version number in its Help >> About dialog is wrong.

Forgetting to bump a version number when distributing a new version of a software package is a common mistake for a developer to make.  That's why I suspected that might be the issue.

---

### Post by grey1beard on 2011-07-16
Last question then, Dave.
Why does the gui of my installed version look so primative - ie nothing like the screen shot on the software center page, supposedly a shot of 1.14.1 ?

john

EDIT attached screen shot of gui plus the about window.

---

### Post by Dave_L on 2011-07-16
When I run Computer Janitor, it looks the same as the screen shot you posted.

I don't know where the screen shots in Synaptic or Software Center come from.  But like any documentation, they're subject to inaccuracies; the screen shot could be from a newer version, even an unreleased alpha version; or it could just be a mockup.

Accept the mystery.

---

### Post by grey1beard on 2011-07-16
> **Dave_L said:**
> ...

Accept the mystery.

Ah, words of Wisdom.
Thanks Dave :)

---

