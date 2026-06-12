---
title: "Help with Amharic input and ibus"
date: 2011-09-20
forum: General Help
---

### Post by dckirba on 2011-09-20
Hi guys (and gals),

How are you doing?

I'm trying to get an Amharic input method set up on an Ubuntu 11.04 install. 

From what I read all you need to do is install all relevant language packs, choose ibus as input method system, restart your system, start up ibus and add the relevant input method in ibus preferences.

So I installed all language packs through the Language support application. I then chose ibus as an input method. Restarted my system. Started up ibus and tried selecting Amharic as an input method but I only have Chinese available.

I double checked language support to ensure that ibus is selected as the input method system and logged out and back in for good measure.

But I still have no Amharic in ibus.

Apparently SCIM is a good alternative, but if possible I would like to stick with something that's part of the default Ubuntu install.

Does anyone have any idea what could be wrong?

Thanks in advance,

Cheers,
David

---

### Post by dino99 on 2011-09-20
just checked on oneiric here: have no am pack installed and ibus pref allow to select amharic, but it is not shown after validation, strange. Maybe a bug but:

" For Indian language users it is suggested that you use 'itrans' layout. "

[https://help.ubuntu.com/community/ibus](https://help.ubuntu.com/community/ibus)

---

### Post by dckirba on 2011-09-20
OK dokey! Now i seem to have completely lost the ability to select ibus in the Language support dialog box.

[IMG]http://dl.dropbox.com/u/5934612/Screenshot-Language%20Support.png[/IMG]

---

### Post by dckirba on 2011-09-20
Thanks Dino,

I'll have a look see, but Amharic is not an Indian language :(

---

### Post by dino99 on 2011-09-20
> **dckirba said:**
> Thanks Dino,

I'll have a look see, but Amharic is not an Indian language :(

yeah yeah, only have pasted that line to let you know :( but ibus seems buggy

---

### Post by dckirba on 2011-09-20
&#4656;&#4619;&#4637;!

Well, installing the ibus-m17n package seems to have taken care of the problem. I wish this were better documented somewhere. I think I'll write a small howto and post it on my blog :)

Cheers,

David

---

### Post by dino99 on 2011-09-20
> **dckirba said:**
> &#4656;&#4619;&#4637;!

Well, installing the ibus-m17n package seems to have taken care of the problem. I wish this were better documented somewhere. I think I'll write a small howto and post it on my blog :)

Cheers,

David

good idea, will help others in such case, but please copy/paste it to "tutorials & tips" subforum too.

---

### Post by dckirba on 2011-09-20
> **dino99 said:**
> good idea, will help others in such case, but please copy/paste it to "tutorials & tips" subforum too.

I'll definitely do that. Thanks for your help :)

---

### Post by gerardbeck on 2011-10-08
> **dckirba said:**
> I'll definitely do that. Thanks for your help :)

I appreciate your effort David. But i'm really stuck on Windows because of this problems. I got the Abys Sil font on ooo and, I can see that under synaptic as well. When I try to type, I get only the base fonts (when I add a vowel there is no change, I have only &#4608;&#4616;&#4624;&#4632;...). So in short where are you with this.
TY again

---

### Post by dckirba on 2011-10-11
Hi Gerald,

I seem to have them all working fine now except for sixth form of &#4771; which doesn't seem to be keyed to the right key. All other characters seem to be working well. For example: &#4848; &#4849; &#4850; &#4851; &#4852; &#4853; &#4854; works fine and it works fine for all characters I've had to use so far. It's only the 'a' that's driving me crazy and I need to use it a lot too... 

But in case it helps: I installed the ibus-m17n package and that helped provide an Amharic keyboard. Ask me more questions and I'll do my best to help.

David K

---

### Post by cruising on 2012-04-20
You may want to have a look at [***[COLOR="Red"][COLOR="DarkRed"]this[/COLOR][/COLOR]***]("http://ubuntuforums.org/showthread.php?t=1825337") thread for a fix to that problem.

---

### Post by dckirba on 2012-04-20
Thanks :)

I've been using ibus to date, but I'll be upgrading next week so I'll give SCIM a shot and follow your advice.

---

### Post by dckirba on 2012-05-20
> **cruising said:**
> You may want to have a look at [***[COLOR="Red"][COLOR="DarkRed"]this[/COLOR][/COLOR]***]("http://ubuntuforums.org/showthread.php?t=1825337") thread for a fix to that problem.

Thanks cruising. I finally upgraded to Precise over the weekend and used this method and it works like a charm.

---

### Post by cruising on 2012-05-20
> **dckirba said:**
> Thanks cruising. I finally upgraded to Precise over the weekend and used this method and it works like a charm.

Glad it helped! I was having problems myself tinkering with my laptop trying out various packages for input. I'm going to stick to what worked for me earlier.

---

