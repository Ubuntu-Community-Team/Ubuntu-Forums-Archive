---
title: "two problems with epiphany 2.26.1"
date: 2009-09-21
forum: General Help
---

### Post by claracc on 2009-09-21
I have just installed epiphany web browser 2.26.1 from ubuntu repositories, and it works very well (better fonts and displayed images than firefox) except for two problems:

- Embeded videos in BBC news don't play, i select to watch a video, it appears the image and the click simbol to play in the center, when i click it seems to be loading the video but never ends. All every places i have tried with videos work very well (youtube, newspapers).If I use firefox 3.0.14, i can play any embeded video included that in bbc news.

- The other problem is that i cannot cut/paste and image  i find in the web to put it in an openoffice document, when i right click over the image, it doesn't appear the copy option (copy the url of image, open image, open link, save image as, appear). The only way to copy an image is to copy some of the text in the web with the image, in this case, when i right click, the copy/paste menu appears.

¿Could someone help to solve this two problems?. 

I have ubuntu 9.04 in a hp compaq6720s laptop updated, adobe flash 10.0.32. Metacity windows decorator, no visual effects.

Thanks in advancehttp://ubuntuforums.org/images/smilies/icon_sad.gif

---

### Post by buellman on 2009-09-21
As for your first problem: I can't watch the BBC News videos with epiphany but with firefox. So the same problem for me.
As for your second problem: maybe some javascript is blocking the right-click option? Maybe try it with disabling javascript? Maybe you would like to show the example URL so I could validate that to? Btw: I had some webpages in the past where the images where presented in some sort of a flash-frame. Maybe thats your problem?

Greets. Buellman

---

### Post by claracc on 2009-09-21
Thanks buellman for answering.

I cannot copy any image in the web, for example i go to this url: [http://es.wikipedia.org/wiki/Condensador_el%C3%A9ctrico](http://es.wikipedia.org/wiki/Condensador_el%C3%A9ctrico), and i try to copy the right part image "condensadores modernos", i right click over it and there is not the option copy , but if i select the image with the text and right click, the copy option appears.

Following your advice i have disabled javascript, but the copy option doesn't appear.

What will be?

 Regards.

---

### Post by buellman on 2009-09-21
Hmmm... I have no problems with copying the image "condensadores modernos".
I have no idea what else could be the problem. Maybe it is language dependent as I use german and you not?

You could try to start the "Guest"-account and see if the problem persists or even create a new user if you like. If the problem persists you may have found a bug. If not you maybe have a problem with permissions or something like that.

Greets. Buellman

---

### Post by claracc on 2009-09-22
I have been investigating and i have found some clues, for example it seems the default behaviour in epiphany to disable custum javascript menus, for this reason, i understand, when i right click over an image in the web, doesn't appear the option copy. It can be seen in the comments in this link:

[http://www.nabble.com/Custom-javascript-menus-to15734824.html#a15773867](http://www.nabble.com/Custom-javascript-menus-to15734824.html#a15773867)

I can always copy the image to a file and then insert it in a document but it is long and tedious.

Anycase i have enabled the extension site permission but it doesn't seem to work, i put there the url of the page to allow images but it doesn't appear in the screen (perhaps i am misunderstanding how to configure it). Now, when i right click over an image in the site permissions edited web, it appears the option copy, i click and try paste over an openoffice document but what is pasted is the url of the image (the link to it). i have the package extensions release 2.26.0 which is in ubuntu's repositories.

I am thinking, i am doing something wrong. What extensions i have to enable in order to copy images directly to the clipboard with right click, and then paste in a document?, or there is some script i have to do?.

Any idea or suggestion is very welcome.

---

### Post by buellman on 2009-09-22
Ah... I see what you mean.
A workarround would be to right-click the image and in the opening menu select "Bild öffnen" (maybe translates to "open image/picture"). That should open Eye of Gnome. From Eye of Gnome you can "move" the image to your document.
I don't know why it doesn't work if you "move" it directly from epiphany to your document.

Greets. Buellman

Ps: you can also mark/highlight the image in epiphany, press ctrl+c on the image, press ctrl+v in your document et voila :-D

---

### Post by claracc on 2009-09-22
Yes, this is a good workaround (for the quick copy/paste of web images)and it works.

You have solved the problem, thank you Buellman.

Regards, Clara

---

### Post by buellman on 2009-09-22
No problem :-)

Greets. Buellman

---

