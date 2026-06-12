---
title: "US-International keyboard layout all wrong and difficult to use."
date: 2010-04-10
forum: General Help
---

### Post by mitchells00 on 2010-04-10
The US-International layout in K/Ubuntu seems to be extremely irritating and difficult to use. I'm wondering if I could find some help here.

One thing is if a dead key doesn't work (typing in ' + t for example) it will produce nothing in Ubuntu, as opposed to windows producing 't. I must add a space after almost every apostrophe or quotation mark, which is becoming extremely difficult, tedious, irritating and unnecessary.

Also the dead keys that are available are ridiculous. The dead keys I am used to and want are: 

' + [letter] = éýúíó á ç
" + [letter] = ëÿüïö ä
` + [letter] = èùìò à
~ + [letter] = õ ã ñ
^ + [letter] = êûîô â

Which allows one to simultaneously and smoothly type English, Dutch and German but could (to a lesser extent) be used for French.

What I get:

&#7811;é&#341;ýúíó&#7765; á&#347;&#501;&#7729;&#314; &#378;&#263;&#472;&#324;&#7743;
&#7813;ë&#7831;ÿüïö ä&#7719; &#7821;
&#7809;è&#7923;ùìò à &#476;&#505;
&#7869;&#7929;&#361;&#297;õ ã &#7805;ñ
&#373;ê&#375;ûîô â&#349;&#285;&#293;&#309; &#7825;&#265;

Which makes 's (&#347;) painful, as well as the many uses for apostrophes in dutch like m'n and 'k (producing m&#324; and &#7729; respectively) etc. 

Considering this layout is widely used and is pretty much the de facto layout in The Netherlands whose primary languages would be Dutch and English (and some German), why has it become so difficult to use? Also, how do I fix it?


Thanks in advance for your helpful replies!
Mitchells00

---

### Post by cogier on 2010-04-10
I presume you are looking to change the keyboard layout. This can be done from **System>Preferences>Keyboard**, select the **Layouts** tab then click **Add**.

Once you have selected the keyboard you want make sure you set it as Default.

---

### Post by mitchells00 on 2010-04-10
> **cogier said:**
> I presume you are looking to change the keyboard layout. This can be done from **System>Preferences>Keyboard**, select the **Layouts** tab then click **Add**.

Once you have selected the keyboard you want make sure you set it as Default.

I have the correct layout and I know how to change it. What I asked is how can I modify the behaviours of a specific layout, especially with regard to dead key behaviour. I did specifically say that I was using the layout I wanted, but it had behaviours that made it almost impossible to use as one usually would.

I do understand that you're quite busy, but please take some more time to read and understand what people post. If you had, you would have noticed that your answer was completely irrelevant and not at all helpful. Though I do appreciate that you answered and I'm sorry if I come across as ungrateful.

---

### Post by jwbrase on 2010-04-10
Well, you can use Alt-Gr to get the symbol that would normally be on that key instead of the dead diacritic (for example Alt-gr + " is the same as " + space). You can also use the US International (Alt-Gr dead keys) layout, which moves the dead keys to Alt-Gr + [dead key]. I use it because the dead keys on the normal International layout trip me up, whereas when triggered with Alt-Gr it acts just like a US Standard keyboard unless I need special characters.

Also, many (though not all) of the characters you want can be accessed in both layouts with Alt-Gr + [something], without having to use a dead key.

---

### Post by cogier on 2010-04-10
Sorry for not getting your point first time around. As I slipped up so badly I went looking for something but there does not seem to be anything simple out there but I found this that I hope might help.[http://ubuntuforums.org/showthread.php?t=188761]("http://ubuntuforums.org/showthread.php?t=188761")

---

### Post by mitchells00 on 2010-04-10
Thanks heaps! That is exactly what I was looking for, although it may take some time to put into place but I was searching for hours... You're awesome :)

---

### Post by jwbrase on 2010-04-10
Be advised, though, that the link is somewhat old and the files are in a different directory: /usr/share/X11/xkb instead of /etc/X11/xkb

You also need to add your new layout to symbols.dir for it to be available. (Actually, the link does tell you to create a backup then overwrite the old keyboard with your new one. If you do that, it will already be in symbols.dir.)

---

### Post by glósóli on 2010-11-16
> **mitchells00 said:**
> Thanks heaps! That is exactly what I was looking for, although it may take some time to put into place but I was searching for hours... You're awesome :)

hey mitchell

I'm facing ur same problem since I'm living in the NL; would you be so kind to post all the modifications you added to have the keyboard working like we are used to?
that could save me quite some time! :)

Many thanks!

EDIT: ignore my request, basically USA layout with dead keys does exactly what I want!

---

### Post by Sabetsu on 2011-01-05
I am having the same exact problem as the OP. I know that this thread was made almost a year ago, but I would love to know the fix for this problem. I have gotten into the us (/usr/share/X11/xkb/symbols) file in gedit, but when I look for the corresponding key (AC11) all I get is:

key <AC11> {    [ apostrophe,    quotedbl    ]    };

Which tells me that all this key is doing is giving an apostrophe, and making a quotation mark. How can I fix it so that when I am typing things like "I'm" that I don't get "I&#7743;" instead? It is very annoying to circumvent using shortened forms of words, or to press space every time I press the apostrophe key to avoid getting accented letters.

I do not want to press the AltGR key every time either. I would love to see the solution the OP made to their file in order to make this work, as none of the keyboard layouts in English or in Dutch are working for me in preventing this extremely annoying problem.

---

### Post by glósóli on 2011-01-05
> **Sabetsu said:**
> I am having the same exact problem as the OP. I know that this thread was made almost a year ago, but I would love to know the fix for this problem. I have gotten into the us (/usr/share/X11/xkb/symbols) file in gedit, but when I look for the corresponding key (AC11) all I get is:

key <AC11> {    [ apostrophe,    quotedbl    ]    };

Which tells me that all this key is doing is giving an apostrophe, and making a quotation mark. How can I fix it so that when I am typing things like "I'm" that I don't get "I&#7743;" instead? It is very annoying to circumvent using shortened forms of words, or to press space every time I press the apostrophe key to avoid getting accented letters.

I do not want to press the AltGR key every time either. I would love to see the solution the OP made to their file in order to make this work, as none of the keyboard layouts in English or in Dutch are working for me in preventing this extremely annoying problem.

actually this exact same last bit would be the last one to have my keyboard configured perfectly!
so by helping Sabetsu u would actually help 2 guys at the same time!

---

### Post by Sabetsu on 2011-01-05
> **glósóli said:**
> actually this exact same last bit would be the last one to have my keyboard configured perfectly!
so by helping Sabetsu u would actually help 2 guys at the same time!

So it the US-International layout with dead keys didn't end up working for you as you had said it did in your last post?

    key <AC11> { [dead_acute, dead_diaeresis, apostrophe,        quotedbl ] };

I think this line has something to do with the problem. It is farther down in the document. Anyone know what I might have to delete and/or add to get this working properly?

---

### Post by glósóli on 2011-01-06
> **Sabetsu said:**
> So it the US-International layout with dead keys didn't end up working for you as you had said it did in your last post?


well before I was using the plain US layout (I think) and switching to this one I can now do stuff like á, é, l'a and so on
but still I gotta hit the spacebar in between. If I could avoid that, it would be quite a time saver!

---

### Post by Sabetsu on 2011-01-07
> **glósóli said:**
> well before I was using the plain US layout (I think) and switching to this one I can now do stuff like á, é, l'a and so on
but still I gotta hit the spacebar in between. If I could avoid that, it would be quite a time saver!

You can also press the apostrophe key twice.

---

### Post by Tamhvm on 2011-04-04
You might be interested in this small project of mine to customize the US - International keyboard layout (built from my issues with those extra characters, like &#347; and &#7743; when I'm writing raw english).

Win US Intl for Linux is a series of scripts I wrote to solve the issue of having problems with the Linux's native US Intl keyboard layout. I use it mainly because my mother language is Spanish, and I still use lots of English forums, texts, chats and so on (like this site).

This is not a complete copy of Windows behavior as there are some borderline cases which I haven't scripted yet (but I'm on my way). You can go to [http://t.tam.x10.mx/en/win-us-intl-4-linux/](http://t.tam.x10.mx/en/win-us-intl-4-linux/) to check it out.

[SIZE="1"]EDIT#1: Edited to update the web address.[/SIZE]

---

### Post by jasonmeggs on 2013-01-30
Hi all,

My version of this problem could seem simple and obvious now but when you can't figure out your keyboard on a new install it is not always easy! Often the first problem a user faces.

Just installed Lubuntu 12.04, programming in Python.

A top problem I faced was this one, the inability to type a proper single or double-quote. I tried quite a few keyboard maps, web searches (which were not honing in well on this type of issue), plus looking in config files, eventually resorting to copy-and-paste of quotes (!) due to production pressures, and finally investigating various suggestions on this thread. LXKeymap was an obvious choice to try, however I tried many options including ones I thought I was familiar with, but they all had the problem with quotes, or were a very different keyboard than I'm used to (e.g., Colemak). 

It would have been helpful to see a description of how each keyboard works while trying them. However, I did not seek one online for each option. 

Then there was trying out the "Keyboard Method Switcher", "Keyboard and Mouse" and the "Keyboard Input Methods" options in preferences. That latter one brought up an unexplained opportunity to start the IBUS Daemon, trying it out didn't seem to do anything. I also tried "man -k <search term>" approaches and more. Very strange, how can it be so hard to type a quote&#8253;&#8253;&#8253;

In the end I found two functional solutions:

1) Pressing alt-" or alt-' gave me the actual quote in many cases (found by trying things). Whether you like this or not, at least it provided a way.

2) Scrolling down far enough the AltGr (specifically, "English (internatonal AltGr dead keys)" gave me a method I'm familiar with from Ubuntu 10.04. (I had mistakenly thought "English (US, international with dead keys)" would be that option and probably  did not understand that one must "Apply" the keyboard to try it (easy to miss and a cautious person may not want to start making global settings before understanding them, the GUI can give that impression to a new user; I would definitely opt for the trial window to set as soon as a keyboard is selected, and if possible show a keyboard map and at least a short overview of how each one is used).

In general I've had a lot of problems with keyboard settings, both in linux offerings and Windows (none yet in MacOS). Typically these revert or need to be set manually each time. I had the same problem in Windows, where the quotes seemingly required irregular extra typing by context (e.g., extra spaces). Probably the alt-" method would have worked. I did not get a functional AltGr there. In Ubuntu 10.04 I had the problem that no matter how many ways I tried to set my default keyboard, it would change back to the one I didn't want. (I have not rebooted since, so this problem may occur in this new lubuntu as well, however at least a new terminal window has the proper keymapping.)

The troubles I've seen might in some cases have been compounded by international work (many issues do arise there!).

I hope this is helpful.

Jason Meggs
---
By the way, the link offered near the end of the thread sounded interesting but was not available when I tried ([http://t.tam.x10.mx/en/win-us-intl-4-linux/](http://t.tam.x10.mx/en/win-us-intl-4-linux/))

---

### Post by oldos2er on 2013-01-31
Old thread closed.

---

