---
title: "Git Push problem (seems doesn`t works!)"
date: 2009-07-10
forum: General Help
---

### Post by Tundo on 2009-07-10
Hi everyone guys! i have a Git issue (lastest vers.), to simulate a lan i create two dir: "server" will`be hosted in a lan server, "user1" to simulate a deveoper local dir. 
I wanna simulate a projcet development across a local lan connected with another remote lan, and i proceed as follow: 
-open 2 terminal, either in the respective path (server, user1) 
-initilze git, add all files and commit (on server terminal) 
-initialize git in User1 terminal 
-from User1 i clone the project folder from "server" 
-i work, work, edit, and work again (in truth i added a single line of code ;-)..), for example in Main.c file, then save, git add ., git commit
  at this time if i push my work in "server" (using "origin" which contains server path).....

  Codice:
  $ git push origin
  and follow: 

Codice:
  Counting objects: 9, done. 
Compressing objects: 100% (5/5), done. 
Writing objects: 100% (5/5), 514 bytes, done. 
Total 5 (delta 3), reused 0 (delta 0) 
Unpacking objects: 100% (5/5), done. 
To /home/******/enrico/virtualnet/user1/../server//.git 
   9be041f..11d3b9f  master -> master

  but the Main.c file in "server" doesn`t changed anything, it`s always the same also if i repeat the push more then a time.... 
what`s wrong? maybe i have to use another command? plz helpme 
thanks alot.. 
_______________________________________________________________________________________________________ 
Ciao a tutti, ho un problema con Git (ultima vers), per simulare una rete ho creato due directory: "server" sara` in futuro ospitata su un server in rete, "user1" simula la cartella di un utente in locale. 
Da qui, per simulare quello che sara` lo sviluppo di un progetto tramite rete lan e remota, ho proceduto come segue: 
- apro due terminali, ciascuno sulla rispettiva dir. (serve, user1) 
- inizializzo git , addo i file e committo su server 
- inizializzo su user1 
- da user1 mi clono il progetto presente su "server" 
- eseguo le mie modifiche, x esempio su un file main.c e salvo, addo e committo
  a questo punto dovrei effettuare il push sul server, "origin" non e` altro che il percorso dal quale ho clonato in precedenza, ossia "server"
  Codice: ..................
  ma il file main.c presente in "server" NON e` cambiato di una virgola..... 
cosa sbaglio? forse ometto qualche comando??
  grazie

---

### Post by Tundo on 2009-07-10
ok folks i understand that Pushin` the server folder i update .git folder with my modify but i`m still not able to update the Main.c file in server dir. how can i do it? 
nobody????? pleaseeee

up up up up....

---

### Post by auch on 2011-01-10
i had the same problem and perhaps another one needs still an answer. 
doing 'git reset --hard' on origin did the trick for me

---

