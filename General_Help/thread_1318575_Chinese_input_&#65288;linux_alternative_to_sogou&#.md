---
title: "Chinese input &#65288;linux alternative to sogou&#65311;&#65289;"
date: 2009-11-07
forum: General Help
---

### Post by hirolau on 2009-11-07
Hi.

I am trying to get my girl friend to use Ubuntu.

So far i have been able to find good replacements of all her software.

PPS, QQ and other chinese tools and popular programs.

But there is one thing I cant find. She want an input method called sogou. Some smart pinyin input method available on windows. I am having a hard time searching for it as my chinese is quite bad.

Is there an Linux alternative as good as sogou&#65311; Is ibus or scim the way to go. Is there anyway to get Google pinyin run on Ubunutu?

In short - what is the best input method for simplified Chinese?  

Many thanks
Harald

---

### Post by Irihapeti on 2009-11-08
Scim-pinyin is a smart pinyin method for entering Simplified Chinese characters. I use it myself (I'm learning Chinese) and I think it is the method my (Chinese) daughter-in-law uses in Ubuntu.

You will need to install scim, scim-bridge-client-gtk and scim-pinyin and then do some configuration. How you do this depends on which version of Ubuntu you are running.

For 9.10, see [http://ubuntuforums.org/showpost.php?p=8273690&postcount=3](http://ubuntuforums.org/showpost.php?p=8273690&postcount=3) (obviously, substitute scim-pinyin for scim-anthy). For earlier versions, see [http://ubuntuforums.org/showthread.php?t=1267584](http://ubuntuforums.org/showthread.php?t=1267584)

Ibus is an alternative, but it only seems to work properly in Karmic, unless you enable ppa repositories.

---

### Post by XProflmfao on 2009-11-08
Unfortunately, Google Pinyin doesn't work on Ubuntu. Luckily, Scim does. Like Irehapeti said, Ibus will only work on Karmic Koala. However, this might not be much of problem as long as your girlfriend downloads the newest version (Karmic Koala) and wants to use Ibus. Good luck!

---

### Post by mdurham on 2009-11-08
I read that SCIM is no longer in development, I have used ibus and would say it's very good for Chinese (maybe others too but I've only tried Chinese). Give it a try.
Cheers, Mike

---

### Post by Irihapeti on 2009-11-08
You can get iBus to work on Jaunty, but you need to enable a ppa. I believe it's also possible in Intrepid, but Hardy is definitely out.

iBus is still pretty new. Scim has been around for quite a while now.

---

### Post by YQ002lc2 on 2009-12-29
I think Google Pinyin will run on Ubuntu
[http://code.google.com/p/scim-googlepinyin](http://code.google.com/p/scim-googlepinyin)

thanks,

jpinson

---

### Post by YQ002lc2 on 2010-11-04
also see my detailed post here about which input methods I now use and recommend.

[http://ubuntuforums.org/showthread.php?p=10074055#post10074055](http://ubuntuforums.org/showthread.php?p=10074055#post10074055)

---

### Post by Naseschwarz on 2012-06-07
Hey there!

Although this thread is kinda old, I'll just dig it up here for I might have some interesting info on that.

I tried and used SCIM, Ibus, Google Pinyin, Microsoft Pinyin and Sogou Pinyin extensively, because I write a lot in Chinese. According to my experience Sogou is by far the best of the above. Why? All of the above input methods are straight forward pinyin input methods that can learn combinations of characters you use. The huge advantage Sogou has is that it seems to have massive data on popular expressions, citations, new words and so on. On top of that it accesses the internet to transform a whole sentence into a meaningful phrase. For I have no idea how this actually works, I can only tell you that it is really awesome. 
To give you an example:
Let's assume you want to write a simple sentece that is commonly used, like "wo huijia le ni hai zai bu zai ruguo buzai jiu gei wo liuyan". With Ibus I have to do the input word by word or phrase by phrase (asterics is selection of characters before continuing to write): wohuijia*le*nihai*zai(*)buzai*ruguo*buzai*jiu*geiwo(*)liuyan. 
When using Sogou you go like: wohuijialenihaizaibuzai*ruguobuzaijiugeiwoliuyan. And that's it - takes Sogou amout a seconds (sometimes more, sometimes less) to figure this out. So, after using Sogou, using other input methods feels like a pain in the a*s, plainly.

On top of that you can download a ton of additional special vocab, like common song lyrics, tech lingo (various sorts), internet lingo and so on - it's really massive.

So, apart from doing some ads for Sogou here (just kidding ;) ), I would absolutely love to see Sogou working on Ubuntu. There is some advice on installing Sogou out there (mostly in Chinese), but none worked for me so far. Installing it with WINE is kinda pointless too, for I don't know how to enable special input methods under WINE for programs running in Ubuntu... 

I tried using Sogou libraries with ibus (there was a turtorial on that somewhere...), but that didn't seems to have changed much.

Does anybody know any way to get Sogou to work in Ubuntu? Once I find any, I'll happily translate it for fellow Chinese learners of course! ;)

Anyone any advice??

---

### Post by ppwwyyxx on 2012-11-27
As a Chinese, I must say..
Linux so far doesn't have a pinyin input method as good as Sogou, indeed. (I have searched for years, trust me..)
Well, not long before, Sogou do promise to release a linux version, but it didn't give a specific time.
Google pinyin can work in Linux, but may need a lot of hacking on source code (because Ubuntu is a OS with misc. troubles...) . You can search ibus-googlepinyin or scim-googlepinyin to see for details.
I myself use one called ibus-sogoupycc([https://code.google.com/p/ibus-sogoupycc/](https://code.google.com/p/ibus-sogoupycc/)). Though it's deprecated, but I found it worked fine under Archlinux..(no need to hack..).
BTW, since it's an cloud input method, it work pretty well just like the original sogou pinyin with Internet. But when you are offline, bugs appear. 
For an offline choice, I recommend sunpinyin or rime, which has both ibus and scim frontend. They work pretty well....  (rime might be difficult to config)..

---

### Post by howefield on 2012-11-27
Old thread back to sleep.

---

