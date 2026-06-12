---
title: "iBus just doesn't cut it"
date: 2011-04-08
forum: General Help
---

### Post by james.wilde on 2011-04-08
Sorry, but now I've found an area where linux - or at least Ubuntu - just isn't in the game: inputting Chinese into documents.  I've spent half a day trying to get iBus and SCIM to work, and not getting anywhere.

For those who don't yet understand, iBus and SCIM are alternative methods of entering western letters and being able to input a Chinese character in a document.  It also works for other languages, like Japanese and Vietnamese, but I'm into Chinese, specifically Simplified Chinese.

On my Mac, I configured the machine for Chinese input and it just worked.  Even on my wife's Windows machine, I configured the machine for Chinese input and it just worked.  Not so on my linux - Ubuntu 10.04 - box.  It just didn't work.

Nineteen times out of twenty I couldn't get the keyboard icon to display.  When I did, I couldn't get it to select an input method (except once).  And that once I couldn't get it to input anything.  Most of the time it let me know that there was no input window, although I had both LibreOffice and Gtext windows open.

Sorry, but I'll try again in a few years.  It's going to take at least that long to make iBus and SCIM work.

Normally I find that if I can do it on the Mac or in Windows, I can do it in linux, but this is one area where there's a lot of work yet to be done.

---

### Post by sanguinoso on 2011-04-08
&#22320;&#23398;&#29017;&#22478;&#27161;&#22478;&#27161;&#22478;&#27161;&#26118;n./xz&#37504;,m/z&#26152;&#27161;&#20043;&#20107;&#22686;'&#26152;. Worked perfectly for me (sorry if any of that was insulting I don't know Chinese). I used this guide here:
[http://lichao.net/eblog/how-to-input-chinese-cjk-in-english-ubuntu-9-10-200911429.html](http://lichao.net/eblog/how-to-input-chinese-cjk-in-english-ubuntu-9-10-200911429.html)

Is it possible that your indicator applet is just not there on the top bar? Also you can see if ibus is even running with ```
ps aux | grep ibus
``` And paste the results here.


> Sorry, but I'll try again in a few years. It's going to take at least that long to make iBus and SCIM work. People on this forum are here to help solve problems and not listen to you whine. iBUS works for me and it doesn't for you which means its either some bug or a configuration problem. Which the good people on this forum could help you solve.

---

