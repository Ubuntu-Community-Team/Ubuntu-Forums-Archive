---
title: "[kmail] how to use &quot;process with external program&quot; in  templates"
date: 2010-04-01
forum: General Help
---

### Post by De-MonHell on 2010-04-01
hi
i'm trying to create a custom "reply to all" template that strip away the sequences of 2 or more blank lines from the original message and put the result in the reply.
The commands to obtain this in kmail, seems to be there, but i don't get how to use them (or they are buggie).

I do this way (the way that is not working):
*Settings --> Configure Kmail --> Composer --> Standard Temlates --> Reply To Sender (or Reply To All)*

From here:
*Insert Command --> process with external program --> pipe original message body and insert as is*
i replaced:
[PHP]%QUOTE[/PHP]
with 
[PHP]%TEXTPIPE=""[/PHP]

Then, in %TEXTPIPE's quotes, i've wrote this
[PHP]%TEXTPIPE="/opt/myScripts/remove2blanklines"[/PHP]

where remove2blanklines is a script that strip sequences of blank lines from the input.

Now, composing a "reply to all"-mail, comes out with a blank reply section.
So i don't understand if i'm using it the wrong way (no manuals around :( ) or if it is has a bug.

someone can at least explain me how the "process with external program" feature works?

ADDITIONAL INFOs: 
[LIST]
[*]remove2blanklines works nicely when called from a shell.
[*]kde/kontact 4.3.2
[*]kubuntu 9.10 64bit
[/LIST]

many thanks

---

### Post by De-MonHell on 2010-04-07
some kmail's expert around here?

---

