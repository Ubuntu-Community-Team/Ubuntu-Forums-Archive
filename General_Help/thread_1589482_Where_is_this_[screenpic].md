---
title: "Where is this? [screenpic]"
date: 2010-10-06
forum: General Help
---

### Post by Moozillaaa on 2010-10-06
I want to increase the size of the reference symbol, which is used in GIMP, for rotating images. 

In this screenshot, it's the 'bullseye-like' symbol in the middle of the pic.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171458&d=1286387621

---

### Post by akvino on 2010-10-06
That is Saint Louis MO - and the image editor probably put the bull's eye. Wrong forum .

---

### Post by lisati on 2010-10-06
Whoops, wrong forum! :D

I don't see a connection with Programming - moved....

---

### Post by nothingspecial on 2010-10-06
Looks like Hulme, Manchester, England

But it`s not raining, so I`ll go with St Louis

---

### Post by Moozillaaa on 2010-10-06
I feared getting every comment except what I'm looking for. Oh well...

It was entered into 'Programming', because it is NOT a configuration setting. It is going to be at the PROGRAMMING level of the application [GIMP].

Please move this thread back into 'Programming'. Thanks.


edit:
Someone reading threads in 'Programming' has to be sharper than this:
> and the image editor probably ***put*** the bull's eye.

I said nothing about 'placement'. The question is about 'sizing'.

---

### Post by hhh on 2010-10-06
I'm sure that is hard coded into GIMP (I have no idea where) and you can't change it without rebuilding it from source. Try posting on the GIMP forums...
[http://gimpforums.com/](http://gimpforums.com/)

---

### Post by Moozillaaa on 2010-10-06
> **hhh said:**
> I'm sure that is hard coded into GIMP (I have no idea where) and you can't change it without rebuilding it from source. Try posting on the GIMP forums...
[http://gimpforums.com/](http://gimpforums.com/)

I think you're right there, hhh - I thought I'd try the Programming' forum tho', since it will involve modifying code for the application.

And good for you - actually reading the question! I think it went right over the others' heads. :(

---

### Post by spjackson on 2010-10-06
> **Moozillaaa said:**
> I think you're right there, hhh - I thought I'd try the Programming' forum tho', since it will involve modifying code for the application.

And good for you - actually reading the question! I think it went right over the others' heads. :(
I'm not really familiar with the Gimp source but I have done a bit of digging.

I think the actual drawing takes place in app/tools/gimpdrawtool.c , with the 2 cases:
GIMP_HANDLE_CIRCLE and GIMP_HANDLE_CROSS.

I think the size calculation happens in app/tools/gimptransformtool.c

I hope that points you in the right direction at least.

---

### Post by overdrank on 2010-10-06
Duplicate [here]("http://ubuntuforums.org/showthread.php?t=1589559").
Thread closed. :)

---

