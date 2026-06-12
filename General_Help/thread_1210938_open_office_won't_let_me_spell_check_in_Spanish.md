---
title: "open office won't let me spell check in Spanish"
date: 2009-07-12
forum: General Help
---

### Post by shateredsoul on 2009-07-12
Hi.. So i'm trying to get Open Office to Spell check a power point on a windows machine in Spanish.  I downloaded and installed a Spanish(Mexico) dictionary and tried doing a spell check but it's in English (USA).  I changed the language of the document to Spanish (Mexico) and then right clicked on words that are underlined and it gives me english suggestions.  What gives?

I tried it also with the built in Spanish (Spain) and it still refuses to spell check in Spanish. When I spell check i switch it to Spanish.. it does a spell check on one word in spanish and then reverts to english for the next word.  Any ideas? I'd appreciate any help.

Yup it's on a Windows machine, it's all i have for tonight =).

I'd appreciate any help or pointers... i'm stumped.

---

### Post by Hukei on 2009-07-30
> **shateredsoul said:**
> Hi.. So i'm trying to get Open Office to Spell check a power point on a windows machine in Spanish.  I downloaded and installed a Spanish(Mexico) dictionary and tried doing a spell check but it's in English (USA).  I changed the language of the document to Spanish (Mexico) and then right clicked on words that are underlined and it gives me english suggestions.  What gives?

I tried it also with the built in Spanish (Spain) and it still refuses to spell check in Spanish. When I spell check i switch it to Spanish.. it does a spell check on one word in spanish and then reverts to english for the next word.  Any ideas? I'd appreciate any help.

Yup it's on a Windows machine, it's all i have for tonight =).

I'd appreciate any help or pointers... i'm stumped.

Hey, I was also trying that out on Ubuntu 9.04 (64 bit) but for Spanish for Puerto Rico and I found the add-on (or similar one) that you mentioned for Open Office on the official site and got it to work. I really don't know if it's the same procedure to get this working on windows but you can try the following to see if it works.

To install the extension from [here]("http://extensions.services.openoffice.org/node/1307") and get it to work with Open Office 3.0 follow these steps:

1. Click on "Get it!", and wait for the browser to start the download (or click the direct link to download the file).

2. Once the download has finished, open the file ( it should be an *.oxt file). Then Open Office should ask "Your are about to install the extension "Diccionarios para Mexico", click "OK" to proceed. You have just installed the extension, but there's still the worst part... getting it to work.

3. Now to get this extension to work go to: Tools > Language > For All Text > "More...". Once you have clicked on "More..." change the Locale setting to Spanish (Mexico) and press OK.

4. Now to get the spell check to work, look at the very bottom of the Open Office Writer window, from left to right you should see some boxes in the following order:

[INDENT]1. Page 1/1 (The number of pages)
2. "Default", and
3. English (US) - or another language.[/INDENT]

5. Now select all the text on the document (or press Ctrl+A) and  on the third box from left to right, click on the current language and change it to "Spanish (Mexico)". By now, if you had written any spanish word wrong, you should see a red line underlining them, and if you right-click the word, you should see the spell check doing its job!!

I hope this was easy to understand! If you still have trouble, don't hesitate to leave a reply!

---

