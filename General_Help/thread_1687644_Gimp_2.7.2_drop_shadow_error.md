---
title: "Gimp 2.7.2 drop shadow error"
date: 2011-02-14
forum: General Help
---

### Post by whalogreg on 2011-02-14
Errors received when trying to use drop shadow plugin..

"Error while executing script-fu-drop-shadow:
Error: eval: unbound variable: gimp-image-insert-layer"

"Plug-In 'Drop Shadow' left image undo in inconsistent state, closing open undo groups"

Any Ideas?

---

### Post by whalogreg on 2011-02-17
::bump::

---

### Post by whalogreg on 2011-02-19
::bump::

---

### Post by whalogreg on 2011-02-27
::bump::

---

### Post by CeltaWeb on 2011-05-05
Hi I don't know if you fixed your issue but I was getting the same error and the reason in my case was characters in the layer name that the script didn't like. I had a € symbol because it was auto generating the layer name so I would try it again but change the layer name to one word no other characters and see if that makes a difference.

---

### Post by Sombra on 2011-05-13
sudo gedit /usr/share/gimp/2.0/scripts/drop-shadow.scm

Find "(gimp-image-insert-layer image shadow-layer -1 -1)"
and replace it with "(gimp-image-add-layer image shadow-layer -1)"

done

---

### Post by theunsheydenrych on 2012-11-02
I use gimp 2.8 and there is not a "(gimp-image-insert-layer image shadow-layer -1 -1)", but "(gimp-image-insert-layer image shadow-layer 0 -1)"
I tried to change it to "(gimp-image-insert-layer image shadow-layer -1)" and it still come up with the error?

---

### Post by wildmanne39 on 2012-11-02
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

