---
title: "How to add text before / after each line in gedit?"
date: 2010-10-23
forum: General Help
---

### Post by inameiname on 2010-10-23
What is a regular expression option to add text prior to the start of a given line? Also, what about after?

Say I have a text file with these lines:

```

This is the first line...
This is the second line...
This is the third line...
This is the fourth line...
This is the fifth line...
This is the sixth line...
This is the seventh line...

```And I would like to add perhaps this before each line:

```

BEFORE I WANT THIS This is the first line...
BEFORE I WANT THIS This is the second line...
BEFORE I WANT THIS This is the third line...
BEFORE I WANT THIS This is the fourth line...
BEFORE I WANT THIS This is the fifth line...
BEFORE I WANT THIS This is the sixth line...
BEFORE I WANT THIS This is the seventh line...

```And perhaps something to add this after each line:


```

This is the first line...I WANT THIS AFTER
This is the second line...I WANT THIS AFTER
This is the third line...I WANT THIS AFTER
This is the fourth line...I WANT THIS AFTER
This is the fifth line...I WANT THIS AFTER
This is the sixth line...I WANT THIS AFTER
This is the seventh line...I WANT THIS AFTER

```I'm sure there is a simple regular expression that can do this.

---

### Post by inameiname on 2010-10-24
Wow, thought this would be an easy one. Guess it's not as easy of a solution as I thought. :P

---

### Post by john77eipe on 2010-10-24
Guess, you need to write a code to do that. If you know java: it's easy to access a text file and append data to it.

---

### Post by inameiname on 2010-10-24
I see. Well I hope not. I'm not good at those. :P

I was hoping there was an easy regular expression. Similar to something like this one, which can replace anything after a certain point, such as ';' here:

?<=;)[^;\r\n]+$    

#selects all after ; on a line <1;WORD 7S>, <2;WORD 7S>, <3;WORD 7S>, & etc. >>>> <1;>, <2;>, <3;>, & etc.

Or this one:

[0-9]\.           

#selects just last digit <1.>, 3<2.>, 214<5.>, 34546346<3.>, & etc.

I thought about modifying them in some way, but I'm at a loss of just how. Perhaps combining for at least adding text AFTER whatever's on each line, IDK.

---

### Post by Vaphell on 2010-10-24
[http://halfhourhacks.blogspot.com/2008/03/gedit-regular-expression-plugin.html](http://halfhourhacks.blogspot.com/2008/03/gedit-regular-expression-plugin.html)
[http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)

besides, standard find & replace will work with \n => \nTEXT BEFORE (won't work at line 1, there is no newline to replace) or with \n => TEXT AFTER\n

---

### Post by inameiname on 2010-10-24
Thanks Vaphil, but I have that installed already. That's how I can use regular expressions inside gedit. It's just finding the correct regular expression to do what I want that eludes me.



UPDATE:

My bad. I noticed the last few comments talk about the same issue. Thank you. I hadn't seen this page in a while to see the potential solution. I'll let you know if it works for me.

---

### Post by inameiname on 2010-10-24
This seems to work. Thanks.

```

besides, standard find & replace will work with \n => \nTEXT BEFORE (won't work at line 1, there is no newline to replace) or with \n => TEXT AFTER\n

```

I figured it was something ridiculously simple. I figured if not, a fancy regular expression command would work, but guess that's not necessary.

I think I can mark this as solved. 

Thanks again.

---

### Post by Vaphell on 2010-10-24
^ and $ are regex symbols for line beginning and end respectively

---

### Post by inameiname on 2010-10-24
Oh, so basically, these do the same thing (minus the first and last lines in a file of course in regards to the normal find and replace method mentioned):

Normal Search & Replace:

\n => \nTEXT BEFORE

=

Regular Expression:

^ => TEXT BEFORE

...and.....................................................................................................

Normal Search & Replace:

\n => TEXT AFTER\n

=

$ => TEXT AFTER

Though, seems the Regular Expression method is better as it includes the first and last lines.

---

### Post by Vaphell on 2010-10-24
yes, ideed :)
regexes rock, though your problem was not the best scenario to showcase their power :)

---

### Post by inameiname on 2010-10-24
Oh I know. I use it regularly, usually for more intricate manners.

---

