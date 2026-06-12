---
title: "crazy firefox"
date: 2010-05-23
forum: General Help
---

### Post by YoshiroShin on 2010-05-23
ok, long story short: 

I installed the Spanish (spain) dictionary add on for firefox and suddenly my right click > languages menu for spell checking is loaded to the nuts with choices of dictionaries for every kind of spanish from cuban to venezuelan. 

Moreover, English US and English UK both appear twice. I disabled and then even uninstalled the spanish dictionary add on and also restarted my browser a couple times and even restarted my computer, but all the spanish dictionary choices are still in the menu! 

How can I fix this? Thanks.

:confused:

---

### Post by jamesisin on 2010-05-23
If you don't have any luck here, you may want to ask your question on the Mozilla forums.

---

### Post by YoshiroShin on 2010-05-23
hold on, I just remembered that to install the spanish dictionary for openoffice I used this command: "sudo apt-get install myspell-es". This installed every variety of spanish dict. for openoffice and maybe also invaded firefox too. How can I reverse that command?

---

### Post by YoshiroShin on 2010-05-23
wow, alright I just did "sudo apt-get remove myspell-es" and the spanish dicts. are all gone now. Now how bout removing the doubled Australian, UK, and US dicts.?

---

### Post by YoshiroShin on 2010-05-23
Actually for Australian, US, and UK I don't have any extensions installed. It's only in Myspell. I went into Synaptic and uninstalled the Australian dictionary. In OpenOffice it disappeared accordingly, but in Firefox not one but both Australian dictionaries disappeared! 



  When I reinstalled the Australian myspell dictionary, two australian dictionaries reappeared in Firefox! 



  Why is this happening?

---

### Post by YoshiroShin on 2010-05-23
Okay so basically I used Synaptic to remove all of the Myspell and Hunspell dictionaries and filled in the blanks manually with Firefox and OpenOffice extensions. But the mean issue persists: why did myspell and hunspell create multiple entries for certain dictionaries in Firefox's right click menu?

Help would be quite appreciated.

---

### Post by YoshiroShin on 2010-05-23
I have a theory on why this is happening though: maybe Myspell and Hunspell both use the same installed dictionaries and seeing as Firefox uses both Myspell and Hunspell, then if you have Myspell's US dictionary installed then it will also register with Hunspell and Firefox will hence make two entries. However this isn't consistent with the South African English dictionary which was installed for Myspell (before I removed it) or the Spanish one (there were just a lot of varieties of spanish installed). It only explains Australian (myspell), UK (myspell), and US (hunspell)...

Any thoughts?

---

### Post by jamesisin on 2010-05-24
Not a one.  You may still want to try the Mozilla forums to see if those cats can offer any insight.

---

### Post by YoshiroShin on 2010-05-24
I did. One person directed me to "usr > lib > firefox(version) > dictionaries" to remove any .dic and .aff files manually that I don't need.
The link to the issue on Mozilla forums is this:
[http://support.mozilla.com/en-US/forum/1/680799](http://support.mozilla.com/en-US/forum/1/680799)

I'll check out the effect of installing a Myspell dictionary on the dictionaries folder...

---

### Post by YoshiroShin on 2010-05-26
Okay guys, I've figured it out! The problem is this:

After I installed the Australian English myspell dictionary through Synaptic as a test, I found that (as expected from before) there were now two Australian English entries in Firefox's right-click menu when there should've only been one;

So then I went to /usr/lib/firefox-3.5.9/dictionaries **and I found something very peculiar** - there were two files named en_AU, one of them being a ".aff" and the other a ".dic" as expected (so en_AU.aff and en_AU.dic), *however, *there were two more files with those exact names beside them: en_AU.aff and en_AU.dic, and these latter two were **links** to the former two in the same folder! 

This is how both the first set and the duplicate set were able to coexist in the same folder and hence why Firefox created two Australian English (as well as US, UK, etc.) entries!

So that's what the problem was. One question still remains which may not be answered for a long while: *why were the duplicate entries created?*

Who knows? Either way I'm satisfied now. :)

---

### Post by jamesisin on 2010-05-26
That's priceless.  I would not ever have guessed that.  Good to know.

---

### Post by pabloab777 on 2011-04-30
I had the same problem, a lot of dictionaries to choose but a few available to remove from Firefox.

In my case, on /usr/lib/firefox-3.6.16, "dictionaries" is a symbolic link to "/usr/share/hunspell"

**SOLUTION:**
[LIST]
[*]Browse as root this folder, "/usr/share/hunspell"
[*]Remove all unusefull symblinks
[/LIST]

Also you could for e.g. ```
sudo apt-get remove --purge hunspell-en-ca
```

---

