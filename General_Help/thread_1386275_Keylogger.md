---
title: "Keylogger"
date: 2010-01-20
forum: General Help
---

### Post by IleaCristian on 2010-01-20
Hello!
First of all I am sorry if i didn't posted in the right section.

Recently I was writing a tutorial on a forum (IT based forum, doesn't matter the url) in the browser. When I pressed the post button it asked me to log in again in my account. I entered my account name and my password and it said successfully logged in. OK! But my tutorial (which was very long and complicated) was gone!!
I almost started to cry , lol.
So I said to myself that I have to avoid this kind of situations in the future. I searched on Google for key-loggers and I got bored.I tried lkl and my system crashed very ugly (by the way, I use Ubuntu 9.10).


So I want some suggestions for a good key-logger with emailing facilities.

---

### Post by Dayofswords on 2010-01-20
> **IleaCristian said:**
> So I want some suggestions for a good key-logger with emailing facilities.
uhhhhh....

---

### Post by IleaCristian on 2010-01-20
ok...mailing facilities optional :))

---

### Post by houseworkshy on 2010-01-20
This isn't an answer to your question but a method I use in similar situations.  I post quite long articles elsewhere and have had similar problems when automatically logged out as I have taken a while.  Some forums will let you choose to be remembered which disables the auto log out.  However I still prefer to write in a word processor partly because it has all the tools such as spell checking but mostly because I like to have a copy locally stored on my machine and do a quick copy and paste to the forum. It is also a safety precaution as some forums let you type as many words as you like and then when you get to click the post button informs you, too late, that there is a word limit...arrrhhh. Untill such time as someone informs you about a keylogger I'd recomend open office writer ( which is free ) as a stop gap.

---

### Post by IleaCristian on 2010-01-20
> **houseworkshy said:**
> This isn't an answer to your question but a method I use in similar situations.  I post quite long articles elsewhere and have had similar problems when automatically logged out as I have taken a while.  Some forums will let you choose to be remembered which disables the auto log out.  However I still prefer to write in a word processor partly because it has all the tools such as spell checking but mostly because I like to have a copy locally stored on my machine and do a quick copy and paste to the forum. It is also a safety precaution as some forums let you type as many words as you like and then when you get to click the post button informs you, too late, that there is a word limit...arrrhhh. Untill such time as someone informs you about a keylogger I'd recomend open office writer ( which is free ) as a stop gap.

I am Admin on that forum and auto log out wasn't enabled.I don't know what happened.
Yes it's a good option(open office).I thought of it too.But the disadvantage is that it doesn't have the bbcodes.

Thanks! But I still accept suggestions...

---

### Post by Maheriano on 2010-01-20
Why didn't you just hit the BACK button?

---

### Post by Xog on 2010-01-20
> **Maheriano said:**
> Why didn't you just hit the BACK button?

I can imagine him saying: FFFFFFUUUUU----

---

### Post by houseworkshy on 2010-01-20
bbcodes as in html?  How about Kompozer, bluefish, or screem.  They are all in the repositories.

---

### Post by IleaCristian on 2010-01-20
> **Maheriano said:**
> Why didn't you just hit the BACK button?

I managed to recover something by hitting the back button but not enough.It kept asking me for resubmission or  smth like that.

> **Xog said:**
> I can imagine him saying: FFFFFFUUUUU----
You can say that again... :roll:

---

### Post by houseworkshy on 2010-01-20
I've just had a quick browse.  Sea monkey might suit; it has several plugins for bbcodes.  You could compose in the editor locally and post when you're done.

---

### Post by darthmob on 2010-01-20
If you write a long post on a forum just copy the code over into any editor (gedit for example). When there is a problem with submitting you can simply paste it back from the editor.

---

### Post by Maheriano on 2010-01-20
> **darthmob said:**
> If you write a long post on a forum just copy the code over into any editor (gedit for example). When there is a problem with submitting you can simply paste it back from the editor.

I always do this. CTRL-A to highlight everything, right-click and COPY. It has saved me more than once.

---

### Post by t0p on 2010-01-20
> **IleaCristian said:**
> I want some suggestions for a good key-logger with emailing facilities.

Well, [here]("http://www.irongeek.com/i.php?page=security/keylogger&mode=print") is a link to the source code for Keymail.  It's for Windows, apparently: but you may be able to use it with linux if your C hacking skills are up to it.

Disclaimer: I've never used it myself.

---

### Post by flabdablet on 2010-01-21
The way I avoid this kind of situation doesn't need a keylogger, just a text editor. Any time I find myself using a web browser text entry box for more than a few minutes, I pop open a Mousepad window, paste in everything I've done, and continue the composition process in there. That way, when (not if) the web does something stupid, I don't lose anything. I also hit Save every few minutes in case my computer does something stupid.

I use Mousepad because it's super-quick to start up, and I've added a launcher to the top panel that makes Mousepad open Documents/scratchpad.txt so I can just use ctrl-S without needing to make up a filename.

---

### Post by IleaCristian on 2010-01-23
Ok...
^^ My C skills are not so good(yet).
I will use openoffice for now.
If I find a neat text editor I'll post it here.
Thanks!

---

### Post by maslow788 on 2010-02-16
I've been looking all over the Internet for a Linux keylogger.  Tried lkl, vlogger, pykeylogger, etc.  lkl doesn't compile on modern Linux OS (Ubuntu 9.10) and the author is non-responsive for over a prolong period of time.  vlogger from thc ... well when I try to compile it, there's a bunch of errors ... it only compiles on kernel 2.14 ... I use kernel 2.16.    And there's pykeylogger ... too many dependencies and when I try to run it, it doesn't work on Ubuntu 9.10.  Maybe it works on other OS but I have to wait for the author update.

Luckily, there's a guy who wrote a keylogger for Linux that works on Ubuntu 9.10 (kernel 2.16).  It's called logkeys.  Works great!!  I compile, sudo make install, logkeys -s -o /var/log/logkeys.log, off I go!

[http://code.google.com/p/logkeys/](http://code.google.com/p/logkeys/)

Now I'm able to monitor my own activity to determine how many characters I type each day :) and not forget what previous typed command.  'history' command doesn't cut it because I usually open 5 to 10 shells at a time.  It only captures the first shell.

Anyways, logkeys is THE keylogger for Ubuntu 9.10 and perhaps for all modern day Linux OS.

---

