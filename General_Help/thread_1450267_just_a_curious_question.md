---
title: "just a curious question"
date: 2010-04-08
forum: General Help
---

### Post by fremantle on 2010-04-08
erm.. i dont know how to ask this but remember how in windows, when you click on your internet browser's address bar, the whole link gets selected and you can just start typing a new one without having to press backspace? well, in linux i noticed that does not happen. does anyone know why?

---

### Post by crlang13 on 2010-04-08
Assuming we're talking about firefox... 

double click instead.

I don't know why it's different or how to change it to be a single click, but oh well :P

---

### Post by lavinog on 2010-04-08
It could be MS holds a patent on "method of clearing fields with just backspace"
Kind of like the have a patent on [page down](http://www.patentstorm.us/patents/7415666.html)...just guessing though.

Another trick is to click on the address bar and hit ctrl-a.

---

### Post by EarlySight on 2010-04-08
Well, at least a double click actually works with Ubuntu and Firefox. Under Chrome, nothing works. Tried one click, two clicks, three clicks, fourteen super fast clicks. Nothing will do.

---

### Post by oldos2er on 2010-04-08
F6 works for me in Firefox.

---

### Post by crichard on 2010-04-08
Type > about:config in the address bar of the firefox, Click the &#8220;*I&#8217;ll be careful, I promise!*&#8221; button to access this tweak.
In that filter bar insert the following keyword 

browser.urlbar.clickSelectsAll

then right click on that & press toggle to change the value to True.  That's it. Hereafter all text will be selected  when you click on the URL bar.

---

### Post by cariboo on 2010-04-10
Double click works in Chrome on my Lucid install.

---

### Post by darolu on 2010-04-10
I usually press "Ctrl + L" when I want to type something in the address bar, it highlights the entire text.

---

### Post by fremantle on 2010-04-10
> **crichard said:**
> Type  in the address bar of the firefox, Click the “*I’ll be careful, I promise!*” button to access this tweak.
In that filter bar insert the following keyword 

browser.urlbar.clickSelectsAll

then right click on that & press toggle to change the value to True.  That's it. Hereafter all text will be selected  when you click on the URL bar.
thanx man, im gonna try it right now.
And yeah, nothing works on chrome, which im using rite now coz firefox is freakin slow. do u think that ubuntuzilla is going to be faster?! i heard sum1 say tht.

---

### Post by fremantle on 2010-04-10
> **fremantle said:**
> thanx man, im gonna try it right now.
And yeah, nothing works on chrome, which im using rite now coz firefox is freakin slow. do u think that ubuntuzilla is going to be faster?! i heard sum1 say tht.

yess its working. thanx crichard. do u know how to do tht in chrome?

---

### Post by crichard on 2010-04-10
[@fremantle]("http://ubuntuforums.org/member.php?u=1033050")


There is no about:config in Chrome browser right now. You can try some other keyboard shortcuts like Ctrl+L or Alt+D or F6.. It's common to Firefox &  Chrome.
BTW, You can install firefox from [http://mozilla.com](http://mozilla.com) 
Have a look at this post to install [Firefox / Thunderbird in Ubuntu.]("http://surferzworld.com/?p=193")

---

### Post by fremantle on 2010-04-10
no itsok i also hav ubuntuzilla but its slower thn chrome

---

### Post by azertyh on 2010-04-10
> **crichard said:**
> Type  in the address bar of the firefox, Click the “*I’ll be careful, I promise!*” button to access this tweak.
In that filter bar insert the following keyword 

browser.urlbar.clickSelectsAll

then right click on that & press toggle to change the value to True.  That's it. Hereafter all text will be selected  when you click on the URL bar.

wonderful!

thanks for this tip.

double-clicking is not annoying but i prefer the simple click.

---

### Post by agkq62 on 2010-05-16
> **crichard said:**
> Type  in the address bar of the firefox, Click the “*I’ll be careful, I promise!*” button to access this tweak.
In that filter bar insert the following keyword 

browser.urlbar.clickSelectsAll

then right click on that & press toggle to change the value to True.  That's it. Hereafter all text will be selected  when you click on the URL bar.

Apologies I am a bit lost with this tweak. Could some kind person talk me through it.

Many thanks.

---

### Post by lavinog on 2010-05-16
> **agkq62 said:**
> Apologies I am a bit lost with this tweak. Could some kind person talk me through it.

Many thanks.
In firefox enter **about:config** into the address bar.
It should give you a warning about voiding the warranty.  After clicking "I'll be careful...", find browser.urlbar.clickSelectsAll and double click to toggle between true and false...set to true if you want to just single click the address bar.

---

### Post by agkq62 on 2010-05-17
Thanks for the reply, I finally get there.

I had to put in the entry for the clickselectsall and set the double click entry to false.

---

### Post by TheStroj on 2010-05-17
I dont see a problem with Chrome - doubleclick works for me

---

### Post by crichard on 2010-05-19
> **TheStroj said:**
> I dont see a problem with Chrome - doubleclick works for me

FYI, this thread is about selecting the URL by using single click :) Obviously double click works but few people like to use single click!!!

---

