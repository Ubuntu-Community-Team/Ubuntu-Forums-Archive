---
title: "Thorough Chinese input primer for Karmic?"
date: 2010-01-27
forum: General Help
---

### Post by davidjbell on 2010-01-27
I'm looking for a current primer on the options for Chinese input available for Karmic (9.10).  I'm new to Linux, but have been using Chinese input method editors for Windows and Mac for some time.  I found some info in these forums, but most of it is several years old.

Some specific questions:
1) I have enabled Chinese input through system>administration>language support, but it seems there is no option for traditional Chinese input via Pinyin, only through some of the other methods, like &#20489;&#38945;.

2) I take is IBus is a general name for Asian language input in Linux, but I don't quite understand if it's the only option out there.  Also, did it replace SCIM?

3) This being open source, I'm guessing there are tons of input method editors out there to try.  Is there some sort of repository I can search.

Thanks!

---

### Post by Zorael on 2010-01-27
I can't answer any GNOME-specific questions, as it's been a while since I used it.

SCIM is supposedly dead or inactive upstream, so the idea is to move to a healthier alternative. As such, as far as I'm aware SCIM is replaced by IBus in Ubuntu Karmic. Kubuntu still doesn't use any specific input method engine (IME).

Your alternatives are basically SCIM (which still works for the time being), IBus or UIM. IBus integrates poorly in KDE so I use UIM, which also offers slightly more features.

As for changing input modes, you should get a tray icon pop up at the start of the IBus daemon upon login. And at least with the Anthy backend (for Japanese input), when you enable it you'll get a toolbar with which you can control input modes, etc. (See attached image; that's the IBus toolbar.)

You can force it to restart by doing the following in a terminal. I'm not sure it'll help, though.
```
$ killall ibus-daemon
$ ibus-daemon -xd
```

---

### Post by davidjbell on 2010-01-27
OK, thanks!  After a little reading, it seems like trying out UIM in place of IBus might be a good next step.  I guess you could say that the things I'm missing with IBus might be considered missing features.

Now, can you (or anyone) tell me how I can get UIM?  I remember when I enabled Chinese language support initially, there was only IBus as a choice, so I'm guessing I have to get and install it myself.  VERY detailed instructions would be greatly appreciated, as I am very much a Linux nubie, and so far, I've found installing new software to be by far the most mystifying aspect of the Linux experience.  I don't mind working with the terminal, and I'm eager to learn, but at this point I have very little experience.  Thanks!

---

### Post by Ordes on 2010-01-27
I never liked UIM, and i worte a lot in chinese when i was studying there.
Before i always used SCIM, now only iBUS.

iBUS does supprt PinYIn, besides its character-word-recognition is far better than scim...
Beside PinYIn iBUS has 10 other input features like bofomo, wu bi etc...

U set it up in system > preferences > ibus ? input method > chinese 

!! there is one called py-pinyin, which is not pinyin to character, but pin yin to pin yin..

pretty much at the bottom of the list is &#25340; pinyin, thats the one u want when writing pinyin to character...

---

### Post by davidjbell on 2010-01-27
Ordes,

I have iBus enabled now, and I see that there are a few different types of pinyin, but I didn't like any of them.  I tried PinYin, but I can't get used to NOT typing in the tone number, and it seems like this isn't an option for this one.  &#25340; does allow this, but it doesn't let you input more than one character at a time, meaning that for every compound word you have to choose each character one at a time... very slow going.  So I was really hoping for a pinyin input that fits thes two requirements, and most importantly, does traditional characters.  I didn't see that in the options for PinYin either.  The windows IME lets you choose simplified or traditional for the same pinyin method.  OS X has different ones, but the traditional lets you both type tone numbers and input multiple characters before selecting.

So I'm just looking for more info on IME's for Ubuntu Linix.  For OS X, there's a cool site called "[Chinese Mac]("http://www.yale.edu/chinesemac/index.html")" over at Yale U.; does any one know of anything similar for Linix?

---

