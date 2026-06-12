---
title: "Firefox Spellcheck is not working (red underline)"
date: 2011-01-16
forum: General Help
---

### Post by S3loth on 2011-01-16
I was having a problem last week where Firefox would underline a mispelled word, but when right-clicked would not list any suggestions. Beliving it was part of the problem I delete the extention "MultiLinks". After this however, Firefox will neither suggest words, or even underline them. I've tried running Firefox in Safe Mode and even going as far as deleting my .mozilla folder and re-installing Firefox, but nothing is working.

---

### Post by wilee-nilee on 2011-01-16
So, to little information here, are you really runny gutsy gibbon? 

What is the FF release version?

Where is the spell checking not working exactly, and are you getting a spell check option at all, ever, now.

You might explain. what and where this was (MultiLinks), and how you removed it

---

### Post by S3loth on 2011-01-16
Ah sorry but it has been a while since I've posted here. :p I'm running 10.10 and FF 3.6. The spell check doesn't show up anywhere anymore. I even tried changing the about:config option to spell check all forms.

---

### Post by wilee-nilee on 2011-01-16
> **S3loth said:**
> Ah sorry but it has been a while since I've posted here. :p I'm running 10.10 and FF 3.6. The spell check doesn't show up anywhere anymore. I even tried changing the about:config option to spell check all forms.

When you use spellckheck in about:config does it look like this.
[ATTACH]181261[/ATTACH]

I am in the US so mine is set to this dictionary.

---

### Post by S3loth on 2011-01-16
Yes, it looks exactly the same as that.

---

### Post by wilee-nilee on 2011-01-16
> **S3loth said:**
> Yes, it looks exactly the same as that.

To be honest, I didn't know FF had a built in spell checker, I thought that say for example posting here it was a on board or site spell checker, it works so I didn't worry about it. Here is a FF add on though that may be helpful I'm not sure.
[https://addons.mozilla.org/en-US/firefox/addon/spell-checker/](https://addons.mozilla.org/en-US/firefox/addon/spell-checker/)

That is about all my knowledge with browsers, not much.

---

### Post by S3loth on 2011-01-17
That extention does not seem to work either. I just checked in Chrome, and the issue is not present there. Is there some other folder Firefox could be saving information other than the .mozilla folder in my home folder?

---

### Post by lithopsian on 2011-01-19
There is a known bug in recent versions of Firefox (4.0 betas and some late 3.6 versions) with some Linux installations where the wavy line doesn't show up.  The cause is not even known yet, but a workaround is to use one of the other line styles which do apparently show up.  I currently have double underline which isn't my favourite but at least I can see my spelling mistakes.

Bug for you to track:
[https://bugzilla.mozilla.org/show_bug.cgi?id=560124](https://bugzilla.mozilla.org/show_bug.cgi?id=560124)

---

### Post by SoFl W on 2011-01-19
> **lithopsian said:**
> There is a known bug in recent versions of Firefox (4.0 betas and some late 3.6 versions) with some Linux installations where the wavy line doesn't show up.  The cause is not even known yet, but a workaround is to use one of the other line styles which do apparently show up.  

Interesting, I have noticed recently that I will be typing, make a mistake the red wavy line is under the word.  I continue typing to complete my sentence/thought and the red line will be gone.  If I remember the word I can go back delete a letter and add it back the red line will re-appear and I can select the correct word, if the line is not there it doesn't think there is a mistake.  

How does one change the line style for spelling mistakes?

---

### Post by S3loth on 2011-01-19
> **SoFl W said:**
> Interesting, I have noticed recently that I will be typing, make a mistake the red wavy line is under the word.  I continue typing to complete my sentence/thought and the red line will be gone.  If I remember the word I can go back delete a letter and add it back the red line will re-appear and I can select the correct word, if the line is not there it doesn't think there is a mistake.  

How does one change the line style for spelling mistakes?

I believe you need to create a new integer value in about:config named ui.SpellCheckerUnderlineStyle and give it a value from 0 to 5 (or 1 to 4 as 0 is "none" and 5 is the wavy line that doesn't work). However after doing this, still nothing shows up for me.

---

### Post by S3loth on 2011-01-19
...Well this is embarrassing. Somehow the English US dictionary had been deleted from my Firefox setup. Really unsure how that happened. Re-installed it and everything works fine now. Thanks for the suggestions!

---

### Post by SoFl W on 2011-01-20
> **S3loth said:**
> I believe you need to create a new integer value in about:config named ui.SpellCheckerUnderlineStyle and give it a value from 0 to 5 (or 1 to 4 as 0 is "none" and 5 is the wavy line that doesn't work). 

Thank you, and I followed [this link]("http://kb.mozillazine.org/Ui.SpellCheckerUnderlineStyle") to get the information on what each of the values represent.
[http://kb.mozillazine.org/Ui.SpellCheckerUnderlineStyle](http://kb.mozillazine.org/Ui.SpellCheckerUnderlineStyle)
0-none, 1-dotted, 2-Long dots, 3-Single Dots, 4-Double Line, 5-wavy (default)

---

### Post by WaNaBePi on 2012-03-08
[https://addons.mozilla.org/en-US/firefox/addon/united-states-english-spellche/](https://addons.mozilla.org/en-US/firefox/addon/united-states-english-spellche/)

The add on above worked for me. I didn't want to uninstall cause it's a pain to get Java and flash working in 11.10. Horray for bd spling!!!~~11!

---

