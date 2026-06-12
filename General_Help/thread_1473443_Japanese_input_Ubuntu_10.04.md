---
title: "Japanese input Ubuntu 10.04"
date: 2010-05-05
forum: General Help
---

### Post by Varout on 2010-05-05
I've searched the forums for help on this and found many pages that haven't solved my problem.

I would like to use Japanese kana (hiragana, katakana, kanji) on Ubuntu but everything that I've tried to get it set up and running isn't working.  The Spanish that I have set up is working perfectly so far.

According to previous threads that I've read, the SCIM input program should start up automatically when loading a program, it doesn't.  When I have it loaded I cannot seem to get the input working.  There seems to be some form of setup needed for it.  I don't understand what needs to be done.

Help to get this working would be greatly appreciated.  If any screenshots are needed I should be able to get them uploaded.

Cheers

---

### Post by zaphod777 on 2010-05-05
you need to go to system->administration->language support

then install the Japanese.

Next go to system -> preferences -> ibus 

and configure your preferences.

then under preferences add "ibus-daemon --xim" to your startup programs. 

It should work like a charm then.

---

### Post by clubsoda on 2010-05-06
I just wanted to add an alternative solution to fix a broken **scim** where the toolbar refuses to appear, even though the daemon is running.

As zaphod777 has suggested, first get the language/locale settings sorted out. 

Then create or edit the following file:-
**/etc/X11/Xsession.d/74custom-scim_startup**```
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"
```and sudo chmod 644 that file.

At least, the above worked for me.

Cheers.

---

### Post by Varout on 2010-05-06
@zaphod777
I can't get it working still.  Thanks for your quick reply.  Here are some screen shots of how I have things set up.

[IMG]http://i173.photobucket.com/albums/w48/Varout/Ubuntu/JPInst1.jpg[/IMG]

[IMG]http://i173.photobucket.com/albums/w48/Varout/Ubuntu/JPInst2.png[/IMG]

Does this look right?
I've added  "ibus-daemon --xim" to the start up and it's running on start up.

@clubsoda
Just saw your post, will give it a go now.

Cheers

*edit*
I've noticed that there's this strange little gray box on the bottom right hand side of my screen that does absolutely nothing.  However if i hover the mouse of the right hand side of it text comes up "Switch input method".  No form of clicking on it will do anything.  I can move it around the screen, but that's all.

[IMG]http://i173.photobucket.com/albums/w48/Varout/Ubuntu/JPInst3-1.png[/IMG]

@clubsoda
Gave it a go, no joy.
Just to clarify what I needed to with that code... this is what I did in a terminal:

sudo gedit /etc/X11/Xsession.d/74custom-scim_startup

Put in the code:
> export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"Saved

sudo chmod 644  /etc/X11/Xsession.d/74custom-scim_startup

and then restarted my laptop.


I was just having a few smaller problems with the Spanish layout, but it's working fine now.

---

### Post by zaphod777 on 2010-05-06
You need to go to System-> Administration -> Language Support and make sure you install the Japanese characters. 

[IMG]http://lh4.ggpht.com/_sjlVRfKJcmw/S-FcwBpqyBI/AAAAAAAABBA/TkmMJUsaa1w/s800/Screenshot-Language%20%26%20Text.png[/IMG]

Also I like Anthy better for the Japanese input 

[IMG]http://lh4.ggpht.com/_sjlVRfKJcmw/S-Fcvj_kssI/AAAAAAAABA4/AQH0Rv1JzLY/s800/Screenshot-IBus%20Preferences.png[/IMG]

---

### Post by Varout on 2010-05-06
Working!!
Thank you both for your help!! =)

&#12354;&#12426;&#12364;&#12362;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#65281;&#65281;

This is fantastic, I can't wait to practice more with it.
I had SCIM installed... I removed it and restarted and then things started working.
Anthy is the same as what seems to be used on Windows and works as I'm use to.

Again, thank you both =)

Now back to the study...

---

### Post by zaphod777 on 2010-05-06
&#12424;&#12363;&#12387;&#12383;&#65281;:d

