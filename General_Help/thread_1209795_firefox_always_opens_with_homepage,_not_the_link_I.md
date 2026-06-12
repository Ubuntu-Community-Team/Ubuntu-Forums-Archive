---
title: "firefox always opens with homepage, not the link I clicked"
date: 2009-07-10
forum: General Help
---

### Post by publife on 2009-07-10
Can anyone help with this?  If I click on a link in an email (or anywhere else) I expect the browser to open that link, but instead it opens my home page every time?

Using: 
Firefox 3.5 / Shiretoko
Linux Mint Gloria (Jaunty)

I'm sure it's something simple but googling has got me nowhere.

---

### Post by publife on 2009-07-10
If it helps, it always opens a new instance as well instead of a new tab or replacing whatever is in the open browser window..

---

### Post by jonobr on 2009-07-10
I found an interesting post of someone complaining to someone else that they didnt google the answer

I think the answer to your question may be in there assuming your using tbird also?

Heres the salient point of the thread

>   
 1.  Close Thunderbird (it writes over prefs.js on close)
   2. Open prefs.js in your favorite text editor. (Should be ~/.thunderbird/blahsaltblah/prefs.js or maybe ~/.mozilla/thunderbird/...)
   3. Add the following line:
      user_pref("network.protocol-handler.app.http", "/usr/local/firefox/firefox");
      (You can add it alphabetical order, but I don't think it matters.)
   4. Open Thunderbird (it reads prefs.js now, go figure)
   5. Click on a link!


NOTE before modifying any file, make a backup of that file

in this case cp prefs.js pref.jsbkup

if you mung up your file just replace it 
cp pref.jsbkup prefs.js

---

