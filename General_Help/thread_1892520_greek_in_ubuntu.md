---
title: "greek in ubuntu"
date: 2011-12-08
forum: General Help
---

### Post by Lilykos on 2011-12-08
hello everyone, quick question because google didnt help me at all....i am not able to read greek on ubuntu in various cases.i have a txt file and i cant read it neither on gedit nor at libreoffice, althogh i have tried with various codecs.likewise, some older pages on firefox just show gibberish.is there a universal encoder that can help me?unicode utf-8 doesnt help unfortunately...thanks in advance!

---

### Post by bryncoles on 2011-12-08
Hi Lilykos.  

I have previously found that opening the Greek file in Libre Office makes Libre Office ask what encoding you want to use.  You probably want to use ISO-8859-7, which is the Greek character set.  

Alternatively if you want to open the file in Gedit use the command line.  

Open a terminal and cd to the directory where the .txt file is. If the file is on the Desktop, you would do 

```
cd ~/Desktop
```

Then type
```
gedit --encoding ISO-8859-7 &#917;&#955;&#945;&#948;&#945;.txt &
```

(Assuming the filename is &#917;&#955;&#945;&#948;&#945;.txt) Then the file should open, and be readable.  The '&' at the end means that the terminal can then be used for other actions after opening the text file.  

I also think (if memory serves correctly) is you then use 'save as' to save the document, you can specify the system default encoding (unicode or utf8 or some such) and be able to open the file normally in future.

***edit***

Just saw you tried Libre Office!  Also, you have Greek language support installed, right?

***edit 2***

If you get an error message, rather than success, post the error here (of course)

---

### Post by Lilykos on 2011-12-08
thank you very much this was actually a great help with the txt file!however i tried to use the same encoding in firefox and the problem persists.dont get me wrong, it is not a main problem, it doesnt appear on newer sites, however i believe it happens with older websites(i think) like this one, which was the reason i opened the thread[ http://www.it.uom.gr/project/cppmanual/cplman/index.htm]("http://www.it.uom.gr/project/cppmanual/cplman/index.htm") 

thanks again for your help!

//or this one here [http://www.it.uom.gr/project/html2/main.html](http://www.it.uom.gr/project/html2/main.html) . any ideas?

//i tried it on libreoffice and it works like a charm!i think that with greek encoding there is no problem with english characters, is that correct?

//confirmed, this encoding you suggested shows gibberish on firefox :(

---

### Post by bryncoles on 2011-12-08
The first page loaded fine for me.   The second page... I see your problem.  Now try this (which I have only just discovered)

Go to [http://www.it.uom.gr/project/html2/main.html](http://www.it.uom.gr/project/html2/main.html).  

Click Firefox's 'view' menu.  Then 'character encoding' sub menu.  The select 'Greek ISO-8859-7'.  If the option is not present, then try adding it with 'customise list'.  

Any luck?

***edit***

Oh, and there shouldn't be any problems with English characters, just cause you're using the Greek encoding.  I've never had an issue, anyway...

---

### Post by Lilykos on 2011-12-08
thank you that kind of solved the problem, i was just wondering if there was a more permanent solution....but its alright, one cant have it all! thanks a lot for your time pal!cheers!

---

### Post by bryncoles on 2011-12-08
Best I can do, at least you can read all that lovely Greek now!

If you're happy with this solution, perhaps mark the thread as 'solved'?  ;-)

---

### Post by Lilykos on 2011-12-08
i have done that, doesnt it show up?

---

### Post by bryncoles on 2011-12-08
Po!  Yes!  And I was doing so well... ;-)

---

