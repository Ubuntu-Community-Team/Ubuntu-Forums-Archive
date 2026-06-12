---
title: "No userchrome.css in firefox, how to create?"
date: 2012-03-17
forum: General Help
---

### Post by dez93_2000 on 2012-03-17
Hi. I'm trying to edit the bookmarks window size in firefox, using this guide:
[http://forums.mozillazine.org/viewtopic.php?f=38&t=2425679](http://forums.mozillazine.org/viewtopic.php?f=38&t=2425679)
whereby you add a line to userchrome.css in the chrome folder, however I don't have this file.
This thread:
[http://ubuntuforums.org/showthread.php?t=1799531](http://ubuntuforums.org/showthread.php?t=1799531)
suggests simply creating one, but i did so and pasted in only the relevant line from the first site and nothing happens.

Any ideas on how to do this? Thanks in advance

dez

(Why can't anything just be easy?)

---

### Post by vasa1 on 2012-03-17
You should mention your Firefox version just in case.

But ...
Search for your profile folder. Mine is: ```
/home/vasa1/.mozilla/firefox/7sw6w9a2.default
```
Within that folder, you should have a folder called "_**c**_hrome". If it doesn't exist, you'll have to create it.
Within the folder, create the file you want. In this case, it will be user_**C**_hrome.css.
Note the **case** for both the folder and file.
The first line of your user**_C_**hrome.css should be:
```
@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

```Then, you can put in whatever code you want.
Edit: ensure you save the .css file as a plain text file.

---

### Post by dez93_2000 on 2012-03-17
you little beauty. yep, that did it - mine was UserChrome not userChrome, and i didn't have the first line - someone else included it on the first thread i posted but it looked like it was personal to them - bad guess on my part.

Many thanks indeed!

---

### Post by t.h.w. on 2013-01-23
> **vasa1 said:**
> You should mention your Firefox version just in case.

But ...
Search for your profile folder. Mine is: ```
/home/vasa1/.mozilla/firefox/7sw6w9a2.default
```
Within that folder, you should have a folder called "_**c**_hrome". If it doesn't exist, you'll have to create it.
Within the folder, create the file you want. In this case, it will be user_**C**_hrome.css.
Note the **case** for both the folder and file.
The first line of your user**_C_**hrome.css should be:
```
@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

```Then, you can put in whatever code you want.
Edit: ensure you save the .css file as a plain text file.

I have not implemented the first line, seems to be ok without it.

To get two 'new-tab'-buttons in firefox, make sure the first 'new tab'-button in front of the back-forward-buttons. Close firefox. +8+
 Then make the userChrome.css-file in the ./chrome folder and add the following line: 

.tabs-newtab-button { visibility: visible !important; } 

Restart firefox and presto!
):P

---