---

### Post by simosx on 2010-05-06
In Ubuntu 10.04, SCIM is replaced with IBus.
Therefore, it is important not to mix up SCIM packages and learn the new IBus way :-).

---

### Post by clubsoda on 2010-05-07
&#12381;&#12358;&#12363;&#12290;&#30693;&#12426;&#12414;&#12379;&#12435;&#12391;&#12375;&#12383;&#12290;
&#12391;&#12399;&#12289;&#20170;&#22238;&#12399;&#21021;&#12417;&#12390;&#12398;ibus-anthy&#12391;&#8230;

We'd better edit the conversion table for anthy though.
cyu -> &#12385;&#12421; is missing, maybe others too.

[link1]("http://blogs.yahoo.co.jp/rmnjr654/31787487.html")
[link2]("http://pinklion.jp/?p=12824")

---

### Post by zaphod777 on 2010-05-07
&#12381;&#12358; &#12391;&#12377;&#12363;&#65311; &#12385;&#12421;&#12358;&#12364;&#26360;&#12369;&#12414;&#12377;&#12290;

really I just wrote it with no problems.

&#12385;&#12421;&#12358; = chuu

---

### Post by Rounin on 2010-05-16
"Cyu" probably isn't part of any official standard. However, "chu" and "tyu" both work just fine.

---

### Post by olifhar on 2010-05-25
The other day, Japanese Input with Anthy mysteriously stopped working--more precisely, when I hit <C-space>, which is set to bring up the input method bar, nothing appears. I'm worried it had to do with some settings I changed in Anthy, but I've tried purging ~/.anthy and purging/reinstalling a bunch of stuff as per [this thread]("http://ubuntuforums.org/showthread.php?t=1473389") (ibus, anthy and everything in-between) to no avail.

ibus-daemon is running with the --xim option.

If this provides a clue: I do notice that when I hit <C-space>, input does "hang" momentarily--I wonder if it's trying to start something and failing. This is just one interpretation; I don't know what's really happening at all.

I'd been using Japanese input since 6.10, and in 9.10 all was fine. I'm somewhat concerned it's because I recently started using xmonad--but that's in a separate session and it was working fine there for about a month!

Hopefully I can get this to work without having to go through a fresh install...

Anyway, here are screenshots which should verify that I have all the language support options installed and blah blah blah. Any ideas?

[IMG]http://posterous.com/getfile/files.posterous.com/olimay/y2xtzoHf5V3NHvutqEtodV0uKNj6AjaJp3GOPBfnhna95sPCUV466LJheURG/ibus_preferences.png[/IMG]

[IMG]http://posterous.com/getfile/files.posterous.com/olimay/PVkRwu9IHdJ9jk3p7EpvaqLp1Sx228blJNi5sd5FVqErIUros1ZSyAYdcXWY/ibus_preferences2.png[/IMG]

[IMG]http://posterous.com/getfile/files.posterous.com/olimay/q44ZGyfxRKT4ZGA7NzMnHFqD6npIcCOZBIVz6iLnmX3zEHolSZ3wLCNZ3Rro/ibus_preferences_advanced.png[/IMG]

[IMG]http://posterous.com/getfile/files.posterous.com/olimay/SMfYBD5u6SRd3mZqTtfmLpH8h3ZYRa1zfplVuQ2mJn1BYVASoKu0j1e2auXA/installed_languages.png[/IMG]

[IMG]http://posterous.com/getfile/files.posterous.com/olimay/X3W8hZydtV6xeoewmHLwLOLWuOzN50FRV1n2sbNCQrgg4NfKMw9KHv2uCIzZ/language_and_text.png[/IMG]

[IMG]http://posterous.com/getfile/files.posterous.com/olimay/VfTGUyA5jkQXnOPXfLNdfWPP4cemfBdTWrF1MB6slLpXqBqrum1BXbVT2nKh/startup_ibus_daemon.png[/IMG]

