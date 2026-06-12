---
title: "Opera copy and paste in to Thunderbird"
date: 2010-08-20
forum: General Help
---

### Post by SoFl W on 2010-08-20
Whenever I try to copy and paste something from Opera to Thunderbird (or FireFox) the copied text does not appear when I select paste.  (or control V)  My work around is to place the copied text into a empty document, re-highlight, copy and then the paste into Thunderbird will work.

Opera Version: 10.61 Build 6430
Thunderbird 3.0.6
System x86_64, 2.6.32-24-generic

Does Opera purposely not get along with Mozilla?  Does anyone else have this problem?

---

### Post by spcwingo on 2010-08-21
Have you tried glipper?  It's a clipboard manager for Gnome similar to Klipper for KDE.  I was having similar problems until I found glipper.

---

### Post by wojox on 2010-08-21
Hey SoFl W 

Do you have both Opera and Thunderbird running at the same time. I've experienced the same problem and found out keeping both applications open worked. If not then +1 to spcwingo advice. 

```
sudo apt-get update; sudo apt-get install glipper
```

---

### Post by SoFl W on 2010-08-21
Both are open but usually Thunderbird is in a different workspace.  I know it copies it, it just doesn't paste it until I put it into another program and re-highlight and copy.  I will research Glipper.

Hope Texas is treating you well Wojox.

---

### Post by jenast on 2010-08-23
I too have the same problem. Copying from Opera to Thunderbird does not work anymore.

Same versions except I use the 32-bit versions.

Not sure if it is Opera's or Thunderbirds's fault though. 

Using  gedit as an intermediate copy-paste station works but is irritating.

---

### Post by Michael_buntu on 2010-08-24
Same problem for me, kubuntu 8.04, but since the beginning of my memories, not only since Opera 10.61. Plus another problem, see below (also ever since)! (my Thunderbird currently 2.0.0.24)

_Problem 1: Opera --> Thunderbird Message composer_
When I copy from Opera, I cannot paste into the message area of Thunderbird directly. Instead, I need to paste it in some "intermediate area", copy it again from there, and then I can paste it to Thunderbird's message composer area normally.

When I just need to paste a single line, I normally use the "subject" or the "To:" field of Thunderbird as "intermediate copy-paste area." This works! Just directly pasting to the message area in Thunderbird fails.

_Problem 2a: OpenOffice Writer --> Opera_
When I copy a word from an OpenOffice Writer document (NOT including any space characters!) and then I paste it to Opera (either Opera URL field or a text form field inside a web page), then Opera adds a space character after the word! Pasting to Firefox works correct.

_Problem 2b: OpenOffice Writer --> Text Editor (Kate, gedit)_
When I copy a word from an OpenOffice Writer document and then I paste it to a text editor, then the editor adds a line break after the word!

_Problem 2c: OpenOffice Writer --> Thunderbird Message composer_
When I copy a word from an OpenOffice Writer document and then I paste it to the Thunderbird message composer window, then I get *two* line breaks, one before and one after the word that I was pasting!

What else is to mention:
[LIST]
[*]All the above happens both with "klipper" running and also after closing  "klipper".
[*]When using the "plain text" message composer window of Thunderbird (you get it when holding the shift key while clicking the "write-new-message" button in Thunderbird), above Thunderbird-specific behaviour (problems 1 and 2c) does NOT occur.
[/LIST]

---

### Post by narcus on 2010-10-29
If anyone else is annoyed with this problem, try right-click in Thunderbird and select Paste Without Formatting instead of ctrl-v. That seems to work for me, though it is still a bit annoying but easier than openening gedit for an intermediate copy/paste.

---

### Post by BasculeTheFule on 2010-11-05
> **narcus said:**
> If anyone else is annoyed with this problem, try right-click in Thunderbird and select Paste Without Formatting instead of ctrl-v. That seems to work for me, though it is still a bit annoying but easier than openening gedit for an intermediate copy/paste.

Nice one - this has been annoying the hell out of me for a while now and this is infinitely better than going via gedit.

Oddly enough I found that you can use the subject line for short pieces of text (small urls for instance), and also the address section too! Presumably that is consistent with this workaround in that Thunderbird automatically strips out the formatting for those fields.

Cheers,

Sean

---

### Post by hernil on 2011-07-06
If anyone should stumble in from Google; try using ctrl+shift+v to paste into Thunderbird. Works for me :)

---

### Post by Frogs Hair on 2011-07-06
I use Opera 11.50 and have no problem pasting into the Firefox browser , but I don't use Thunderbird. ( sorry old thread )

---

### Post by zextra on 2011-11-29
[SOLVED]
The solution is to use xorg xclipboard. It will automatically strip text formatting when you
copy text from anywhere, and you can just ctrl v paste into thunderbird no problem.

If you want to hide the application start it as "xclipboard -iconic" and it will only be in 
the panel. I use openbox with tint2 and in the rc.xml i can then hide xclipboard from
the panel and it is then running silently in the background, which is what i wanted. For
the gnome panel I am sure there are other ways to hide the app from the panel as well.
Enjoy~

---

