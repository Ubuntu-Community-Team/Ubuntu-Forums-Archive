---
title: "Firefox 1.5.0.1 Updated - now doesn't run"
date: 2006-02-02
forum: General Help
---

### Post by urusaiyatsu on 2006-02-02
I have Firefox 1.5 installed in my home directory. After updating to 1.5.0.1 – I run Firefox, the cursor goes ‘busy’ then nothing. It doesn’t run. Can someone clue me in to what I need to do to get it running agin?

Cheers.

---

### Post by jrib on 2006-02-02
try running 'firefox' from a terminal and see if it tells you anything interesting

---

### Post by towsonu2003 on 2006-02-02
also, try running firefox from terminal like this: firefox -safe-mode
if it runs, you've got a problem with your themes or extensions.

---

### Post by urusaiyatsu on 2006-02-07
firefox -safe-mode runs version 1.0.7.

I did get 1.5.0.1 to run by clicking on a link in Thunderbird, but it was screwed and it looks like adblock extension is the culprit. However, I could not access the Extensions pop-up to disable it.

How do I run 1.5 in safe mode if the above runs 1.0.7???

Thanks.

---

### Post by towsonu2003 on 2006-02-07
[QUOTE=urusaiyatsu]
How do I run 1.5 in safe mode if the above runs 1.0.7???
[/QUOTE]
Locate where you untarred (unzipped) your new firefox. Here, I am assuming that you used [http://wiki.ubuntu.com/FirefoxNewVersion](http://wiki.ubuntu.com/FirefoxNewVersion) section 1. If it was something else and you remember the steps (and can't remember where you untarred your firefox), post the steps here and I'll try to make sense of them ;)

ok assuming you used the wiki page: ```
cd /opt/firefox
./firefox -safe-mode

```

---

### Post by urusaiyatsu on 2006-02-07
Thanks for your reply.

Yeah, I ran “firefox-safe-mode” in the directory I untarred 1.5 into, but got 1.0.7. I did not use the “./”. What does this do?

I will have to try this after work...

---

### Post by towsonu2003 on 2006-02-07
[QUOTE=urusaiyatsu]Thanks for your reply.

Yeah, I ran &#8220;firefox-safe-mode&#8221; in the directory I untarred 1.5 into, but got 1.0.7. I did not use the &#8220;./&#8221;. What does this do?

I will have to try this after work...[/QUOTE]
you mean ```
firefox -safe-mode
``` and not firefox-safe-mode right? 

this one refers to /usr/bin or /usr/sbin to locate firefox and runs it from there ```
 firefox -safe-mode
```
this one rus the firefox that is located in your current directory 
```
./firefox -safe-mode
```
./ means "don't look for it elsewhere, the thing I want to execute is where I currently am".

If you really didn't like the look of ./ , you can also use```
/opt/firefox/firefox -safe-mode
``` ;)

---

### Post by urusaiyatsu on 2006-02-07
Haha, no, I like the look of "./" a lot. I just didn't know what it meant!

I'll give that a go and I assume it'll run 1.5 in safe mode.

Thanks for you help.

---

