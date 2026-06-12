---
title: "Japanese characters showing as if they were Chinese"
date: 2011-11-07
forum: General Help
---

### Post by Mezzoforte on 2011-11-07
I have installed support for both Chinese and Japanese on my Ubuntu 11.10 (at least according to the list in System Settings > Language Support > Install/Remove Languages). The problem is that when I view Japanese text either in a web browser or some local application (like Anki), it seems the system thinks it's actually (traditional, not simplified) Chinese text. Or actually, it seems displaying the characters in the Chinese style seems to have priority over the Japanese style. So if there is no similar Chinese character for a given Japanese character, the Japanese one is displayed, but in any other case it seems the Chinese one is displayed. In many cases they are very similar, but it's quite disturbing and increases the risk of mixing them up. It certainly won't do any good to my writing tests at university...

By the way, my girlfriend happens to be Chinese, so I think I have given the correct information although I don't speak much Chinese.

Here's an image showing what the characters look like on my computer:
[IMG]http://i42.tinypic.com/2556tm0.jpg[/IMG]

Look at the first character (the second character is not quite right either, for that matter). It should look something like this (a few different styles of the same character, but they are all fine):
[IMG]http://i42.tinypic.com/15fpxfc.jpg[/IMG]

---

### Post by Mezzoforte on 2011-12-11
I bet there are at least a few other people here speaking or studying Japanese. Have you never thought of this? I don't think the problem is specific to my computer...

---

### Post by Anuovis on 2011-12-18
Yes, this has been a problem with some Ubuntu versions. I have solved it twice now but still not sure what exactly causes this. The good news is that by installing and removing fonts you can get the desired result, at least with the Japanese characters. 

I found a few threads on this but they do not provide a clear answer for most of the part.

Maybe it can be done with the Software Center but I installed Synaptic (does not come with Ubuntu 11.10 any more) and filtered everything related with they keyword "jap". Then you can add or remove fonts as you wish and some good combination or maybe a removal of some defunct font solves this.

One way was to remove every Japanese-related font except these:

ttf-kochi-mincho-naga10
ttf-kochi-gothic-naga10
ttf-sazanami-gothic
ttf-sazanami-mincho

It worked. Another time I decided to install every font there was but got rid of ttf-wqy-microhei and ttf-wqy-zenhei because they looked to be related to the Chinese language.

I am still not sure which font causes this problem but it is obvious that the wrong one is used for some reason. Can not really tell more than this.

Once I tried removing every Japanese font there was but the system could still render a lot of characters (others were looking like boxes with numbers in them) which can also mean I did not remove something but I have no idea how to do so. By testing fonts one by one it would probably be possible to find the bad one.

It might also be that Ubuntu just picks the wrong font from the available ones. Some years ago that could be altered by writing a good the fonts.config file but the tutorials on that seem to be very outdated. Not sure if there is another way to toy with the default preferences.

However, in your case you probably need both Chinese and Japanese which complicates matters a bit. The solution I introduced here might not be a fix for you at all or solve just half the problem but it is worth trying nonetheless.

Please share if you find a simpler solution or a cause to this. It would certainly help a lot of users, right now people seem to be going the trial-and-error way until it works.

---

### Post by Mezzoforte on 2011-12-18
Anuovis: Thank you so much! With your hints I was able to work this out.

I had a different set of fonts installed to start with, those that you mentioned were not installed.

The following fonts were installed before I started tinkering:

ttf-arphic-ukai
ttf-arphic-uming
ttf-takao-gothic
ttf-takao-mincho
ttf-takao-pgothic

In addition, these two fonts were installed:

ttf-wqy-microhei
ttf-wqy-zenhei

These last two fonts seem to be aimed at displaying a few different languages (from the description of the first: "WenQuanYi Zen Hei is a Hei-Ti style (sans-serif type) Chinese font.
It was designed for general purpose text formatting and on-screen
display of Chinese characters among many other languages..."). It seems these two were the culprits - I uninstalled them and suddenly Japanese characters were showing properly. On the other hand, some Chinese characters would not show now, but then I realized I had uninstalled these too:

ttf-arphic-ukai
ttf-arphic-uming

I didn't realize these were Chinese fonts at first. I installed ttf-arphic-ukai again and now I can see both proper Japanese text and Chinese text.

Hope this will help more people with this problem!

By the way, I also used Synaptic to install and uninstall fonts, it's quite handy.

EDIT:
Today, when using a Japanese dictionary online, I realized the problem had come back.I went back to synaptic to check, and neither microhei nor zenhei was installed. I checked which other fonts I had installed, and found ttf-arphic-uming there. Tried uninstalling, and now my fonts seem all right again. And as far as I can see at the moment, I'm still able to view Chinese text properly. In conclusion, it's not only microhei and zenhei which are problematic - it's also ttf-arphic-uming.
EDIT 2: Oh no! It's not working. See later post.

---

### Post by Anuovis on 2011-12-19
Glad I could be of help. I was also suspicious of microhei and zenhei but did not find a way to really test it out. 

It seems there are bug reports in Launchpad about Korean and Chinese language problems caused by these. Hopefully it gets polished for future Ubuntus.

---

### Post by Mezzoforte on 2012-01-03
Note my last edit - ttf-arphic-uming also seems to cause the problem.

Tried uninstalling fonts to get it to work, but there was still something shoddy going on. Maybe it's not only a problem with previously mentioned fonts - it might be that some Japanese fonts are incomplete and somehow then "covered" by Chinese fonts. I don't know anything about the inner workings of fonts though.

Anyway, I have temporarily given up on having both Chinese and Japanese fonts working properly. I've got Japanese working (I think - will report back if something turns out to be wrong again) with the current font set:

ttf-takao-gothic
ttf-takao-mincho
ttf-takao-pgothic
ttf-sazanami-gothic
ttf-sazanami-mincho

---

