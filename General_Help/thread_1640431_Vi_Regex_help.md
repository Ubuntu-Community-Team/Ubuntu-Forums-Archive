---
title: "Vi Regex help"
date: 2010-12-07
forum: General Help
---

### Post by COKEDUDE on 2010-12-07
Can someone tell me what is going with this expression **:%s/<C-V><C-M>/**. 

Is there a way to get a more useful message if the carriage return has been deleted? 

> I get the "Pattern not found: ^M" error with that.
You'll get that error if you've already deleted all the carriage
returns...

[http://objectmix.com/editors/149245-fixing-dos-line-endings-within-vim.html#post516826](http://objectmix.com/editors/149245-fixing-dos-line-endings-within-vim.html#post516826)

Why does this expression work for changing CRLF line endings to LF and the one above doesn't work **:%s/\r//g**?

---

### Post by bodhi.zazen on 2010-12-07
From all your questions you might want to look at the package tofromdos =)

---

### Post by COKEDUDE on 2010-12-07
> **bodhi.zazen said:**
> From all your questions you might want to look at the package tofromdos =)

Pidgin is keeping me busy :(. I would have never had all these questions if pidgin would just work :). Unfortunately Microsoft has mess everything up when I need MSN for like the first time since August. If you don't know what I'm talking about please read these 2 articles. 

[http://developer.pidgin.im/ticket/12906](http://developer.pidgin.im/ticket/12906)
[http://developer.pidgin.im/wiki/MSNCertIssue](http://developer.pidgin.im/wiki/MSNCertIssue)

---

