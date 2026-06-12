---
title: "Browser issues /w Yahoo"
date: 2010-05-18
forum: General Help
---

### Post by cavemanbangs on 2010-05-18
Ubuntu 10.4 (new install) 32-bit 

FireFox and chrome share the same issues 

Yahoo.com (homepage) will not load (chrome) or freezes (firefox)
(if something dose load it is just text that is all over the place were it should not be) 

i can get to the yahoo mail sign in page yahoo.com/mail with no issues loading 
 
i can sign-in but when i go to check my mail the email message will not load (yahoo will give me an error message)

every other site seems to work fine but there some issues when the site try's to redirect me 


google gmail
youtube
facebook
seem to work fine with no issues.  

i have reinstalled ubuntu 3 times clean with the same issue -  i started with 64-bit then moved to 32-bit

i have reinstalled flash countless times

i think flash or java is the issue but i cant for the life of me figure out why yahoo would be the only site messing up and every-other site seems to work fine  

idk if im missing a hidden repository ? or what (i have the media one)

---

### Post by Concrete on 2010-05-18
What sources and version of flash and java you installed!?

---

### Post by cavemanbangs on 2010-05-18
flash is 10.0.45.2ubuntu1 ... ? idk if thats the flash version or the installer version # for the synaptic manager .. 

java i started with what ever was default .. 
then when i used the media repository i think it installed openjdk6 
unless it was there before

---

### Post by cavemanbangs on 2010-05-18
so i just installed libv8-2.0.3 for the chrome browser and it allowed the yahoo home page to load *weird .. however firefox still freezes .. 

and i still can not check my mail in ether browser 

i also have swift fox with the same issues 

is there another java to try ? my buddy is also having the same issue

---

### Post by jatanr on 2010-05-21
I am also having the same issue, but still haven't found any solution to it. Someone has suggested that it may be an issue with the ISP.

---

### Post by cavemanbangs on 2010-05-27
I don't understand how it could be an ISP issue if i can connect with windows no problem ...

when i updated java (with the ubuntu version) firefox was able to log in .. same with chrome when i added  libv8-2.0.3 (im guessing its version of java integration)

however when logged in i can see my emails (names and subject) but when i click on them it won't allow the email to load :confused:

ive also noticed in windows yahoo blocks (chrome) from video streams

*its not really issue except that my school requires the use of an yahoo account for groups - and i have forwarding to my gmail but i like to double check once and awhile just to make sure.

---

### Post by cavemanbangs on 2010-06-04
somehow i solved my own problem by reinstalling everything after i wiped my hard-drive ..  maybe the drivers on the ubuntu cd don't play well with blu-ray drivers very nicely and tend to corrupt everything ?

---

### Post by linuxwonder on 2010-10-24
Hi All:

I have noticed yet another problem : When I try to access my Yahoo e-mail from the Google share icon in the Google toolbar in, Firefox, I get the following error:

[FONT=Helvetica,Arial][B]Your request is prohibited because it would cause a cycle.

T[/B]his used to work just fine under 9.04. I switched to 10.04 and am now seeing this error.:(

Thanks in advance
[/FONT]

---

### Post by NoVista on 2010-11-03
In response to the original post >>
"(if something does load it is just text that is all over the place were it should not be)"

Clearing the browser cache will resolve that.
Tools>>Clear Recent History>Cache

---

