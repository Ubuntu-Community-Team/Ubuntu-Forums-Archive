---
title: "Thunderbird HTF do I increase the small received list box font"
date: 2011-06-18
forum: General Help
---

### Post by goneskiing on 2011-06-18
the little font on the Thunderbird inbox list box is killing my eyes - how can I increase the font?   I created a Chrome folder under the profile but no luck - any suggestions ??  

userChrome.css

#expandedtoBox, #expandedccBox, #expandedbccBox {
  -moz-binding: url(chrome://userchrome/content/userChrome.xml#mail-multi-emailHeaderField-noMore) !important;
}

#threadTree {
    font-family: Verdana, Arial, Calibri !important;
    font-size: 12px !important;
}

#msgHeaderView {
    font-family: Verdana, Arial, Calibri !important;
    font-size: 12px !important;
    height: 100px !important;
    overflow: auto !important;
}

#folderTree {
    font-family: Verdana, Arial, Calibri !important;
    font-size: 12px !important;
}

---

### Post by pqwoerituytrueiwoq on 2011-06-18
try using userContent.css
edit:
this will make the text massive
#threadTree, #folderTree {
font-size:25px!important;
}

---

### Post by goneskiing on 2011-06-18
> **pqwoerituytrueiwoq said:**
> try using userContent.css
edit:
this will make the text massive
#threadTree, #folderTree {
font-size:25px!important;
}

Tried it - no luck - boy, talk about something being hard coded!

---

### Post by pqwoerituytrueiwoq on 2011-06-18
lol
worked for me
```
$ thunderbird --version
 Thunderbird 3.1.10
$ cat ~/.thunderbird/ugjumrdx.default/chrome/userChrome.css
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
#threadTree, #folderTree {
    font-size:50px!important;
}

```

---

### Post by goneskiing on 2011-06-19
> **pqwoerituytrueiwoq said:**
> lol
worked for me
```
$ thunderbird --version
 Thunderbird 3.1.10
$ cat ~/.thunderbird/ugjumrdx.default/chrome/userChrome.css
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
#threadTree, #folderTree {
    font-size:50px!important;
}

```


you say LOL but I don't think it's funny when:
a) Thunderbird makes it difficult to adjust the font - wasting lots of time for people to go look this up
b) various posts including yours have contradictory responses - first you said put it in userContent not userChrome - and other posts showed the directory to be "Chrome" not "chrome" 
c) based on the number of different forum posts this issue has wasted a lot of people's time.  

But at least your post got me to the point of fixing it - thks.

---

### Post by pqwoerituytrueiwoq on 2011-06-19
"talk about something being hard coded"
that is what i loled at
i just used the dom inspector and found the element i had to target and set the font size i did not look it up
the original font size works fine for me
maybe your screen resolution is too high to reed the standard font size

---

