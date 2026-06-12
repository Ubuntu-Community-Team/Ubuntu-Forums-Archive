---
title: "Firefox: Problem showing pages in Farsi"
date: 2011-09-25
forum: General Help
---

### Post by amir17901m on 2011-09-25
hi 
i just started using ubuntu officially like 3 weeks ago !
so i'm a newbie !

my mother languange is farsi and a lot of sites that i'm used to surf is in farsi language but ...

firefox does not show farsi texts right ! you can read it but you're not comfortable with it ! and that's because some charachters are seperated where they should not be !

chrome shows farsi text sweet and sound !
but firefox which is ,was and will be my #1 is showing some signs of weakness on this :D

by the way my ubuntu version is 11.04 

anybody has any ideas ?

---

### Post by Shazaam on 2011-09-25
There are Farsi ttf fonts found in Synaptic, see if those work.
Here is a page I found in google...

[http://www.hoomanb.com/Unicode/](http://www.hoomanb.com/Unicode/)

---

### Post by amir17901m on 2011-09-25
big thanks goes to you ;)

i have installed the package ttf-farsiweb  and i can surf so many sites!no problem ! but there are some sites that i still seem to have problems with :D

i need someone who knows farsi languange and can read farsi to check some sites and see if the problem is in fonts or something else ;) 

for instance :[]("http://www.shatel.ir") still not coming up nicely at all !!!
do you think maybe it's because this site's designers did not pick some standard fonts ? 
thx in advance !!!

---

### Post by amir17901m on 2011-09-25
one site that i have problems with it's fonts : [www.shatel.ir](www.shatel.ir)

---

### Post by lovinglinux on 2011-09-26
> **amir17901m said:**
> big thanks goes to you ;)

i have installed the package ttf-farsiweb  and i can surf so many sites!no problem ! but there are some sites that i still seem to have problems with :D

i need someone who knows farsi languange and can read farsi to check some sites and see if the problem is in fonts or something else ;) 

for instance :[]("http://www.shatel.ir") still not coming up nicely at all !!!
do you think maybe it's because this site's designers did not pick some standard fonts ? 
thx in advance !!!

It could be. I never saw such problem in Firefox, but you could try to disable the option "Allow pages to choose their own font" in the *Font & Color* preferences. You can find that in the *Content* preferences tab. You need to click the *Advanced* button, next to *Font & Colors* options.

---

### Post by amir17901m on 2011-09-26
check this site : [www.shatel.ir](www.shatel.ir)
see for your self is this site comes up and shows the fonts how it should !!! but the problem is you'll get it only if you know farsi (persian) ! if you don't!! you won't recognize a thing !

