---
title: "download whole website..?"
date: 2010-07-26
forum: General Help
---

### Post by OnlineBuddy on 2010-07-26
i am using *FIREFOX*....i want to be download some articles from wikipedia for offline view(100+ pages)...
.
i read a forum where they suggested command(wget)
.
isn't there some (**GUI**) of **firefox add-on**??

---

### Post by AlphaLexman on 2010-07-26
'wget' really is the best / easiest method to grab an entire web site. A gui environment or a plugin for firefox, is more work than just typing the commands into a terminal!

---

### Post by Sub101 on 2010-07-26
Id also use wget, however this plugin looks like what you are after. 

Ive not used it myself though....

[https://addons.mozilla.org/en-US/firefox/addon/7661/](https://addons.mozilla.org/en-US/firefox/addon/7661/)

---

### Post by OnlineBuddy on 2010-07-26
could you please give me the *wget* syntax to save website to a folder on my desktop..?
.
also plugin asks for *firefox* ver >3.5 .. how could i update my firefox...

---

### Post by AlphaLexman on 2010-07-26
I don't normally do other people's homework for them, but I am feeling generous tonight...
```
wget --random-wait -r -p -e robots=off -U mozilla http://www.example.com
```> [Download an entire website]("http://www.commandlinefu.com/commands/view/901/download-an-entire-website")                 
                                      -p parameter tells wget to include all files, including images.
 -e robots=off you don't want wget to obey by the robots.txt file
 -U mozilla as your browsers identity.
 --random-wait to let wget chose a random number of seconds to wait, avoid get into black list.
 Other Useful wget Parameters:
 --limit-rate=20k limits the rate at which it downloads files.
 -b continues wget after logging out.
 -o $HOME/wget_log.txt logs the output
                  

from: [http://www.commandlinefu.com/](http://www.commandlinefu.com/)

---

### Post by OnlineBuddy on 2010-07-27
thanx *man...

cud u also tell me how to upgrade my firefox to 3.5..??

---

### Post by Sub101 on 2010-07-28
> **OnlineBuddy said:**
> thanx *man...

cud u also tell me how to upgrade my firefox to 3.5..??


The current version is 3.6.

Assuming you have firefox installed you can use the update manager - System -> Admin -> Update Manager

or install Firefox from the software center - Applications -> Software Center

Or install from here; [http://www.mozilla-europe.org/en/firefox/](http://www.mozilla-europe.org/en/firefox/)

---