### Post by Zorael on 2010-01-27
If you do get the panel/toolbar to spawn, check it for any Configuration buttons. Perhaps the missing features you're looking for are in there. For instance, Anthy (again, Japanese), cannot be configured via IBus's options dialog - but if you enable Anthy with the keybinds, spawning the toolbar, you can then click Configure Anthy there and enter its settings. Perhaps there's similar functionality in the pinyin module.

----------

To try UIM, you'd need to install the **uim** package, as well as **uim-pinyin** for the pinyin module. You will also need the **uim-qt** package to get it to work in Qt4/KDE4 apps, and **uim-qt3** if you still have any Qt3/KDE3 apps (largely none by now, unless you're using Amarok 1.4).

Once installed, run the following command in a terminal to make UIM the default for your user. (Omit the **$**; that's just convention to show it's a terminal command.)
```
$ im-switch -s uim-toolbar
```

Unlike IBus, the UIM toolbar needs to be started separately from its service (daemon), but that **uim-toolbar** input method chocie will start the toolbar twenty seconds after login. Hopefully that's long enough to not slow down the login process, and short enough that it's there when you need it. Another way is to change **uim-toolbar** to just **uim** and make a normal autostart entry to start it. The executable is at **/usr/bin/uim-toolbar-gtk**.

It's very easy to change back to IBus if you don't like UIM - they can both be installed alongside eachother, but only one can be the default. Just enter the following in a terminal to get to the menu where you can set it to what you want. After that, just log out and back in to have it take effect.
```
$ im-switch -c
```

If something's not working (toolbar not starting, input doesn't work in certain type of apps, etc), we'll need the output of the following four commands to start digging for the cause. Put it inbetween code tags to make it readable.
```
$ echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS
$ im-switch -l
$ echo -e "user setting:\n---"; cat /etc/X11/xinit/xinput.d/$(im-switch -l | grep supersedes -B 1 | grep -v supersedes)
$ echo -e "system setting:\n---"; cat /etc/X11/xinit/xinput.d/$(im-switch -l | grep "system wide default" -A2 | grep "link currently points to" | awk '{ print $5 }')
```

Don't worry about the third and fourth commands being unintelligible; they're harmless. They just parse the output of '**im-switch -l**' and tries to find what your system-wide and user-specific settings point to, and outputs the contents of those settings file.

---

### Post by Ordes on 2010-01-27
&#20013;&#22269;&#33756;&#24456;&#26834;

nah.. u can type more than 1 character... e.g the sentence above i wrote without choosing anything, no tones, no space, no choosing characters, just inputing the pinyin. the word recognition is pretty good in ibus.. u can use tones, but this just makes it slow as anything, chinese never use tones..the input system should figure out your meaning from the context...

look at the preferences of language bar (show up when u type) u can adjust pretty much anything in there... most of my sentences start and end with using the space bar once....no choosing in between...

and yes.. u can input traditional chinese character.. just have to download the character set for traditional chinese (language support)  and add it in ibus...

---

### Post by davidjbell on 2010-01-27
Ordes,

Yep, I can see you can type more than one character in PinYin.  But I don't see how you can input tones numbers.  When I type zhong1, it just gives me the first zhong in the list.  What I want is for it to limit my choices to first tone zhong's.  Using tones may not be that nessesary for &#30333;&#35441;&#25991; or once you've input a significant amoutn of text, but i type a lot of &#25991;&#35328;&#25991;, and find that accuracy is much higher if I type tone numbers.  And yes, lots of Chinese type their tones.  I lived in Taipei for over seven years now, and everyone I know that uses phonetical ime's do (namely bopomofu).

So you have to download the traditional character set?  OK, great.  Help please?  Sorry, just getting started with Linux:)  Is this something I can do with apt-get?

---

### Post by Ordes on 2010-01-27
mhm.. perhaps they write different in taipei than in mainland.. i am living here for 15 years now... and went through a lot of ancient classic through my studies, like &#40644;&#24093;&#20869;&#32463; (which came out just like that, without choosing ;&#65289; &#65289;&#65292; and the chinese i know never use tones...too &#40635;&#28902;

however...
&#25340;pinyin is just typed pinyin, no tones, at least nothing that i know of, perhaps its also somewhere in the settings