(just in case images decide to be fickle, they're cross-posted on my Posterous:

[http://olimay.posterous.com/having-some-issues-with-japanese-input-and-ib]("http://olimay.posterous.com/having-some-issues-with-japanese-input-and-ib"))

---

### Post by clubsoda on 2010-05-26
> **Rounin said:**
> "Cyu" probably isn't part of any official standard.Looks like you win on a technicality because the Japanese Industrial Standards Committee withdrew JIS X 4063:2000 sometime in the last few months(!) Apparently there's less diversity in character conversion systems these days so the document is no longer in demand. Type x4063 as a search term at [&#26085;&#26412;&#24037;&#26989;&#27161;&#28310;&#35519;&#26619;&#20250;'s junked documents page](http://www.jisc.go.jp/app/JPS/JPSO0080.html) if you want to check it out. Cyu appears in the non-essential but desirable category.

[ATOK7](http://docs.sun.com/app/docs/doc/805-4182/6j3vf1te7?l=zh&a=view) had it in 1989.

Hey, I'm with you and zaphod777 about "chu" but slide your keyboard under the palms of a native typist and start your stopwatch for the first &#12300;&#12360;?&#12301;.


Olifhar, could your issue be related to [this bug](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/522814)?

---

### Post by olifhar on 2010-05-28
@clubsoda:

I don't think that's it: my locale is set to Japanese; ALL is nowhere to be seen. Here's my locale output:
```
~$ locale
LANG=ja_JP.utf8
LANGUAGE=en_US:en
LC_CTYPE="ja_JP.utf8"
LC_NUMERIC="ja_JP.utf8"
LC_TIME="ja_JP.utf8"
LC_COLLATE="ja_JP.utf8"
LC_MONETARY="ja_JP.utf8"
LC_MESSAGES="ja_JP.utf8"
LC_PAPER="ja_JP.utf8"
LC_NAME="ja_JP.utf8"
LC_ADDRESS="ja_JP.utf8"
LC_TELEPHONE="ja_JP.utf8"
LC_MEASUREMENT="ja_JP.utf8"
LC_IDENTIFICATION="ja_JP.utf8"
LC_ALL=

```

I would still like to know what's going on, but right now I'm just not going to deal with iBus--going with UIM instead.

&#65327;&#65323;&#12381;&#12358;&#12384;&#12363;&#12425;…

&#20814;&#12395;&#35282;&#12289;&#12354;&#12366;&#12364;&#12392;&#12358;&#12290;

---

### Post by orengolan on 2010-06-12
since I use Lubuntu Lucid I don't think I can use the visual instructions on this thread. 
I would really like a step by step instructions (I would assume text-based) including all the packages I need and the way to switch between English and Japanese.

having Those instructions will be valuable for
xubuntu/lubuntu/kubuntu or any ubuntu-based distro.

Thanks!

---

### Post by mopreme on 2010-06-17
I created a step-by-step how to for setting up Japanese input in Ubuntu 10.04 Lucid Lynx. It is a complete tutorial of the steps from start to finish with pictures of each step.

Link: [Ubuntu Japanese input tutorial]("http://www.localizingjapan.com/blog/2010/06/15/setting-up-japanese-input-on-ubuntu-linux-10-04-lts-lucid-lynx/")

This was done on fresh install of Ubuntu 10.04.
Following the steps outlined will get you set up with Ibus Anthy for Japanese input.

---

### Post by orengolan on 2010-06-17
awesome!

---

### Post by shannon.jacobs on 2010-06-28
Well, after another round of so-called upgrades that included some of the the Japanese input components, I thought it might have been fixed (only a couple of months after the so-called official release). Therefore I went ahead and tried again on yet another machine running a clean Lynx. (Upgrades to Lynx have been too damaging for me to risk another.) Still doesn't work, but now I have no interest in tinkering with it or with trying to fix things that WERE NOT BROKEN to start with.

I used to be a supporter of Ubuntu. I'm still using older version of Ubuntu on a couple of machines. Not perfect satisfaction, but good enough. However, I have long since stopped recommending Ubuntu to any new users, and my current attitude is just waiting for something else. I already regard as wasted the many hours I spent studying how to work with Ubuntu. The great new hope is probably Google's Chrome--but it's a shrinking hope...

Here's a new idea for the Ubuntu people. It's called regression testing. Oh, you say it isn't a new idea? Certainly seems to be as regards the Ubuntu staff.

Even though I've given up on Ubuntu (obviously in anger and frustration at the lost hope), I feel obliged to try to close on a constructive note. I think the root of the problems is that Ubuntu's financial model is broken. It puts new features ahead of testing, and especially ignores regression testing. Therefore I suggest an alternative funding model to help insure that things which are NOT broken don't BECOME broken.

[http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html](http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html)

---

### Post by Bafflebox on 2010-07-14
&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12375;&#12383;&#65374;
it works like a charm ^_^

---

### Post by zaphod777 on 2010-07-14
> **shannon.jacobs said:**
> Well, after another round of so-called upgrades that included some of the the Japanese input components, I thought it might have been fixed (only a couple of months after the so-called official release). Therefore I went ahead and tried again on yet another machine running a clean Lynx. (Upgrades to Lynx have been too damaging for me to risk another.) Still doesn't work, but now I have no interest in tinkering with it or with trying to fix things that WERE NOT BROKEN to start with.

I used to be a supporter of Ubuntu. I'm still using older version of Ubuntu on a couple of machines. Not perfect satisfaction, but good enough. However, I have long since stopped recommending Ubuntu to any new users, and my current attitude is just waiting for something else. I already regard as wasted the many hours I spent studying how to work with Ubuntu. The great new hope is probably Google's Chrome--but it's a shrinking hope...

Here's a new idea for the Ubuntu people. It's called regression testing. Oh, you say it isn't a new idea? Certainly seems to be as regards the Ubuntu staff.

Even though I've given up on Ubuntu (obviously in anger and frustration at the lost hope), I feel obliged to try to close on a constructive note. I think the root of the problems is that Ubuntu's financial model is broken. It puts new features ahead of testing, and especially ignores regression testing. Therefore I suggest an alternative funding model to help insure that things which are NOT broken don't BECOME broken.

[http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html](http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html)

Have you looked for support in these forums? I see you only have 11 beans I am not trying to be condescending but it looks like you have not asked for much help. Japanese input has worked fine for me since the betas of 10.04 as well as 9.04+ I never had to use it before that. Though they should make the configuration a little more seamless rather than a two step process. 

I have found that this last release is the best yet.

---

### Post by Numer0bis on 2010-07-15
Thank you all very much for all your help in this thread. After adding the iBus daemon to the StartUp application I finally got Japanese Input to work.
&#12393;&#12418;&#12358;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#12290;

---

### Post by Psychic Saw on 2010-08-07
This is awesome, shockingly easy.

---

### Post by TWEP191 on 2010-08-28
Hey all, I am new to the forums, but have been looking around to figure out how to get iBus to work. I followed the instructions here 
[HTML]http://www.localizingjapan.com/blog/2010/06/15/setting-up-japanese-input-on-ubuntu-linux-10-04-lts-lucid-lynx/[/HTML]
This did not work. I have gone through and installed the language pack for Japanese. I have added the startup process "/usr/bin/ibus-daemon -x". iBus is running because I see the keyboard in the task bar, but when i open gedit, OO.o, Firefox, etc. it will not let me choose an input method. It just shows "No input window". 
I have no idea what to do.

---

### Post by rustiguzzi on 2010-09-12
Can't say for sure, as I'm new to IBus too, but how about starting again and following this how-to:

[http://www.moritzmolch.de/2010/05/02/writing-japanese-with-ubuntu-10-04-lucid-lynx/](http://www.moritzmolch.de/2010/05/02/writing-japanese-with-ubuntu-10-04-lucid-lynx/)

In my case, I could get Japanese input but had trouble switching between it and romaji.  The breakthrough came when I took up the suggestion in this how-to of deleting the "ispell(m17n)" option from the input method tab in "ibus preferences".  

Roy

---

