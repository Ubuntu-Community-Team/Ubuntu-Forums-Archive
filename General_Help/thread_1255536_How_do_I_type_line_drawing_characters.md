---
title: "How do I type line drawing characters?"
date: 2009-09-01
forum: General Help
---

### Post by foxmajik on 2009-09-01
Hello,

This is another "in windows..." post.

I searched Google but could not find an answer.

In Windows if I want line drawing characters I can hold Alt and type xxx on the numpad to get them.

For example, Alt+178 is the 75% block character.

I can't find a way to type them in Ubuntu.

How I done did that up in this?

---

### Post by imhotep_ on 2009-09-01
> **foxmajik said:**
> 

 How I done did that up in this?

well son, you need to buckle up and RTFM.

no, seriously, depends on where you want to write those characters.

[http://www.linuxquestions.org/questions/programming-9/bash-printing-extended-ascii-characters-286242/](http://www.linuxquestions.org/questions/programming-9/bash-printing-extended-ascii-characters-286242/)
[URL="http://tldp.org/LDP/abs/html/wrapper.html"]
http://tldp.org/LDP/abs/html/wrapper.html[/URL]

etc and so on and so forth ...

---

### Post by StuartN on 2009-09-01
You can access all characters and enter them (character-by-character) from Applications->Accessories->Character Map.

Behaviour similar to the Windows use of the Alt-Gr key can be enabled from System->Preferences->Keyboard, under Other Options on the Layout tab. Select a key for Compose and then you can type á by pressing the compose key, then the ' and then the a (not Alt-Gr and a simultaneously as in Windows). I don't know what range of characters can be obtained this way.

---

### Post by StuartN on 2009-09-01
I have just fiddled with some alternatives (my own need is the simple one of adding accents, and is easily solved). Type ctrl+shift+u, then release the u while continuing to hold the ctrl+shift and type the Unicode value for the character - e.g. c6 (or 00c6) gives the A-E ligature Æ and 2588 gives the 100% box &#9608;.

See [http://en.wikipedia.org/wiki/Box_drawing_characters](http://en.wikipedia.org/wiki/Box_drawing_characters) for box-drawing Unicode.

---

### Post by foxmajik on 2009-09-01
> **imhotep_ said:**
> well son, you need to buckle up and RTFM.

You must be from debian-user.

Welcome to Ubuntu forums.

Here, when someone asks a question it's not a requirement for them to tell you each of the steps they went through trying to find the answer before posting the question.

In general, we assume that people are fairly intelligent and that if they're asking a question they'd like your help answering the question and that helping them to feel like an idiot is neither productive nor expected.

So please, for your future replies, either answer the question or do not.

And welcome to Ubuntu forums.  =)

---

### Post by foxmajik on 2009-09-01
> **StuartN said:**
> You can access all characters and enter them (character-by-character) from Applications->Accessories->Character Map.

Behaviour similar to the Windows use of the Alt-Gr key can be enabled from System->Preferences->Keyboard, under Other Options on the Layout tab. Select a key for Compose and then you can type á by pressing the compose key, then the ' and then the a (not Alt-Gr and a simultaneously as in Windows). I don't know what range of characters can be obtained this way.

I should have stated that I need to do this on an American keyboard with a 101-key QWERTY layout.

I do not have a Gr key.

---

### Post by foxmajik on 2009-09-01
> **StuartN said:**
> You can access all characters and enter them (character-by-character) from Applications->Accessories->Character Map.

Behaviour similar to the Windows use of the Alt-Gr key can be enabled from System->Preferences->Keyboard, under Other Options on the Layout tab. Select a key for Compose and then you can type á by pressing the compose key, then the ' and then the a (not Alt-Gr and a simultaneously as in Windows). I don't know what range of characters can be obtained this way.

All of the line drawing characters show up as boxes with letters and numbers in them rather than the actual character in the character map.

It doesn't seem to matter which font I pick, so I'm somewhat confident it's not because the font doesn't support that character.

When I copy and paste them they show up as tiny boxes with tiny numbers and letters in them.

---

### Post by StuartN on 2009-09-03
> **foxmajik said:**
> It doesn't seem to matter which font I pick, so I'm somewhat confident it's not because the font doesn't support that character.

Without any alterations to the default configuration I can type ctrl-shift u259f and get correct the Unicode box character &#9631;. I found a Unicode list at [http://en.wikipedia.org/wiki/Box_drawing_characters](http://en.wikipedia.org/wiki/Box_drawing_characters). Does this code work for you, and what codes are failing to work?

The European AltGr key might be the same as the Right Alt key. However, Linux allows you to select a compose key from a number of different keys. Incidentally I think that the US International setting gives you access to a wide variety of additional accented characters.

---

