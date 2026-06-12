---
title: "NoScript test thread"
date: 2010-06-13
forum: General Help
---

### Post by maotse on 2010-06-13
An user told me he couldn't post/edit here with NoScript installed.

1st test: posting a new thread with ubuntuforums.org kept forbidden (of course, WYSIWYG editor can't work this way, but I can enter HTML in the text area nevertheless).
SUCCESS. 

2nd test: editing the same thread with ubuntuforums.org still forbidden.
SUCCESS

3rd test: editing the same thread with ubuntuforums.org allowed.
**Problem**
I expected WYSIWYG editing to work now, and in fact the editing area is now HTML-styled, **but** buttons on the formatting toolbar (e.g. "B" for bold) don't work. Looking in *Tools|Error Console* I can see lots of lines with this message:

[FONT=Courier New]Error: vB_Editor[this.editorid] is undefined
Source file: [http://ubuntuforums.org/clientscript/vbulletin_textedit.js?v=384](http://ubuntuforums.org/clientscript/vbulletin_textedit.js?v=384)
Line: 11
[/FONT]
This probably means some external script is still missing, breaking the main script.
Let's see what's left to be allowed in the NoScript menu: 

[LIST]
[*]**google-analytics.com** - unlikely, since NoScript has surrogates for that
[*]**yahooapis.com - **good candidate, since it serves centralized copies of the popular YUI JavaScript framework, which appears to be used by this forum (and possibly by other vBulletin installations). Recent change?
[HTML]<script type="text/javascript" src="http://yui.yahooapis.com/2.7.0/build/yahoo-dom-event/yahoo-dom-event.js?v=384"></script><script type="text/javascript" src="http://yui.yahooapis.com/2.7.0/build/connection/connection-min.js?v=384"></script>[/HTML]
[/LIST]
So i tried **Allow yahooapis.com** and bingo!, formatting buttons started to work.

---

