---
title: "Firefox 3.6 drag n drop not working"
date: 2010-05-08
forum: General Help
---

### Post by xrado on 2010-05-08
Firefox 3.6 support html5 drag n drop features (files,...)
both in karmic and lucid do not working
while in Windows, same version of Firefox drag n drop works.

why is that so?

---

### Post by pikappa73 on 2010-07-04
...same issue here!,

i'm setting up an application, which will mainly run as a standalone  application (thanks --> [COLOR=DarkRed][prism]("http://prism.mozillalabs.com/")[/COLOR]! <--), providing an html5 drag'n'drop environment to upload images, and it perfectly works on firefox-windows - but does not on firefox-lucid - and i do need linux support.

i can see that html5 d'n'd DOES work for on firefox-lucid (as in this --> [COLOR=DarkRed][demo]("http://demos.hacks.mozilla.org/openweb/imageUploader/")[/COLOR] <--), but not in my code, so... why, what's wrong-missing-whatever?

only thing i can think about is the complexity of it all: i had to setup the javascripts' eventListeners to the html-root-element itself to avoid people erroneusly replacing the application-url with a preview of the image they would like to upload (with, then, no turning-back possibility!*), so i can imagine that under lucid the whole capturing and bubbling thing is a little too much, as the placeholders are at level 8 or 9 in the nesting dom-tree: sometimes i do see the elements react to the dragenter and mouseovers functions, mostly not, but actually never DOING the upload -

so, if someone dares to give it a try (*it's still a pre-alpha phase for the whole project, not all security-issues are already tracked down or special-programmed for (against?), but some already are, so i cannot give a simple url and let's go - and, it's in italian*), *just* follow that:

[...]
[19.7.2010 - removed: the application isn't there 'open' anymore - but i'll let the rest here for future reference]

[...] the drag'n'drop javascript functions [...] it enables image-place-swapping and dropping of external image-files, checking in the classList of the potentially starting/receiving targets for "swap" (to swap but also to replace the images) or "upload" classNames -

enough!, hope this will bring new impulses to track down and resolve this issue, for the moment i'll try to focus on continuing the coding - the project is due for 2011, but i would like to let it be tried from *real* potential-users from the car-accident-workers sector - (the program is actually already managing one local "carrozzeria", so this will be version 2, open to several ones at the same time)

pikappa


** the choice of prism is **not really an anti-hacker feature - rather** it is to avoid people triggering unexpected behaviours in the application, as one could easily do with BACKSPACE, F5 or right-clicks and juggling with the client-side-code, messing up the db-consistency - (in italian "user" is "utente", but oft enough these "utenti" behave more like "utOnti", where "tonto" is in english... nincompoop?)*

---

### Post by pikappa73 on 2010-07-07
ok - now it's done, now it works -

it turned out that (under ubuntu) javascript protested a "security error" (code 1000), when i tried to read the [FONT=Courier New]event.dataTransfer.getData('text/plain')[/FONT] already by the dragover, dragenter and dragleave events... mistake!, **these details about EXTERNAL dragging object are only free to consult in the drop event**!

> A security error will occur if you attempt to retrieve data during a drag that was set from a different domain, or the caller would otherwise not have access to. This data will only be available once a drop occurs during the drop event.
*[from the --> [COLOR=Red][MDC page about dataTransfer]("http://mdn.beonex.com/En/DragDrop/DataTransfer")[/COLOR] <-- section getData(), about in the middle of the page]*so, as i indeed needed to read these infos for the INTERNAL ones (like for  swapping 2 images) i added a[INDENT][FONT=Courier New]try { data = event.dataTransfer.getData('text/plain'); } [/FONT]
[FONT=Courier New] catch(e) { data = ''; }[/FONT]
[/INDENT]to prevent the error-triggering - and this does the trick: now ubuntu too accepts my code and the images upload / update by native html5 drag and drop! :P 

*[curious enough, it only needs an extra**[FONT=Courier New] var foo=e.dataTransfer.files;[/FONT]** in the drop-handling-function to make the image-update working too, as without it the files collection is void... boh?]*

so, i hope this can be of some help for people who will stumble on this unexpected 'error' or 'security feature': under windows (bless it or curse it) there were no problems about that - and for people like me who mainly develop in a windows environment but have an always increasing need (and pleasure, why not?) to know and handle linux issues, this could spare some time - thanks for hosting my posts!

paolo

[SIZE=1]- - - - -
 about the error tracking, it was in two directions:
  
 - addressing the 'complexity-problem': i removed all  eventListeners  from the HTML element but the "dragover" one (as this  only really  prevents the document-replacement-problem) - all other  listeners are  now only targeted at the *real* targets and the whole reacts a  little  more realtime -[/SIZE] [SIZE=1]
  
 - in my (virtualbox) naked-firefox-under-ubuntu i have no webdeveloper  toolbar, nor a firebug console, so no feedback on js errors at all -  "could it be a js error?"[/SIZE] [SIZE=1]
 i set up a more personal error console [ *window.onerror=function(){  [give onscreen js  errors feedback] }* ], and there, finally, was  this "security error", pointing at the faulty code-line![/SIZE]

---

### Post by MaskedMarauder on 2011-03-24
Was there ever a solution to this problem?

DnD stopped working on my laptop when I upgraded from jackalope to maverick.  Firefox 3.6.10 works OK on jackalope, but toolbar icon DnD customisation doesn't work on in 3.6.25 in maverick.

---

