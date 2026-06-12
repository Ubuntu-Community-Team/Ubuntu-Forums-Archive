---
title: "copy &amp; paste doesn't stay copied &amp; pasted"
date: 2012-01-03
forum: General Help
---

### Post by missmoondog on 2012-01-03
why doesn't the copy & paste feature STAY copied once i leave a page?

what i mean is when i copy something from one page and go to another, the paste part is not there. i have to go back to original page copy it again and then either open a new tab or page and then go to page i want to paste it to, for it to work.

and example would be like this. say i want to copy a link from one page and mail it to someone. i use gmail and yahoo, so if i copy something like a weather page link and want to mail it to some one, i have to leave weather page open, open new tab/window, go to yahoo or gmail, go back to weather page tab/window and copy the link, then go back to tab with yahoo or gmail open and paste it. if i try to copy & paste weather link and go to either yahoo or gmail in same window, the paste feature is gone.

did i confuse the heck out you? i just did myself!!  :o

thank you

---

### Post by westie457 on 2012-01-03
> **missmoondog said:**
> why doesn't the copy & paste feature STAY copied once i leave a page?

what i mean is when i copy something from one page and go to another, the paste part is not there. i have to go back to original page copy it again and then either open a new tab or page and then go to page i want to paste it to, for it to work.

and example would be like this. say i want to copy a link from one page and mail it to someone. i use gmail and yahoo, so if i copy something like a weather page link and want to mail it to some one, i have to leave weather page open, open new tab/window, go to yahoo or gmail, go back to weather page tab/window and copy the link, then go back to tab with yahoo or gmail open and paste it. if i try to copy & paste weather link and go to either yahoo or gmail in same window, the paste feature is gone.

did i confuse the heck out you? i just did myself!!  :o

thank you

Clear as mud. LOL

Just tried copy & paste via right-click, works okay here on Gmail in Meerkat, as does highlight to copy and middle-click to paste. Absolutely no help to you at all as I do not know what causes your issue. 

Hope somebody can though just in case this happens to me in the future and it has been solved by then.

---

### Post by mike555 on 2012-01-03
What you need is a clipboard manager running all the time like "clipman" or one like that, if you copy pictures you would need a clipboard program that does pictures (not just text).

---

### Post by neu5eeCh on 2012-01-03
I had this problem in earlier versions of Ubuntu & Xubuntu (pre 11.04). At the time, I installed Parcellite and that solved the problem. But wouldn't it be nice if some things just worked? ;-)

Here's [a useful link]("http://www.webupd8.org/2010/08/best-linux-clipboard-manager.html") if you haven't been googling already.

---

### Post by MartijnNL on 2012-01-03
I think the OP means that she's on a webpage, copies something on that page, then loads a new site (yahoo/gmail) in the SAME tab and then tries to paste the content into that new page. So the original page is no longer present when the paste action takes place. Which doesn't seem to be working for her.

I just tried this in Firefox 9.0.1 under Xubuntu 10.10 and it works fine.

What browser (and version) and Ubuntu version are you using?

Edit: I noticed Xubuntu has xfce4-clipman installed, so that may be why it's working for me.

---

### Post by mcduck on 2012-01-03
Linux desktops don't usually actually use a clipboard, the copy/paste is done directly between applications so you need to still have both source and destination open for it to work. This is probably because the traditional way to do this on Linux is actually primary selection instead of clipboard or cut buffers. (This way also allows some nice extra features a clipboard-based system wouldn't be able to handle, for example the source application can, if necessary convert the data to some other format based on what the destination app asks for. A clipboard would need to be insanely complicated to handle all the possible data types, while the application you viewed the data with in the first place is much more likely to be capable of converting the same data to some other format)

If you want a clipboard instead you'll need to install a clipboard manager. Which one to use depends on which desktop environment (or window manager) you are running, and your personal preferences of course.

---

### Post by missmoondog on 2012-01-04
> **MartijnNL said:**
> I think the OP means that she's on a webpage, copies something on that page, then loads a new site (yahoo/gmail) in the SAME tab and then tries to paste the content into that new page. So the original page is no longer present when the paste action takes place. Which doesn't seem to be working for her.

I just tried this in Firefox 9.0.1 under Xubuntu 10.10 and it works fine.

What browser (and version) and Ubuntu version are you using?

Edit: I noticed Xubuntu has xfce4-clipman installed, so that may be why it's working for me.

this is dead on as to the issue i'm trying to explain!

doesn't matter what browser i use, firefox, seamonkey or opera and all are most current available. actually, just updated firefox to version 10 manually instead of waiting for repos to catch up to things.

running xubuntu 11.10.

seems like i had this problem in a previous version also, now that someone else mentioned it, but it's worse this time.

sometimes doesn't matter if leave original tab open or not also, have to go back to original page/tab and copy again.

will check into Parcellite, Glipper, Pastie, Klipper and Glippy.

Thank you

---

### Post by mike555 on 2012-01-05
> **missmoondog said:**
> 

will check into Parcellite, Glipper, Pastie, Klipper and Glippy.

Thank you

   If you install "Klipper" it will install loads of KDE stuff you might not want.
If your on Xubuntu I recommend "Clipman".

---

### Post by missmoondog on 2012-01-05
> **mike555 said:**
> If you install "Klipper" it will install loads of KDE stuff you might not want.
If your on Xubuntu I recommend "Clipman".

thanks!!

just came back to see what those names were again.

no need for loads of kde stuff here.

edit:
clipman installed and working. not exactly like windows, is it? ;)
it'll due though.

didn't this used to be installed by default?

thanks

---

