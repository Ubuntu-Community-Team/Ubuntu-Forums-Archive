---
title: "Kile &amp; Okular question"
date: 2011-07-14
forum: General Help
---

### Post by 71GA on 2011-07-14
Hello.

I am using Kile, to edit LaTeX documents and every time i click on 
build button Kile opens Okular which shows my .pdf. Problem begins, when i do this multiple times, as Kile opens another Okular for same document everytime i click build button. 

I end up having 1 pdf opened multiple times and it is getting on my nerves. 

Is there any way i can make Kile open only 1 Okular window and updates it when i click on build button?


Ty Žiga

---

### Post by mukl on 2011-07-14
Use the "PDFLaTeX" button in the "Build" dropdown. Okular always updates when a file changes.

---

### Post by 71GA on 2011-07-14
> **mukl said:**
> Use the "PDFLaTeX" button in the "Build" dropdown. Okular always updates when a file changes.
Well that is THE button i click all the time, but i get many Okular windows...

---

### Post by dragonfly41 on 2011-07-14
From another site .. it seems that to launch multiple sessions the [COLOR=DarkRed]--unique[/COLOR] argument is used

*[COLOR=DarkRed][FONT=Sans Serif]R[/FONT][FONT=Sans Serif]un Unique/Multiple Instances of Okular [/FONT][/COLOR]*
*[COLOR=DarkRed][FONT=Sans Serif]Usually, when you open PDF files in Okular, it opens in the same okular window all the time. However there are times when you want to refer to more than one pdf file at the same time and would need multiple instances of the software to run. The way to get Okular to run unique instances is by firing it with the [/FONT]--unique[FONT=Sans Serif] argument.[/FONT][/COLOR]*
*[COLOR=DarkRed][FONT=DejaVu Sans]okular --unique[/FONT][/COLOR]*
*[COLOR=DarkRed][FONT=DejaVu Sans]You could also put this in your .bashrc or .bash_aliases if you want it as a permanent fix.[/FONT][/COLOR]*
*[COLOR=DarkRed][FONT=DejaVu Sans]alias okular="okular --unique" [/FONT][/COLOR]*


So perhaps you might try to remove this argument in the command that launches okular?

---

### Post by 71GA on 2011-07-14
Thanks

---

### Post by CapnKirk on 2011-12-12
[Using Kile 2.1.0]

This solution did not work for me because okular was not being invoked with the "--unique" parameter. Nevertheless, I was getting multiple instances of okular.

What did work is the menu item "Build->Watch file mode". This is a toggle. And one has to have already an occurrence of okular running. So it's a bit of a pain to (1) run quickbuild and get an okular instance of the resulting pdf and (2) toggle the "Watch file mode". Then if one shifts to another file/project, one must turn off the Watch File mode, get an okular instance of the pdf and then turn the Watch File mode back on. I wish the mode was smart enough to recognize that no pdf of the file/project was running and create one, then update it as you go.

Hope this helps someone.

Kirk

---

### Post by 71GA on 2011-12-13
> **CapnKirk said:**
> [Using Kile 2.1.0]

This solution did not work for me because okular was not being invoked with the "--unique" parameter. Nevertheless, I was getting multiple instances of okular.

What did work is the menu item "Build->Watch file mode". This is a toggle. And one has to have already an occurrence of okular running. So it's a bit of a pain to (1) run quickbuild and get an okular instance of the resulting pdf and (2) toggle the "Watch file mode". Then if one shifts to another file/project, one must turn off the Watch File mode, get an okular instance of the pdf and then turn the Watch File mode back on. I wish the mode was smart enough to recognize that no pdf of the file/project was running and create one, then update it as you go.

Hope this helps someone.

Kirk

Thanks. It is a nice add to this thread.

---

