---
title: "Nautilus setting crashes nautilus ..."
date: 2011-03-30
forum: General Help
---

### Post by An Sanct on 2011-03-30
If I choose the option on the screenshot (Open each folder in its own windows), Nautilus starts to crash without reason.

Can anybody confirm this?

PS. If anybody is going to check this out and get the same crashing as I did, the way to turn it off is to open a Nautilus window, in the menu click "Edit" and use the arrow keys, to navigate to Preferences.

---

### Post by Krytarik on 2011-03-30
No, it doesn't crash if I enable those option, and it works like expected. I'm running Lucid 10.04, like stated.

Greetings.

---

### Post by An Sanct on 2011-03-31
Okay, I've tested it on a vanilla Ubuntu 10.10 virtual machine, clean install 

... It also doesn't crash ... 

So my question is: How to find out why it does and what could cause it to crash?

---

### Post by Krytarik on 2011-03-31
You don't happen to have Nautilus Elementary running, right?
The current version of vanilla Nautilus provided by the official Maverick repos is "2.32.0-0ubuntu1.3".

Trigger those crash again, then check "~/.xsession-errors" for error messages.

You can use this command to easily disable those option again:
```
gconftool-2 /apps/nautilus/preferences/always_use_browser --type bool --set false
```

---

### Post by An Sanct on 2011-03-31
I've read about Nautilus Elementary, while fixing it from another computer.

*Should* I have Nautilus Elementary installed?

---

### Post by Krytarik on 2011-03-31
> **An Sanct said:**
> 
*Should* I have Nautilus Elementary installed?
No, actually not. I tried it twice, but it keeps having a graphical issue when scrolling.

I just wanted you to check if it is installed.

---

### Post by An Sanct on 2011-03-31
I've done a reinstall just a month ago. I'm sure Its not installed (I never installed it)

Is there a simple way to check, so I can post a picture or paste the result?

The next post will be the "~/.xsession-errors" thing ... since I pinpointed the *One* setting, causing this ...

Edit: I sudo gedit-ed "~/.xsession-errors", cleared it, saved, closed
Made it crash and the file is still empty :confused:

---

### Post by An Sanct on 2011-03-31
I'm kind of playing with the idea to install nautilus-dbg, finding the culprit and posting a bug ... but I don't feel up to it yet ...

---

### Post by An Sanct on 2011-03-31
Argh ... In nautilus under help>about, I see 
"Nautilus **Elementary** 2.32.2 ... Nautilus patched for simplicty"

So .. how do I install the non Elementary nautilus?

---

### Post by Krytarik on 2011-03-31
To 'downgrade' "nautilus" and "nautilus-data" to the vanilla version, simply run:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```

---

### Post by An Sanct on 2011-04-01
I ran the two commands and still have Nautilus Elementary

Also, maybe a hint, I never added the mentioned PPA - the "monkeyd" thing.

PS. crashes still occur.

---

### Post by Krytarik on 2011-04-01
> **An Sanct said:**
> I ran the two commands and still have Nautilus Elementary

Also, maybe a hint, I never added the mentioned PPA - the "monkeyd" thing.

Did you at least restart nautilus? Sorry, I didn't mention it.

I'm wondering how you came to it then. But you also don't know, right?

Please check the repos in "System -> Administration -> Software Sources -> Other Sources", you may post a screenshot.

You can also downgrade them manually by "forcing" down their versions, but you have to be really careful, because it sometimes wants to remove "ubuntu-desktop" altogether:
- open Synaptic
- search for "nautilus"
- first click at "nautilus-data"
- click in the menu at "Package", then choose "Force Version..."
- choose the next lower version, in your case listed as "maverick-updates"
- at this point, it should say that "nautilus" will also be downgraded
- accept it, then apply the changes

If that way around doesn't work, try the other way around.

When done with the downgrade, check if Synaptic wants to upgrade them again!

When it's finally finished, restart Nautilus by pressing Alt+F2 and entering "killall nautilus", before make sure that there is no active browser window.

---

### Post by An Sanct on 2011-04-01
I checked the PPAs and was baffled to see the "mokeyd" thing there ... I removed both, then did the downgrades with Synaptic, both nautilus and nautilus-data, restarted and now the crash disappears.

Thank you Krytarik!:P

PS. No, I really don't know how those PPAs came into my list ... :confused:

---

### Post by Krytarik on 2011-04-01
> **An Sanct said:**
> 
PS. No, I really don't know how those PPAs came into my list ... :confused:
Quite a lot theme authors recommend installing/using Nautilus Elementary, and include the respective commands into their install instructions.

---

### Post by An Sanct on 2011-04-01
hm ... I have no *special* theme installed tho ... Compiz and no other eye candy ...

Nun ja, danke für deine Hilfe ;)

MFG!,
Sanct

---

