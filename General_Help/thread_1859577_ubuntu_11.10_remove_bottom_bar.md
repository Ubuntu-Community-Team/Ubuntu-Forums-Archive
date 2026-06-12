---
title: "ubuntu 11.10 remove bottom bar"
date: 2011-10-14
forum: General Help
---

### Post by cadogan32 on 2011-10-14
Hi,just installed ubuntu 11.10 and the clasic gnome desktop.Got glx dock installed as well,but cant figure out how to remove the bottom panel so i can just have my new dock.I was running 10.04 and remember just right clicking on it and removing it.Not quite the same here i guess:P iam sure its really easy but i cant figure it out.any help would be great.

---

### Post by Vaphell on 2011-10-14
[http://www.youtube.com/watch?v=e271OvFxbpM](http://www.youtube.com/watch?v=e271OvFxbpM)

Open dconf-editor and go to
org &#8594; gnome &#8594; gnome-panel &#8594; layout
Change ['top-panel','bottom-panel'] to just ['top-panel'] and hit the enter key.

---

### Post by cadogan32 on 2011-10-14
Thank you! it worked great.:)

---

### Post by crdlb on 2011-10-14
You just needed to hold Alt when you right clicked on the panel.

---

### Post by cadogan32 on 2011-10-14
Thanks.I'll have to remember that as well.:)

---

### Post by mörgæs on 2011-10-14
Please mark the thread 'solved'.

---

### Post by Bouffski on 2012-01-26
> **crdlb said:**
> You just needed to hold Alt when you right clicked on the panel.

this was the only way it worked for me... 

(simplicity is the beholder of truth...)

Cheers!

---

### Post by sportfreak2020 on 2012-05-04
works in 12.04 as well .. just saying!

---

