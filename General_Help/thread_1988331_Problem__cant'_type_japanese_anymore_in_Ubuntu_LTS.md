---
title: "Problem : cant' type japanese anymore in Ubuntu LTS 12.04"
date: 2012-05-27
forum: General Help
---

### Post by Aust on 2012-05-27
Hello everyone !

Since the upgrade from Ubuntu 11.10 Oneiric Ocelot to the Ubuntu LTS 12.04, I can't type in japanese anymore ! 

Ibus and Anthy are installed, and "Japanese - Anthy" is selected (black dot), but nothing happens. Everything worked perfectly with the previous version of Ubuntu. That's really strange. :(

I read millions of threads without finding any answer... Since I'm living in Japan, it's really a great problem for me if I can't type japanese. I'm starting to think I should change to windows... arghhghghghgh   ](*,)

Please, could someone help me ? I'm sure there is a lot of person in my case. I already check the japanese forum and for what I understood, it's a real mess since Precise Pangolin.
The better thing should probably be to show the way from scratch, without ibus nor anthy installed, so nobody won't commit any mistakes (wrong extensions or the like).

Thank you all for your kind assistance to the community  ! :wink:

Aust

---

### Post by AnesU on 2012-05-27
did u add the japanese language from keyboard layout sttings?

---

### Post by Aust on 2012-05-27
Yes I did that. I have two icons with a keyboard at the top of my screen. 


[LIST]
[*]The one for **Ibus **ie japanese or not: with
[LIST]
[LIST]
[*][SIZE=1]Japanese - Anthy[/SIZE]
[*][SIZE=1]Input method Off[/SIZE]
[*][SIZE=1]Preferences[/SIZE]
[*][SIZE=1]About[/SIZE]
[*][SIZE=1]Restart[/SIZE]
[*][SIZE=1]Quit[/SIZE]
[/LIST]
[/LIST]
[*]And the one for the** key[SIZE=2]bo[/SIZE]ard layout** ie azerty (I'm french) or qwerty keyboard with :
[LIST]
[LIST]
[*][SIZE=1]French[/SIZE]
[*][SIZE=1]Japanese[/SIZE]
[*][SIZE=1]Show layout chart[/SIZE]
[*][SIZE=1]Keyboard layout settings[/SIZE]
[/LIST]
[/LIST]
[/LIST]
[SIZE=1][SIZE=2]So basically, I can of course change the keyboard layout to japanese. But I doesn't change anything since hiragana don't show up ... 

Problem not fixed ! Thanks though...

[/SIZE][/SIZE]

---

### Post by AnesU on 2012-05-27
try to install the followings :


[LIST]
[*]scim (Smart Common Input Method platform)
[*]scim-anthy (Japanese input method module for SCIM)
[*]anthy (Japanese kana-kanji conversion engine)
[*]scim-input-pad (an add-on to input various symbols)
[*]kasumi (dictionary maintenance tool for Anthy)
[/LIST]

---

### Post by AnesU on 2012-05-27
you can install them by entering this :
$ sudo apt-get install scim 
$ sudo apt-get install scim-anthy >>>> and do this with the rest

---

### Post by whatthefunk on 2012-05-27
From the ibus icon, go to preferences.  Make sure that your enable and disable are set correctly.

Also, make sure that French, English, and Japanese are set to use ibus otherwise you wont be able to switch.

What you could also try is setting the system language to Japanese and then rebooting so that all your menus and everything are in Japanese.  See if you can type in Japanese then.  Then change your system language back to English or French.

---

### Post by kemicha on 2012-06-11
I had the same problem. Updatet from ubuntu 10.04 to 12.04. Ibus started, but doesn't change the  hiragana to Kanji. It helped to install in synaptic from anthy  the uim.
Then, in the ibus-window activate japanese the first icon(peng huang), not the anthy m17n icon.
And, additionally,  you must install an second language there, in my case unicode. Than, after new start,  I could write japanese.  Don't ask me wy!
Good luck.
Sorry, my english is not the best.

---

### Post by Aust on 2012-06-16
Thanks to all of you guys, everything work just fine now !&#12288;\\:D/

I don't really know how I did precisely, but I did everything you said. 
The important part reminds that if someone else faces the same problem, he/she'll find the answer among your posts.&#12288;

Thank you very much guys !
&#30342;&#12373;&#12435;&#12289;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#65281;&#26412;&#24403;&#12395;&#21161;&#12363;&#12387;&#12383;&#65281;

Aust

---

