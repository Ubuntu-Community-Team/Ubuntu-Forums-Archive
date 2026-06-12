---
title: "typing in Hindi Language with various input methods in ibus preferences"
date: 2012-02-05
forum: General Help
---

### Post by jamesbon on 2012-02-05
Hi,
I use Ubuntu 11.10 and Gnome environment. I am able to type documents in Hindi by a method shown here
[http://www.youtube.com/watch?v=LL7icGNhIfI](http://www.youtube.com/watch?v=LL7icGNhIfI)
I installed ibus-m17n and ibus packages and have enabled support for Hindi language in gnome-language-selector.I have following input methods enabled in ibus preference window

[LIST]
[*]Hindi inscript (m17n)
[*] Hindi phonetic (m17n)
[*] Hindi itrans (m17n)
[*] Hindi remington (m17n)
[*] Hindi typewriter (m17n)
[/LIST]
 a snapshot for the same can be seen here
[http://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5705518106929667058](http://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5705518106929667058)

Also you can see in this snapshot that these methods do come in drop down menu of ibus 

[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704771437325752466](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704771437325752466)

 I open libreoffice and press Ctrl+Space so that I can type in Hindi. I am able to type in Hindi.


When the input method is off as in this snapshot 
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5705519585633896530](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5705519585633896530)

then I am able to type in Hindi with following kind of keyboard
```
/usr/share/m17n/hi-typewriter.mim
```
i.e. by pressing key  "h" letter &#2346;  gets typed. Which is expected behavior. 


Now comes the problem upon selecting the method phonetic as in this snapshot
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704771437325752466](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704771437325752466)

pressing key  "h" letter again &#2346; gets typed. Which is not expected.As per my understanding the keymap for phonetic input method in this case is 

```
/usr/share/m17n/hi-phonetic.mim
``` and given that input method phonetic is already selected 
upon pressing key "h" letter "&#2351;" should get typed.

That means that selection of different input methods has no effect on typing. So is ibus not working properly or I missed some thing? 
How can I get expected behavior when selecing different input methods in ibus preference window?

---

