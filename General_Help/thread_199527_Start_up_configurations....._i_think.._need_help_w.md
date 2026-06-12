---
title: "Start up configurations..... i think.. need help with them"
date: 2006-06-18
forum: General Help
---

### Post by konacoffeeguy on 2006-06-18
Hello, 
 
  When I start up my computer, I notice when it is starting up it checks for the older PCI slot or whatever and say's it fails. I would like to stop my computer from checking that operation on start up. How can I edit what it try's to configure on start up. Thank you , 
 
Konacoffeeguy

---

### Post by Compucore on 2006-06-18
When it shows that one has failed is it the pcmcia daemon by any chances?

Compucore

---

### Post by konacoffeeguy on 2006-06-18
yes thats it the pcmcia ... thats correct

 cobbweb

---

### Post by Compucore on 2006-06-18
Have you tried reinstalling it. by anychance under the terminal? I know it has failed on mine over here. But I just simply ingore it. since it is on a workstation that does not have any pcmcia slots on it. Try reinstalling it to see what happens.  here is the terminal version for reinstalling it. 

sudo aptitude reinstall pcmcia-cs

[QUOTE=konacoffeeguy]yes thats it the pcmcia ... thats correct

 cobbweb[/QUOTE]

---

### Post by konacoffeeguy on 2006-06-18
I would just like to be able to remove the whole um... "process" if thats what it's called of even looking for a pcmcia. I don't even know if I have one... err... how sould I just skip that whole process? 
 
 Danka, 

 Konacoffeeguy

---

