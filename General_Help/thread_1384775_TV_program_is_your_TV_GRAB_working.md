---
title: "TV program: is your TV_GRAB working?"
date: 2010-01-18
forum: General Help
---

### Post by frenchn00b on 2010-01-18
Hello,

I noticed that tv_grab is not working any longer. It seems that they do not updated the pages. It is since long time the problem. 

:( 

Have you same problem or is it workign for your country? 

Cheers

---

### Post by lovinglinux on 2010-01-18
Perhaps the source site has changed. Have you tried to use another country just for testing purposes?

I can't confirm if it is working or not because in my country there is a company that makes the guides for the satellite providers and they distribute a complete ready-to-use xmltv for users. So I just download from them.

Do you still have a xmltv file sample? I'm asking this because I would like to test it with my media center extension for Firefox. It currently works pretty fine with my xmltv file and with a file from another user from UK that sent me a sample. But little differences in the xmltv content could cause some issues, so I want to test as many different sources and languages as possible.

---

### Post by frenchn00b on 2010-01-19
> **lovinglinux said:**
> Perhaps the source site has changed. Have you tried to use another country just for testing purposes?

I can't confirm if it is working or not because in my country there is a company that makes the guides for the satellite providers and they distribute a complete ready-to-use xmltv for users. So I just download from them.

Do you still have a xmltv file sample? I'm asking this because I would like to test it with my media center extension for Firefox. It currently works pretty fine with my xmltv file and with a file from another user from UK that sent me a sample. But little differences in the xmltv content could cause some issues, so I want to test as many different sources and languages as possible.

I mean those xmlt, this is crazy, it never works as soon as somebdy change something on the website. 

It is a bit like shoutcast, after some years, all codes arent working. 

So I avoided this solution, and use antoher way: the no internet way. 

We use the teletext of the channel, and make it as if it is reading it. 
Then one get the /tmp/TV.xml.

It works in any country + without interent + is in the repositories. :) 

here is the code, that I start in .xinitrc: 
[B]
```
nxtvepg -rcfile $HOME/.nxtvepgrc   -dump xml -provider merged > /tmp/TV.xml 2> /dev/null   &


sh $HOME/.freevo/freevoscripts/grab_nxtvepg.sh  &
```


grab_nxtvepg.sh 
```

nxtvepg -daemon -acqonce full -rcfile $HOME/.nxtvepgrc 
nxtvepg -dump xml -provider ff -rcfile $HOME/.nxtvepgrc > /tmp/TV.xml  
``` 


[/B]


A first gui start of nxtvepg, is required to set up the thing. 


Enjoy !!

---

### Post by lovinglinux on 2010-01-19
> **frenchn00b said:**
> I mean those xmlt, this is crazy, it never works as soon as somebdy change something on the website. 

It is a bit like shoutcast, after some years, all codes arent working. 

So I avoided this solution, and use antoher way: the no internet way. 

We use the teletext of the channel, and make it as if it is reading it. 
Then one get the /tmp/TV.xml.

It works in any country + without interent + is in the repositories. :) 

here is the code, that I start in .xinitrc: 
[B]
```
nxtvepg -rcfile $HOME/.nxtvepgrc   -dump xml -provider merged > /tmp/TV.xml 2> /dev/null   &


sh $HOME/.freevo/freevoscripts/grab_nxtvepg.sh  &
```


grab_nxtvepg.sh 
```

nxtvepg -daemon -acqonce full -rcfile $HOME/.nxtvepgrc 
nxtvepg -dump xml -provider ff -rcfile $HOME/.nxtvepgrc > /tmp/TV.xml  
``` 


[/B]


A first gui start of nxtvepg, is required to set up the thing. 


Enjoy !!


Yep, you are correct, xmltv grabbing stops working as soon as something in the source site changes. Unfortunately, this is the only way for a lot of people. 

Thanks for the tip, but we don't have teletext here, not even HD TV.

---

### Post by frenchn00b on 2010-01-19
> **lovinglinux said:**
> Yep, you are correct, xmltv grabbing stops working as soon as something in the source site changes. Unfortunately, this is the only way for a lot of people. 

Thanks for the tip, but we don't have teletext here, not even HD TV.

give a try : nxtvepg
from apt-get 

then you go into:
CONFIGURE >> PROVIDER SCAN >> START SCAN 
;) maybe it works with some channels

---

### Post by lovinglinux on 2010-01-19
> **frenchn00b said:**
> give a try : nxtvepg
from apt-get 

then you go into:
CONFIGURE >> PROVIDER SCAN >> START SCAN 
;) maybe it works with some channels

Perhaps. I have a DHT satellite box. Do you if it works with such system?

I'm busy migrating my site to another server, so I will do it tomorrow. Thanks.

---

### Post by rd1381 on 2010-02-02
> **frenchn00b said:**
> Hello,

I noticed that tv_grab is not working any longer. It seems that they do not updated the pages. It is since long time the problem. 

:( 

Have you same problem or is it workign for your country? 

Cheers

what country are u testing?
i am new to tv guide programs but when i try france and it didnt work, i got the snapshot version on xmltv source from their software site and compile it myself and france worked again.
note: in installing there is a step that is 'make test' it gives some error but installing works so i think it checks the sites for getting the guide and mie dah just 2 errors ,so don't worry if it gave you errors there.

---

### Post by frenchn00b on 2010-02-03
> **frenchn00b said:**
> I mean those xmlt, this is crazy, it never works as soon as somebdy change something on the website. 

It is a bit like shoutcast, after some years, all codes arent working. 

So I avoided this solution, and use antoher way: the no internet way. 

We use the teletext of the channel, and make it as if it is reading it. 
Then one get the /tmp/TV.xml.

It works in any country + without interent + is in the repositories. :) 

here is the code, that I start in .xinitrc: 
[B]
```
nxtvepg -rcfile $HOME/.nxtvepgrc   -dump xml -provider merged > /tmp/TV.xml 2> /dev/null   &


sh $HOME/.freevo/freevoscripts/grab_nxtvepg.sh  &
```


grab_nxtvepg.sh 
```

nxtvepg -daemon -acqonce full -rcfile $HOME/.nxtvepgrc 
nxtvepg -dump xml -provider ff -rcfile $HOME/.nxtvepgrc > /tmp/TV.xml  
``` 


[/B]


A first gui start of nxtvepg, is required to set up the thing. 


Enjoy !!

I use this trick and it still works on my tvtime, it is cool

but I have to do : 
```
cp .tvtime/channel.xml-bak  .tvtime/channel.xml
```
very often cuz soemtimes it changes by itself. i use freevo.

so i have the programs of what i am watching using teletext instead ot tv_grab

---

