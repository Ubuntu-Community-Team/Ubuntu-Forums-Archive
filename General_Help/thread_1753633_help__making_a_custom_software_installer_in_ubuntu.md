---
title: "help : making a custom software installer in ubuntu."
date: 2011-05-09
forum: General Help
---

### Post by tonph on 2011-05-09
Hi guys,
I am new in this forum as well as to ubuntu, now i am working my work on ubuntu platform and recently i have been assigned a task in which i have to make a software installer script and a GUI which will installer tar file software packege like mysq.tar and .deb file extensions.Now I have chosen my language of development in c++ widget and using a bit part of shell script to make install the software.What i m trying is to provide a custom installable software with GUI which will be provided as a backup of the software.

Now my problem comes as follows,
   1. How can i show the percentage or time left  for the software installation progress bar.Exp: i want display the installation progress as like in the software installer where it shows x% complete.

   2. In case i need to provide the sudo password how can i grap it ,Exp: when i open the synaptic manager for the first time , it ask for the root password.

Thanks guys in advance and i really appreciate any genuine help from u guys.

 ](*,)

---

### Post by ziekfiguur on 2011-05-09
To your first question i have no idea, for the second i'd say just provide a script that runs `gksudo yourprogram' and let users run that script instead of your program directly.

---

### Post by tonph on 2011-05-09
thanks _[COLOR=Black][ziekfiguur]("http://ubuntuforums.org/member.php?u=960698")[/COLOR],_
   It was a very usefull tip from ur side, regarding the 1st problem i am also searching if there is  a way to solve the problem.
  And for the second one which you have suggested, i will try and work it out on that ...
Thanks

---

