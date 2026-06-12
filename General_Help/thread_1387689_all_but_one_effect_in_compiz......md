---
title: "all but one effect in compiz....."
date: 2010-01-22
forum: General Help
---

### Post by basbuntu on 2010-01-22
hi all, 

after searching for two days i thought i'd ask here....

have my desktop running karmic, and it runs like a beauty.
but i can't seem to get the water effect  in compiz running, all other effects do run :confused:

have an nvidia quadro4 980 
and intel dual xeon 3.00Ghz

hope you guys have an idea.

---

### Post by Saiko Berry on 2010-01-22
Dont worry. You arn't missing anything. It's almost as annoying as driving without windshield wipers.
Linux's greatness != Compiz

---

### Post by basbuntu on 2010-01-22
> **Saiko Berry said:**
> Dont worry. You arn't missing anything. It's almost as annoying as driving without windshield wipers.
Linux's greatness != Compiz

yeah i know, but don't you hate it when something that should work, doesn't?
and i really love the pidgin notification thingy :D

---

### Post by Saiko Berry on 2010-01-22
libnotify isnt part of compiz. :p

---

### Post by basbuntu on 2010-01-22
> **Saiko Berry said:**
> libnotify isnt part of compiz. :p

[http://www.youtube.com/watch?v=-nI3tTctdM4](http://www.youtube.com/watch?v=-nI3tTctdM4)

:D

---

### Post by Saiko Berry on 2010-01-22
I see. That's quite nice. Did you initiate it using the water initiation keybindind?

---

### Post by basbuntu on 2010-01-22
yes i tried it with several different keybindings but none of them reacted.....

---

### Post by Saiko Berry on 2010-01-22
Are you using ccsm? Is the box checkmarked for water effect? Is the hotkey shared/ Do other key bindings work? Try turning off the fire and whatever other ones are in that cateogry then turn on the water see if it works. I see no reason why it wouldnt work.

---

### Post by basbuntu on 2010-01-22
> **Saiko Berry said:**
> Are you using ccsm? Is the box checkmarked for water effect? Is the hotkey shared/ Do other key bindings work? Try turning off the fire and whatever other ones are in that cateogry then turn on the water see if it works. I see no reason why it wouldnt work.

yep, yep, don't know what you exactly mean (shared hotkey?) and yes. 

i even turned off all other effects, leaving just the water effect on....but no luck. :(

---

### Post by basbuntu on 2010-01-22
btw reflection effect doesn't seem to do much either...(although i'm not quite sure what is does :P )


ahum....bump....

---

### Post by basbuntu on 2010-01-22
isn't there anyone familiar with this problem? this is frustrating the heck out of me....

---

### Post by c0mput3r_n3rD on 2010-01-22
> **basbuntu said:**
> [http://www.youtube.com/watch?v=-nI3tTctdM4](http://www.youtube.com/watch?v=-nI3tTctdM4)

:D


Where do you get that from?  I don't see an option for it any where...

---

### Post by JiuJitsu500 on 2010-01-22
[Here]("http://gitweb.compiz.org/") is Compiz's git repository if you know how to use it.... the 3D one is the anaglyph one, and is one of the cooler ones. Maybe basbuntu... re-install the water effect?

:)

---

### Post by basbuntu on 2010-01-23
> **c0mput3r_n3rD said:**
> Where do you get that from?  I don't see an option for it any where...


[http://forums.linuxmint.com/viewtopic.php?f=42&t=7065](http://forums.linuxmint.com/viewtopic.php?f=42&t=7065)

here it is, works like a charm on my netbook. :)

---

### Post by basbuntu on 2010-01-23
> **JiuJitsu500 said:**
> [Here]("http://gitweb.compiz.org/") is Compiz's git repository if you know how to use it.... the 3D one is the anaglyph one, and is one of the cooler ones. Maybe basbuntu... re-install the water effect?

:)


noobuntu!    	 	 	 	 	any guides or howto's on the git repository? that's new for me.......

  	 	 	 	 	 	  ah i see! gonna look into it, thanks!

---

### Post by basbuntu on 2010-01-23
> **JiuJitsu500 said:**
> [Here]("http://gitweb.compiz.org/") is Compiz's git repository if you know how to use it.... the 3D one is the anaglyph one, and is one of the cooler ones. Maybe basbuntu... re-install the water effect?

:)

i'm afraid using git is going too much of a hassle for a noob like me....
i did however reinstall all of compiz, but no luck. 

i really don't get it. *pulling out hair* :(

---

### Post by stinkeye on 2010-01-23
ctrl + w works for initate for me.

---

### Post by basbuntu on 2010-01-25
....and the search continues....

still found no good reason why this isn't working.


nobody with a similar problem?

---

### Post by howefield on 2010-01-25
> **basbuntu said:**
> ....and the search continues...

Not all graphics cards seem to work with the water effect.

What is the make/model of yours.

What's the output of these terminal commands..

```
lspci | grep VGA
```
```
glxinfo | grep GL_ARB_fragment
```

---

### Post by basbuntu on 2010-01-25
> **howefield said:**
> Not all graphics cards seem to work with the water effect.

What is the make/model of yours.

What's the output of these terminal commands..



thanks for the reply...

```
lspci | grep VGA
```gives me:

01:00.0 VGA compatible controller: nVidia Corporation NV28GL [Quadro4 980 XGL] (rev a1)


and


```
glxinfo | grep GL_ARB_fragment
```doesn't give me an output?

could give a full output for glxinfo if you like...

---

### Post by Vaphell on 2010-01-25
if there is no output, it means that there was no such string in the glxinfo output

your gfx card is quite old and apparently it doesn't have features necessary for water plugin to work.

---

### Post by howefield on 2010-01-25
> **basbuntu said:**
> doesn't give me an output?..

No output means the card doesn't support GL_ARB_fragment_program, so the water plugin simply will not work. Sorry. :(

Do a search for "GL_ARB_fragment water compiz" or similar if you want more info.

---

### Post by basbuntu on 2010-01-25
> **Vaphell said:**
> if there is no output, it means that there was no such string in the glxinfo output

your gfx card is quite old and apparently it doesn't have features necessary for water plugin to work.


aaah that's a shame. at least i know now not to get my hopes up too high with this.

one more question:
does this go for more effects in compiz? (using my graphics card?)
because all the effects seem to work except water and reflection......

thanks for the help. gotta love the boards. gotta love ubuntu!

---

