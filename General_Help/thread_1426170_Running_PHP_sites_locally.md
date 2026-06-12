---
title: "Running PHP sites locally"
date: 2010-03-09
forum: General Help
---

### Post by gantww on 2010-03-09
Greetings,
I'm about to develop some python code that interacts with remote sites built on Pligg. So that I can test this code as I'm going, what is the simplest possible way to host a PHP site? Would I just install apache, or is there something even easier. I basically just need my code to interact with the existing site while it is running.

Is there some sort of development webserver that will handle the task better?

Thanks,
Will

---

### Post by darolu on 2010-03-09
After apache you need to install php and now that you are at it, install mysql also, and you'll have a LAMP server. I also recommend installing "phpmyadmin".

You can install it all easily from Synaptic, open it (system - admin - synaptic) and go to Edit - Mark packages by task (or similar my ubuntu is in spanish so my translation may not be 100% accurate) and mark LAMP Server, it will install all you need, -phpmyadmin- is not included so you'll have to search for it.

---

### Post by gantww on 2010-03-10
Ah. As usual, I was overcomplicating things. For some reason, I was under the impression that I had to fight with a bunch of config files to make this happen like I wanted.

Thank you.

---

