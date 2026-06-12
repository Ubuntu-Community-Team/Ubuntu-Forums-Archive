---
title: "Libreoffice, no spell check?"
date: 2012-05-09
forum: General Help
---

### Post by Zukaro on 2012-05-09
How do I add spell/grammar check to Libreoffice?  On Windows it seems to come with it but on Ubuntu it doesn't seem to work.  Even when clicking on the spell check button it says there's nothing wrong (even when I have obviously misspelled words).

I've been looking around on Google for awhile and haven't found anything yet.

---

### Post by Kobnar on 2012-05-09
I *just* got on this forum to try and search for a better spell checker. I've been using Linux for about a decade now, and I still can't believe that the spell check software is so horrible. I have to double check pretty much every word w/ Google because things that are clearly wrong show up as peachy keen, or totally legit words will be broken up for no reason (eg: words like "recalculate" will commonly be red-flagged with suggestions like "re calculate")

It's ridiculous.

---

### Post by Kobnar on 2012-05-09
So I just did some checking and it turned out that for whatever reason my computer defaulted to having like 3 languages installed and none of them were for us english.

Anyway, try opening up semantic package manager and look for "myspell-en." Uninstall any packages that aren't your default language and check to make sure your default is (mine was "myspell-en-us" for example).

Just restarted LibreOffice and finally all my stupid mistakes are showing up.

---

### Post by Kobnar on 2012-05-09
Also, try going to Tools > Spelling and Grammar > Options, then un-select any languages that aren't your default. For whatever reason, my computer was checking for Australian, UK English and Slovenian all at the same time.

---

### Post by ubuntu27 on 2012-05-09
You have to install the appropriate spell checker and their dictionaries.
Which language do you want it to spell check?


Let's say that you want to have a US English spell checker.
then you have to install
**hunspell-en-us**
**aspell-en**
**wamerican** 

now, this is important. the Dictionary Word file (W) is where words are stored. And they are divided into sizes or categories. They are:

**wamerican** ---
**wamerican-small**
**wamerican-large**
**wamerican-huge**
**wamerican-insane**

Now, the bigger the Dictionary Word is, the more words you will be able to spell check, but there is down size to this. The bigger the words are, the more likely it will include words that are extremely uncommon, possibly archaic, and also there might be words that are considered invalid words.

So, it is your choice in which one to use. Thankfully you can install as many as you want.

The same applies for British English and Canadian English

**wbritish**
**wbritish-small**
**wbritish-large**
**wbritish-huge**
**wbritish-insane**

**wcanadian**
**wcanadian-small**
**wcanadian-large**
**wcanadian-huge**
**wcanadian-insane**

SPANISH:

**wspanish**

---

### Post by Kobnar on 2012-05-10
You, sir, have vastly improved my quality of life.

I thank you.

---

### Post by Zukaro on 2012-05-12
I've installed wcanadian-insane; how to I enable it?
(what I did was sudo apt-get install wcanadian-insane in the terminal to get it; I'm not sure how to get it working in LibreOffice though as it doesn't seem to be working)

---

### Post by wilee-nilee on 2012-05-12
You want to go to the libreoffice site and download their extensions, then go to tools-extensions in libreoffice and add them.

---

### Post by colin.p on 2012-05-12
I never knew that spell-check didn't work until I read this thread, then when I checked LibreOffice, no spell-check. I tried the suggestions here but still no-go. I did a Google search and found this, which worked for me:
[http://listarchives.libreoffice.org/global/users/msg00065.html](http://listarchives.libreoffice.org/global/users/msg00065.html)

It seems that even if there was a listing of a dictionary (en-canadian) by default, apparently it wasn't installed

---

### Post by ubuntu27 on 2012-05-12
I am no expert, but the ReadMe file for Word-List says:

"Please use 'select-default-wordlist' superuser script
to change your selection.

Note that you will need to run that script and select
the 'manual' option if you want to play with symlinks
yourself."


So, what we have to do is to run the "select-default-wordlist" script.

The script can be found at /usr/sbin/


So, what we have to do is to Open the terminal and navigate to the sbin directory by:

```
cd /usr/sbin
```

Now, we are going to execute the script

```
sudo select-default-wordlist
```

And now select your dictionary ;-)


Hope that helps. And if someone has additional input and tips, they are welcome :popcorn:

---

### Post by wilee-nilee on 2012-05-12
[http://extensions.libreoffice.org/](http://extensions.libreoffice.org/)

---

### Post by sierra1bravo on 2012-07-15
As much as I am thankful to the LO team for their much-valued work on LO, I must state that that condition of spell-check in LO is absolutely *insane*.

As someone who has been using various flavors of Linux since 1997, this is the first time that I was tearing my hair out in frustration, trying to install such a basic functionality as spell-check.

Why can't the LO team install one language (say, en-US), by default, and ensure that LO works out-of-the-box with that one language? For users of other languages, it would be clear that they have to install only the dictionaries...not start ab-initio on a wild-goose chase.

cheers and apologies for venting...




s1b
[Still trying to install spell check on a fresh 12.04 install]

---

### Post by Zukaro on 2012-08-15
I finally figured it out (with the help of a few comments on this thread :P).
Go to [http://extensions.services.openoffice.org/en/dictionaries](http://extensions.services.openoffice.org/en/dictionaries), download a dictionary; then in Libre Office go to Tools > Extension Manager and add it into there (you just save the file to your desktop or where ever and then add it to the extension manager).

---

### Post by mark q on 2013-04-19
In my case the spell-check option to enable my language of choice was not present.

The dictionaries were installed so the problem was with the office programme.

This was remedied by the following :

1. killall soffice.bin

2. rm -r .config/libreoffice/

3. Start Libreoffice & go to Tools->Options-> Language Settings -> Default language for documents: English UK (now with spell check icon)

I hope this helps!

PS: For english uk I have libreoffice-l10n-en-gb and myspell-en-gb installed.

---

### Post by shievaniupadhyay on 2013-10-26
this so totally worked. thank u so much. i just created an account to thank u back. i was that troubled with no spell checks.

---

