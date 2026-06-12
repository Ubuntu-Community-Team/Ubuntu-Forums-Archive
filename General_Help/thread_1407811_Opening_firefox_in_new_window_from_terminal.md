---
title: "Opening firefox in new window from terminal"
date: 2010-02-15
forum: General Help
---

### Post by bigbudz on 2010-02-15
I like to alias my firefox commands so I can open up mutiple pages at once. This works great.     firefox "www.google.ca" "www.yahoo.ca"&

But if I have firefox already up and running it will open as tabs of the firefox I already have running. How can I open the multiple pages in a new window in this case?

- Using -no-remote could work, but I would have to make a whole different firefox profile for each set of pages, not really a solution. 
- Also tried setting it to a particular display and it opened as a tab again. ie. firefox "www.google.ca" -display=":0.0"

---

### Post by Satoru-san on 2010-02-15
```
/usr/bin/firefox
/usr/bin/firefox www.google.ca
```for me that will open up a new window, then open google. I don't know how you could get it to go to a certian work space though.

if you dont want it to open a new tab in the new window, make the home page be 
```
about:blank
```

---

### Post by lovinglinux on 2010-02-15
> **Satoru-san said:**
> ```
/usr/bin/firefox
/usr/bin/firefox www.google.ca
```for me that will open up a new window, then open google. I don't know how you could get it to go to a certian work space though.

if you dont want it to open a new tab in the new window, make the home page be 
```
about:blank
```

That doesn't work for me.

I tried 

```
firefox %u www.google.ca
```

 and it opens a new window, but it thinks %u is the url.

---

### Post by bodhi.zazen on 2010-02-15
```
firefox google.com &
firefox -new-window http://ubuntuforums.org/ &
```

---

### Post by lovinglinux on 2010-02-15
> **bodhi.zazen said:**
> ```
firefox -w http://ubuntuforums.org/ &
```

That works ;)

---

### Post by bodhi.zazen on 2010-02-15
> **lovinglinux said:**
> That works ;)

-new-window is more reliable.

-w appeared to work, but it opens a new window to your home page, I could not pass a url reliably.

---

### Post by bigbudz on 2010-02-15
Thank you. Where did you learn about the -new-window its not on the manpages? 

Setting the display actually opens a new window, if you put the option before the url, or else it ignores it, which is what happened to me, doh.

---

### Post by lovinglinux on 2010-02-15
> **bigbudz said:**
> Thank you. Where did you learn about the -new-window its not on the manpages? 

Setting the display actually opens a new window, if you put the option before the url, or else it ignores it, which is what happened to me, doh.

[https://developer.mozilla.org/en/Command_Line_Options](https://developer.mozilla.org/en/Command_Line_Options)

---

