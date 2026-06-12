---
title: "rhythmbox-youtube plugin"
date: 2010-09-06
forum: General Help
---

### Post by mithereal on 2010-09-06
Has anyone had luck with getting this plugin to work
i put it in the correct dir and it is seen but it always gives me error 
ImportError: No module named youtube

(rhythmbox:7116): Rhythmbox-WARNING **: Could not load plugin youtube


(rhythmbox:7116): Rhythmbox-WARNING **: Error, impossible to activate plugin 'YouTube Browser'
^Z
[2]+  Stopped                 rhythmbox

any suggestions on how to fix this??
directories xtracted to are ~/.gnome2/rhythmbox/plugins/rhythmbox-youtube and /usr/lib/rhythmbox/plugins/rhythmbox-youtube
mithereal

---

### Post by int2ag0n on 2010-10-20
The plugin for me  , the first time i installed it , used to load . I was also capable of viewing the plugin in rhythmboxes window. However the search didnt fetch anything ,not even once . So i decided to uninstall it because i didn't found any relevant info about my problem . After 3 monthes , i decided to give a try , so i installed it again (yesterday). Now i face the same problem as you. "Could not load plugin youtube blah blah blah". 
Apart from not loading , problem is that the error message of rhythmbox doesnt help much to identify the problem. So i used the following command in a terminal (that supposed to give debug info) but with no help.
```
$ rhythmbox -d 
```

I doesn't give any additional info for the problem.
I'm gonna start putting debugging info in the plugins code , and see what happens .

---

### Post by Lylex11 on 2010-12-02
I have the same issue, would love a fix for this. The link in rhythmbox sent me to gitorious but I got lost at that point [http://gitorious.org/rhythmbox-youtube]("http://gitorious.org/rhythmbox-youtube")

---

