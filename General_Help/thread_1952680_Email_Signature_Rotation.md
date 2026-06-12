---
title: "Email Signature Rotation"
date: 2012-04-04
forum: General Help
---

### Post by Silvernail on 2012-04-04
I am not finding what I think I want. Way back I had a apt that would read a random 'tag line' from a file and copy it to another file  that would then be read by my email client. This apt faithfully follow me through Mandrake, Winspire, and several updates/grades of Ubuntu. I used it on 10.04 and then when I upgraded to 11.04, I lost it.  It went by the name 'sigrot'.

Three weeks I've been looking or reading how to recreate it. Seems everything is a generator, either number or word. Or limits the number of words.

I need a script I can call from a 'crontab' every 10 minutes and it will write a random line from a file with this format:
> 
I looked up in the sky and saw heaven playing poker all night.

Live in such a way that you would not be ashamed to sell your pet parrot to the town gossip.

I lift my pen in rhythm and rhyme  to  tell of a far greater tyme

I was with my children at the moment of their breath.
I stood by my father at the moment of his death.
I stand by you at this moment, forever.

There is nothing in this world,
that beats a six shooter and a red haired girl.

There is no blame in the San Andreas Fault.

"Once is happenstance. Twice is coincidence. Three times is
	enemy action." 
			- Ian Fleming (spoken by Auric Goldfinger)


to another file to be read by my email client.

Does anyone know if this code already exist and what name I can search for?
Any suggestions, help, insight would be appreciated.
Dave

---

### Post by Paddy Landau on 2012-04-05
Try this:
[https://addons.mozilla.org/thunderbird/addon/randomsignature/](https://addons.mozilla.org/thunderbird/addon/randomsignature/)

---

### Post by mike555 on 2012-04-05
In Thunderbird I use "QuickText" add-on .

---

### Post by Silvernail on 2012-04-05
Ubuntu Oneiric Ocelot
Gnome 3
Thunderbird 11.0.1
fortune-mod version 9708[COLOR="#ff0000"][/COLOR]

UNCLE!!!!!
Your mention of 'Fortune Cookie' jarred some old memories.  I remembered that 'sigrot' was based on the fortune cookie apt. I found that I had already downloaded it in my search. So I revisited it and have it working almost as I wish.  Thanks for suggesting this.

I want 'fortune' to read my own list of signatures. 

If I copy my list to one of the existing names, 'fortune' dumps everything to standard out.

It appears that I need a 'fortune.dat' file. How do I create that. [COLOR="#ff0000"]<-- Ignore this request. As usual I ask before I quit looking.  Found oodles of soulutions.[/COLOR]

---

### Post by Silvernail on 2012-04-05
Mike, I'll look into 'Quick Text'.  Thanks for the suggestion.
D

---

### Post by Silvernail on 2012-04-06
OK, I finally figured out how to use 'sed' to insert a '%' between each signature as required by the 'fortune' code.

Now.
Trying to create a 'fortune.dat' file.
As per instructions here. [http://bradthemad.org/tech/notes/fortune_makefile.php](http://bradthemad.org/tech/notes/fortune_makefile.php)

I used this Makefile.
```

POSSIBLE += $(shell ls -1 | egrep -v '\.dat|README|Makefile' | sed -e 's/$$/.dat/g')

all: ${POSSIBLE}

%.dat : %
        @strfile $< $@

```
I get this error when I run 'make'.
> 
dave@dave:~/LIST/work$ make
Makefile:6: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.
dave@dave:~/LIST/work$ 

I assumed that it was the indentation before 'strfile', so I changed it to a tab. Same error message.

I'm bumfuzzled.

---