i'v unchecked that preference option too ! but it doesn't seem to  work :(

---

### Post by lovinglinux on 2011-09-28
> **amir17901m said:**
> check this site : [www.shatel.ir](www.shatel.ir)
see for your self is this site comes up and shows the fonts how it should !!! but the problem is you'll get it only if you know farsi (persian) ! if you don't!! you won't recognize a thing !

i'v unchecked that preference option too ! but it doesn't seem to  work :(

Without being able to reproduce the problem, it will hard for me to help. Perhaps [this](http://support.mozilla.com/en-US/questions/863157) will help. Look at the chosen solution, just below the question. I don't understand what it is saying, but looks like a simple config trick.

---

### Post by amir17901m on 2011-09-28
thank you lovinglinux 

the link that you left there helped me understand some of the basics of fonts for web and all that stuff !!!

i did all the tweeks and hacks but it didn't solve my problem :(( it's really really disappointing from firefox !! 
i've always been a fan of the fox !!! but this ! this is not so cool !

the strange thing is i can see farsi fonts on my laptop ASUS N82JQ  almost like better than it's windows versions ! using the same OS Natty and same version of firefox being v 6 .
 
:D but thank you !thank you so much !

as much as i am disappointed in this problem i'm fascinated by the great user support for linux specially ubuntu ;)

---

### Post by Krytarik on 2011-09-28
> **amir17901m said:**
> it's really really disappointing from firefox !! 
i've always been a fan of the fox !!! but this ! this is not so cool !
I'm curious if this issue is present in Chrome/ium, too!?

---

### Post by amir17901m on 2011-09-28
No i didn't have the problem with chrome ! but the say if you search you'll find ;)

here's the perfect solution :

[http://meysam.ws/blog/1388/12/font-compulsory-from-night-bread/](http://meysam.ws/blog/1388/12/font-compulsory-from-night-bread/)

now i can surf through all persian websites and i don't have font problems :D 

cheers !!!

---

### Post by lovinglinux on 2011-09-28
> **amir17901m said:**
> No i didn't have the problem with chrome ! but the say if you search you'll find ;)

here's the perfect solution :

[http://meysam.ws/blog/1388/12/font-compulsory-from-night-bread/](http://meysam.ws/blog/1388/12/font-compulsory-from-night-bread/)

now i can surf through all persian websites and i don't have font problems :D 

cheers !!!

I am glad you fixed it.

What was the source of the problem and the solution?

---

### Post by Krytarik on 2011-09-28
> **lovinglinux said:**
> What was the source of the problem and the solution?
Google Translate is your friend! :D

[http://translate.google.com/translate?hl=en&sl=auto&tl=en&u=http%3A%2F%2Fmeysam.ws%2Fblog%2F1388%2F12%2Ffont-compulsory-from-night-bread%2F](http://translate.google.com/translate?hl=en&sl=auto&tl=en&u=http%3A%2F%2Fmeysam.ws%2Fblog%2F1388%2F12%2Ffont-compulsory-from-night-bread%2F)

Basically, importing TTFs from Windows, to close an apparent fonts gap for Firefox. But I don't know why the same doesn't apply to Chrome, as already stated in the OP (just re-read those; sorry for the redundant question!). Wondering if Chrome and Chromium are behaving the same here, or if Google's Chrome brings some additional fonts with it, possibly!?

---

### Post by lovinglinux on 2011-09-28
> **Krytarik said:**
> Google Translate is your friend! :D

[http://translate.google.com/translate?hl=en&sl=auto&tl=en&u=http%3A%2F%2Fmeysam.ws%2Fblog%2F1388%2F12%2Ffont-compulsory-from-night-bread%2F](http://translate.google.com/translate?hl=en&sl=auto&tl=en&u=http%3A%2F%2Fmeysam.ws%2Fblog%2F1388%2F12%2Ffont-compulsory-from-night-bread%2F)

Basically, importing TTFs from Windows, to close an apparent fonts gap for Firefox. But I don't know why the same doesn't apply to Chrome, as already stated in the OP (just re-read those; sorry for the redundant question!). Wondering if Chrome and Chromium are behaving the same here, or if Google's Chrome brings some additional fonts with it, possibly!?

Thank you for the information.

---

### Post by amir17901m on 2011-09-29
As krytarik said the source of the problem was that ubuntu do not have some of the .TTF fonts preinstalled ! you should import it yourself manually !! and the most important one is Tahoma !!! the solution explains how to import some of the windows fonts into a folder called .fonts into the home folder and then fc-cache makes them work :D i guess :P That is the main idea of that !!

---

### Post by lovinglinux on 2011-09-29
> **amir17901m said:**
> As krytarik said the source of the problem was that ubuntu do not have some of the .TTF fonts preinstalled ! you should import it yourself manually !! and the most important one is Tahoma !!! the solution explains how to import some of the windows fonts into a folder called .fonts into the home folder and then fc-cache makes them work :D i guess :P That is the main idea of that !!

Thanks for the clarification. Will be easier now to help other users with the same problem.

---

### Post by amir17901m on 2011-09-29
Your Welcome ;)

marked this thread as solved !!

---

