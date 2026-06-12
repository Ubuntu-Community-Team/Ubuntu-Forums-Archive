---
title: "No such file or directory"
date: 2010-12-04
forum: General Help
---

### Post by mike22112211 on 2010-12-04
i am trying to compile a C file on ubuntu feisty fawn. when i try to compile by typing:

gcc firstprog.c

i get the following message:

gcc: firstprog.c: No such file or directory

i get this when i try compiling any file. any ideas?

---

### Post by Nytram on 2010-12-04
Hi Mike

I don't know how familiar you are with Linux, so this may be stating the obvious, but anyway.. have you checked that letter cases are correct, ie FirstProg.c is not the same as firstprog.c. It's an easy mistake to make.

---

### Post by mike22112211 on 2010-12-06
i am new to linux and trying to learn it. i checked for caps and there are none so i must have entered it correctly. im not sure what the problem is but i cant compile any C files. any ideas? thanks for the reply.

---

### Post by Nytram on 2010-12-08
After you open the terminal do you set the current directory to the same one as your program is in?

---

### Post by oldos2er on 2010-12-08
> **mike22112211 said:**
> i am new to linux and trying to learn it. i checked for caps and there are none so i must have entered it correctly. im not sure what the problem is but i cant compile any C files. any ideas? thanks for the reply.

Unlike most Linux distros, Ubuntu does not come by default with the ability to compile code; you need to install the package build-essential. But Feisty is no longer supported, so I'm not exactly sure how you would go about doing that.

---

### Post by mike22112211 on 2010-12-09
to answer both questions. first, how do i set the current directory to the same one my program is in? i have noticed that the directory currently says mike@mike-desktop, in my manual i am using it needs to have "/booksrc" added to the end of that. how would i do that?

secondly, i have searched for package build essential and have found it using my synaptic package manager. it says it is installed. do i need to do anything else? thanks for the help.

---

### Post by mike22112211 on 2010-12-09
sorry for the extra message but i figured it out. i entered :

cd ~/booksrc 

and it now compiles fine. thanks for the help with the fix.

---