TonePY is the input method if u want to use pinyin and tones.. u can also type multiple characters in a row...

bopomofu, is also in iBUS, but that is no pinyin with tones.. its a complete different phonetic system...thats probably why they use tones, cuz in bopomofo using tones is essential.. but not in normal output pinyin....

i know whenu go trhough classics, it might not be always the first choice in the list.. but it narrows down pretty fast as its learning from your choices..

>> system >> admin >> language support for trad chin...

---

### Post by davidjbell on 2010-01-27
Zorael,

Ok, Thanks!  Hmmmm... seem to have done something wrong.  In a terminal, I typed:

$ sudo get-apt install uim

a bunch of stuff seemed to have been installed.
then

$ sudo get-apt install uim-qt

again a bunch of stuff happened...
then

$ im-switch -s uim-toolbar

The terminal says: 

"Error: no configuration file 'uim-toolbar' exists.
Error: no action taken."

Can you tell me what I did wrong?

---

### Post by davidjbell on 2010-01-27
> **Ordes said:**
> mhm.. perhaps they write different in taipei than in mainland.. i am living here for 15 years now... and went through a lot of ancient classic through my studies, like &#40644;&#24093;&#20869;&#32463; (which came out just like that, without choosing ;&#65289; &#65289;&#65292; and the chinese i know never use tones...too &#40635;&#28902;

Well, for a test, I typed the first line of the preface to Sima Qian's Shi Ji (&#21490;&#35352;&#65289;, which is as follows (correct version):                 [FONT=&#26032] &#26132;&#22312;&#38995;&#38922;&#65292;&#21629;&#21335;&#27491;&#37325;&#20197;&#21496;&#22825;&#65292;&#21271;&#27491;&#40654;&#20197;&#21496;&#22320;&#12290;

Using IBus's PinYin IME, I got this: &#31995;&#22312;&#38995;&#38922;&#65292;&#26126;&#21335;&#24449;&#20013;&#37291;&#22235;&#22825;&#65292;&#34987;&#25972;&#30410;&#27515;&#22320;&#12290;

So that's 6 correct out of 17 characters, or 35% accuracy.

As for the tonepy ime, you apparently can use tones, but not multiple characters and tones.  when I type tian1di4 and then hit space in OS X, I get a list of two possible matches, &#22825;&#22320; and &#22825;&#24093;.  I can choose one of these by hitting 1 or 2, or I can use backspace to choose a different tian1 and or a different di4.  The ime remembers this combination the next time I enter tian1di4.[/FONT]

---

### Post by Ordes on 2010-01-27
perhaps scim might sute u better

enable in language support..

---

### Post by Zorael on 2010-01-27
> **davidjbell said:**
> $ im-switch -s uim-toolbar

The terminal says: 

"Error: no configuration file 'uim-toolbar' exists.
Error: no action taken."

Can you tell me what I did wrong?
Perhaps it's not there in the version you're using. Just do '**im-switch -s uim**' then, or '**im-switch -c**' to get the menu to spawn, allowing you to pick the alternative you want.

You may need to create an autostart entry to get the toolbar to spawn if there isn't a uim-toolbar option. Upon having logged out and in, just run '**uim-toolbar-gtk**' from a run box (Alt+F2) to get it up.

---

### Post by Rounin on 2010-05-15
There are some input methods that might suit your needs.

For Traditional Chinese, there's ibus-chewing and scim-chewing, two smart(ish) input methods which allow entire phrases to be input at a time. Unlike ibus-pinyin, they require tones to be explicitly specified for each character.
The default settings should be modified to specify pinyin (hanyu), and not bopomofo, as the script to use for input. One might also want to specify whether to use the space bar as a selection key.

If you need to input Simplified Chinese, scim-pinyin could be used for that. Unlike ibus-pinyin, it allows tones to be used by altering the settings. However, the smart pinyin functionality in scim-pinyin is targeted solely at Simplified Chinese.

Thus, if you need to input both Traditional Chinese and Simplified Chinese with tones, perhaps using both scim-chewing and scim-pinyin would be the best choice.

---

### Post by davidjbell on 2010-05-15
Thanks, Rounin.  I'll give that a try.

---

