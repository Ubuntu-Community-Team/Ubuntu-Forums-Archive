---
title: "Stress Marks in Russian"
date: 2012-02-23
forum: General Help
---

### Post by RussianSoup on 2012-02-23
Hello all,
I'm currently in a situation where on a daily basis I find myself needing to write in Russian. I've been using the "Russia Phonetic" layout, and it's worked splendidly. However, for academic reasons I would like to be able to put stress marks in my text. Since Russians don't do this, there doesn't seem to be any support for marking stress on vowels. I know on the English layout you can use a compose key to put marks like this, but this doesn't seem to work with different layouts. Does anyone know of something I could set up so I can quickly and easily type stressed characters without having to copy/paste, use apostrophes, etc?

Thanks everyone
RussianSoup

---

### Post by grahammechanical on 2012-02-23
I do not use the compose key feature but I do use a Greek keyboard layout as well as an English keyboard. If the accented character exists in the font character set and you can get it when using the English keyboard layout, why not just switch layouts?

For Example, with my English extended keyboard layout switched to the Greek layout I get 

> &#962; &#952; &#953; &#959;

When I press the w u i o keys. But if I then switch to English layout and press the right alt key I get

> &#7811; ú í ó

and it is in the same document and even in the same word if I chose.

When I use Libreoffice I use the Insert Special Character under the Libreoffice Insert menu to put in accented characters of any language if that character is part of the font set that I am using. I suppose that I could use a Compose key combination but I have been too lazy to work it out.

For example: &#333; &#275; are part of the Latin extended - A section of the FreeSerif font character set. 

Regards.

P.S. I found this link for you:

[http://askubuntu.com/questions/30334/what-application-indicators-are-available?page=1&tab=votes#tab-top]("http://askubuntu.com/questions/30334/what-application-indicators-are-available?page=1&tab=votes#tab-top")

Go down the list of app indicators until you come to Chars Indicator. I knew that something like this existed in Ubuntu version before 11.10 but all those old apps that could be put in the the panel have to be converted to work with Unity and it seems that this Chars Indicator applications has been converted.

I hope it helps.

---

### Post by RussianSoup on 2012-02-26
Hey thanks for the pointers,
Sorry I didn't make this clear above, because Russians don't use accent marks, the stressed characters aren't part of the standard character set. I've found program-specific ways to insert them in mainstream programs like word, but I'm looking for something quick and efficient I can use in other applications (in my case Mnemosyne). I'm just baffled that, with this many people globally having to type in multiple languages, there still doesn't seem to be a straightforward way to stick a stress mark on a non-latin character.

Thanks again,
RussianSoup

---

### Post by Pilot6 on 2012-02-26
I think there is the only one way to do it. It is to find a font where stressed Russian characters exist, if any.

---

### Post by LuK_green on 2012-05-31
Hello, RussianSoup.

I had the same question lately. Since you seem to be familiar with the Compose Key, you also might probably know there is a settings file for adding custom key combinations to the existing ones. It's called *.XCompose* and has to be placed in home directory. I added a line there for a support of a Russian stress mark. There were so many types of accents, graves etc., so I consulted Wikipedia on what mark is used in Russian typography. Here's the line:

```
<Multi_key> <apostrophe> <apostrophe> : "&#769;" U0301 # COMBINING ACUTE ACCENT
```

The stress sign is poorly seen in the line because it has become combined with the double-quote mark in it.

I forgot to mention that there is a predefined key combination for the U0301 sign in */usr/share/X11/locale/en_US.UTF-8/Compose*, which is:

```
<dead_acute> <nobreakspace>
```

but I couldn't figure out how it works. The dead acute works as the nobreakspace does, but together they don't produce the needed stress mark.

Hope this is helpful.

---

### Post by RussianSoup on 2012-05-31
Thank you! I created the .XConfig file and added the line you provided, it's exactly the solution I'd been looking for :) Worked like a charm.

---

