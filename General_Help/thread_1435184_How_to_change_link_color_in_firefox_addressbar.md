---
title: "How to change link color in firefox addressbar"
date: 2010-03-21
forum: General Help
---

### Post by alket on 2010-03-21
How to change link color in firefox addressbar

---

### Post by mechro on 2010-03-21
I'm not sure but in firefox try **Edit > Preferences > Content > Fonts & Colours > Colours > Link Colours**

---

### Post by colorlessprism on 2010-03-21
after looking around in wiki i found this page:
[http://www.wikihow.com/Custom-Colorize-Firefox](http://www.wikihow.com/Custom-Colorize-Firefox)
it seems to have a number of different fixes, it seems (according to the wiki) you will need to install this unsigned addon [http://webdesigns.ms11.net/chromeditp.html](http://webdesigns.ms11.net/chromeditp.html). 

however you should also to able to get what you need by going:
~/.mozilla/firefox/73p4jdmd.default/chrome (this is my path ymmv)
ensure firefox is not running and rename the "userChrome-example.css" to "userChrome.css" and open it with a  text editor (i prefer gedit). Paste the following code at the bottom:

"#urlbar { background-color: #00FF00 !important; color: #000FFF  !important; }
#urlbar[level] .autocomplete-textbox-container >* {
background-color: #FFFFB7 !important;
}"

i have not tested this but you should have enough information to get  started, i should also point out mozilla "warns you about voiding your  warranty, and changing setting could cause stability problems, security  issues, and performance issues so back up your profilem before attempting an edit....good luck

edit - nevermind i see now the answer your were looking for

---

