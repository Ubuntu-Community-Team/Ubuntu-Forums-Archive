---
title: "GPL licence and restricted codecs - how do I know, what I can use ?"
date: 2009-07-20
forum: General Help
---

### Post by credobyte on 2009-07-20
Let's start with the fact that I'm from Latvia ( and this fact will play the main role in my question ) and GPL licensing isn't a big problem ( translation is the one and only "turtle" ), but .. I can't find anything about restricted codecs.
As far as I know, in USA, there are a few restrictions regarding the use of these codec packs ( correct me if I'm wrong .. that's just the info I've found so far ) and I want to know, is there any restrictions in my country as well ? A quick note would be - currently I can't find a single line about these codecs and GPL exceptions ( I assume they are released under GPL license ? ).

Is there a way to find out, what I can/can't use without being scared about legal aspects ? Laws are different, tough, the idea should be the same, isn't it ?

Any ideas/suggestions/documents ?

---

### Post by mikewhatever on 2009-07-20
The restricted codecs are not released under GPL, in fact, had it been the case, they wouldn't be restricted in the first place. You need to check the issue against the Latvian law which is easier said then done. 
It's generally accepted that EU users are not restricted in using the these codecs, and I would assume it also applies to Latvia.

---

### Post by niteshifter on 2009-07-20
Hi,

Keeping in mind I am not a lawyer, and certainly not one expert in international law, google gave me this: [http://portal.unesco.org/culture/en/files/30288/11419166023lv_copyright_2004_en.pdf/lv_copyright_2004_en.pdf](http://portal.unesco.org/culture/en/files/30288/11419166023lv_copyright_2004_en.pdf/lv_copyright_2004_en.pdf)

In which I find an interesting thing (from a USA perpective) - Section 30
which begins with this text:
> (1) The permission of the holder of a copyright shall not be required, if, without reproducing the
code of the computer program or modifying its form, it is not possible to obtain the necessary
information in order to achieve the interoperability of an independently created computer program
with other computer programs.

I wish we (USA) had that. So I tend to think you're ok to use the restricted codecs. Better advice: Get with a lawyer / law student in Latvia and ask them.

---

### Post by credobyte on 2009-07-20
Thank you guys - at least some ideas are clear now :) Regarding laws in Latvia, the problem is that, I have went trough all the documents ( related to open source software and related licenses ) and found nothing related to stuff that doesn't come embedded ( which I install manually after setting up Ubuntu ).
There are a few documents describing that I can use GPL licenses in any way I want, however, as mikewhatever said, some of these packages are not released under GPL ( I'm just quoting him .. I'm not 100% sure about this fact, which was the reason why I started this thread ). 
If they are not released under GPL, what licenses I should look for ?

---

### Post by CatKiller on 2009-07-20
The problem with codecs is that certain countries have decided that it would be a good thing if people could patent mathematics. The USA is one of these, but there are others that recognise software patents. In those countries it is illegal to distribute the mathematics that some companies have decided belong to them, and so Canonical cannot do so. In other countries you can have all the mathematics you can eat. If you live in a country that has patented mathematics you cannot legally use the mathematics that's included in those codecs without paying a tithe to the patent holder. If you live in a sane country you can use any mathematics you can find, to your heart's content.

The other situation is where there is software (such as the Flash plugin) that is free to use, but is not Free. Canonical are prevented, by the license that covers the use of that software (under copyright law), from redistributing that software. In those cases you are provided with a script that will retrieve the software from the people that made it. In the case of Flash you will download the software (automatically) from Adobe's servers. In the case of Sun's Java you will download the software from Sun's servers. And so on. These pieces of software may come with additional licensing restrictions.

The third class of restriction is Trademarks. For example, you cannot modify Firefox to do what you want it to do and then re-distribute that as "Firefox" in a way that would imply that your modified version came from them. You would have to call it something else. Like Ice Weasel.

There a number of licenses that cover Free or open-source packages that are included with Ubuntu. Where the line is drawn between packages that are Free and packages that are open-source is the subject of much heated debate. Common examples of licences that are used are the GPL, the LGPL, the BSD licence, the Apache Licence, the Mozilla Public License, and so on. There is usually a document included with the package that states what licence it is provided under.

---

### Post by earthpigg on 2009-07-20
dude, you are fine.

as far as i know, not a single American has been prosecuted for installing ubuntu-restricted-extras ---- and the US is _*less*_ friendly towards this stuff (intellectual property, etc) than the EU.

i would be jaw-droppingly shocked and surprised if the first prosecution of a private citizen for using happened in the EU. this isn't piracy we are discussing -- this is like taking a *_photograph_* of a _*music CD.*_


why would Adobe go after you for using flash? the more people that use flash, the more money they make! :D

---

### Post by mikewhatever on 2009-07-20
The important thing to understand is that ALL of the restricted codecs have nothing to do with GPL, which is why they are called restricted. If you are concerned about licensing, for whatever reasons, perhaps you should check out [Canonical Store page.]("http://shop.canonical.com/index.php?cPath=19&osCsid=bae27c48373139cf2c344f3cb6faf616")
As for the actual license texts, check out the following:
[http://www.fluendo.com/shop/product/fluendo-dvd-player/](http://www.fluendo.com/shop/product/fluendo-dvd-player/)
[http://www.fluendo.com/shop/product/fluendo-mp3-decoder/](http://www.fluendo.com/shop/product/fluendo-mp3-decoder/)
[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/faq/html/chapter-legal.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/faq/html/chapter-legal.html)

---

### Post by CatKiller on 2009-07-20
The chances of getting caught aren't necessarily the only factor to consider when doing something illegal, you know :)

> **earthpigg said:**
> the US is _*less*_ friendly towards this stuff (intellectual property, etc) than the EU.

Actually the EU is ambiguous on the matter. The individual member states have a broad spectrum of laws on the matter, and since the proposal to harmonise these laws across the whole of the EU was being lobbied heavily by the large media companies the only plan that they put forward was "maximum protection for everything." The patent issue has been (temporarily) put down since the EU Parliament rejected the proposal, although the Commission said they are waiting for a more compliant Parliament.

They still voted in a retroactive theft of the commons on copyright, though.

I don't know how trademark law compares between the two.

---

### Post by credobyte on 2009-07-20
Ok, quoting everyones message would lead into something unreadable, so .. I'm just going to thank you all for your support ( I've got quite a few research targets for the next few days ) :)
Regarding the fact that EU is a friendly place in the meaning of copyright/trademark acts, you should take a look at this post ( wasn't able to find an alternative source in english ) : [http://ukucis.com/2009/03/18/youtube-embeds-considered-illegal-in-latvia/](http://ukucis.com/2009/03/18/youtube-embeds-considered-illegal-in-latvia/). I hope it'll give at least some introduction on what's currently going on here :D

---

