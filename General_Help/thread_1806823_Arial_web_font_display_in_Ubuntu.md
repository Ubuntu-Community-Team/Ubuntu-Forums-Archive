---
title: "Arial web font display in Ubuntu"
date: 2011-07-18
forum: General Help
---

### Post by Mellifluous on 2011-07-18
I've recently made the switch to Ubuntu. One thing that's bugging me is the way fonts on the web look compared to Windows, Arial in particular.

In the first attachment you'll see a web page screenshot taken using Google Chrome on standard settings in Windows. In the second attachment you'll see the exact same page taken with Chromium on standard settings in Ubuntu. You'll notice that in the 2nd example the text looks more squashed and not as clearly defined, almost very slightly blurred.

I find this quite off-putting and can't find a way to resolve it. Any ideas on what I can do to make it display the same as Windows? Thanks in advance for any help.

---

### Post by SeijiSensei on 2011-07-18
> **Mellifluous said:**
> I've recently made the switch to Ubuntu. One thing that's bugging me is the way fonts on the web look compared to Windows, Arial in particular.

Do you have Arial installed on your system?  If not, the browser will pick the default sans-serif font as the alternate. 

If you have Arial and other MS fonts in a local or network directory, you can install them with the Font Manager in Ubuntu.  Otherwise, you can install the "MS Core Fonts" package which includes Arial, by using 

```
sudo apt-get install ttf-mscorefonts-installer
```

Use the Tab key to highlight the OK choice when the EULA displays on your screen, then hit Enter to continue.

---

### Post by Mellifluous on 2011-07-18
Hi, thanks for the reply. I installed the Microsoft fonts using the software centre. It was a bundle in the Fonts section. I created a document to make sure they were all installed (I don't know how to find the fonts folder in Ubuntu) and they were. I've looked at the settings in Firefox and Chromium but nothing seems to change it. Maybe it's just the way Ubuntu renders those fonts?

---

### Post by SeijiSensei on 2011-07-18
If the website's stylesheet specifies Arial, then that's what the browser will use.  If no font is specified, or a sans-serif font that's not on your system is specified like Helvetica, the *browser's default sans font* is used.

In Firefox, you can set the sans-serif default via Edit > Preferences > Content, then clicking the Advanced fonts button.  If you want to make Arial the default, set it as the sans-serif preference.  I don't use Chromium, but I wouldn't be surprised if there were some equivalent setting there.

---

