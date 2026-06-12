---
title: "Start executable with library from anywhere"
date: 2012-04-11
forum: General Help
---

### Post by HobbsTunaSandwich on 2012-04-11
I have an executable relap5.x and a necessary library file tpfh2onew placed into /home/HobbsFolder/bin/ - I would like to be able to execute this from anywhere in the file tree.

 To this end I added PATH=$PATH:/usr/lib/pvm3/lib:/home/HobbsFolder/bin/ to the .bashrc. Checking with echo $PATH shows the expected path. Starting the executable with relap5.x from a random folder works, as long as the library is placed in the folder, where the computation is started.

So, for some reason the system finds  relap5.x but not tpfh2onew in /home/HobbsFolder/bin/. Why is that so and what can I do to circumvent it?

---

### Post by SeijiSensei on 2012-04-11
Try putting the library in /usr/local/lib, then running ldconfig.  You need to use sudo for both these tasks.

---

### Post by HobbsTunaSandwich on 2012-04-12
Tried your suggestion. Doesn't work. ldconfig -v shows no links created for /usr/local/lib. Maybe the file is not recognized as a library? If so, is there anything I can do to change that?

---

