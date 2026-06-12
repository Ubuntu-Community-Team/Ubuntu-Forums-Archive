---
title: "xbndkeys and mx1000"
date: 2006-06-21
forum: General Help
---

### Post by brownrl on 2006-06-21
The tutorial to get the forward and back buttons working for the MX1000 works fairly ok.

However, some pages when you use the mouse to go back it will go back to the very first page in your history and not just one page. you can see it going like in a loop all the way back.

this is my xbindkeysrc

"xvkbd -no-repeat -text "\[Alt_L]\[Left]""
   m:0x10 + b:8 + Release
"xvkbd -no-repeat -text "\[Alt_L]\[Right]""
   m:0x10 + b:9 + Release

cap L's and cap R's get converted to lower on this forum... very weird...

however, if someone knows what the deal is and why firefox goes crazy all the way back to page 1 then I would thank them very very very much for ridding me of this annnoying bug...

Rob

---

### Post by jrib on 2006-06-21
The xbindkeysrc here [https://help.ubuntu.com/community/MX1000Mouse#head-b12641790e6f0d1a5ea8f83c67e6068a284f62ad](https://help.ubuntu.com/community/MX1000Mouse#head-b12641790e6f0d1a5ea8f83c67e6068a284f62ad) is what I use.  It doesn't seem to give me the problems you mention.

Note that the path to xvkbd has changed in dapper and I'll be updating the guide for dapper later today if you are interested

---

### Post by brownrl on 2006-06-22
Maybe the -xsendevent does the trick I will try that thanks...

Whats even weirder is that when this happens it goes back to the first page that you went to ie google.com but then if you hit forward, it will go all the way forward many pages to the page you were on.

I will post the results of the -xsendevent later.

---

### Post by brownrl on 2006-06-23
It seems the send eent was the key, have not had the problem anymore. Thanks a ton.

---

