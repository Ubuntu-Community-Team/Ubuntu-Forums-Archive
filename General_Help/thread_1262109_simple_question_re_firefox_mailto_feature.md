---
title: "simple question re: firefox mailto feature"
date: 2009-09-09
forum: General Help
---

### Post by tjk on 2009-09-09
Seems simple and straight forward but... I can't figure out how to make it so that firefox will open thunderbird's composition window when I right click (context menu) on a email address, while viewing a website. (I've checked firefox extensions) 
I know you all are very helpful, so I thought I'd drop a msg here...  Thanks.

Using Firefox 3.5

---

### Post by tjk on 2009-09-09
Anyone?  Please.

---

### Post by Vaphell on 2009-09-09
you should go to System->Preferences->Preferred apps
set Thunderbird as a default mail app, it should start every time you click mailto link

---

### Post by tjk on 2009-09-09
> **Vaphell said:**
> you should go to System->Preferences->Preferred apps
set Thunderbird as a default mail app, it should start every time you click mailto link

Thanks for responding...

The preference is already set to Thunderbird.  The problem is that I don't have a menu icon/button to click on (in the context menu) and nothing happens if I click directly on the email address.

---

### Post by Vaphell on 2009-09-09
that email address is in plain text or it's a clickable link with mailto: prefix?

i made a simple page with clickable email address and it called thunderbird window just fine
also running thunderbird from terminal works
```
thunderbird mailto:aaa@wtf.com
```
if it works for you, then it should be possible to get TB from links in FF, because that's how it's invoked (thunderbird %s command)

plain text emails have no context menu option though, so you need to run TB manually

---

### Post by tjk on 2009-09-09
> **Vaphell said:**
> that email address is in plain text or it's a clickable link with mailto: prefix?

i made a simple page with clickable email address and it called thunderbird window just fine
also running thunderbird from terminal works
```
thunderbird mailto:aaa@wtf.com
```if it works for you, then it should be possible to get TB from links in FF, because that's how it's invoked (thunderbird %s command)


Okay.  The above command works in the terminal, but it still isn't working in FF.  Even when I enter FF preferences and change the content "mailto:" to "always ask" I still do not get a response of any kind.

I have opened about:config to see if there was anything obviously wrong, but there are about a dozen various lines and I don't understand what most of them do.  Some of the questionable ones are:[INDENT]google.toolbar.mailto.gmail.configured;true
network.protocol-handler.expose.mailto;true
network.protocol-handler.external.mailto;false
network.protocol-handler.warn-external.mailto;false

[/INDENT]Could the problem have anything to do with these settings?

---

### Post by tjk on 2009-09-11
> **tjk said:**
> Seems simple and straight forward but... I can't figure out how to make it so that firefox will open thunderbird's composition window when I right click (context menu) on a email address, while viewing a website. (I've checked firefox extensions) 
I know you all are very helpful, so I thought I'd drop a msg here...  Thanks.

Using Firefox 3.5

Well, I figured out how to fix the problem.  I found it at: [http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions) , where it explained that the Google Toolbar changes the settings in about:config.  I changed the mailto settings back to default and everything works again.  It's weird that no one else seems to have had the same problem...

---

### Post by misfitpierce on 2009-09-11
Glad to hear you fixed the problem. Very nice and enjoy.

---

