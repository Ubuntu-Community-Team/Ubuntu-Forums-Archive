---
title: "Script when using R in Ubuntu Jaunty"
date: 2009-07-01
forum: General Help
---

### Post by rockstallion on 2009-07-01
I am New to Ubuntu. I do all my statical analysis using R. When using R in windows I was used to the script which I could save and make changes to. But since I switched to Ubuntu I have to type the commands in the terminal window and i can only save the workspace but am find it tough to work this way. Can some one help me with how can I install some thing like scrpt or Tinn-R or anything which will allow me to work on the commands before I run the commands in R

---

### Post by niteshifter on 2009-07-01
Hi,

```
R CMD BATCH scriptfile.R
```

Create your script with Gedit or whatever text editor you like.

Keep in mind I'm rusty as hell on R. This [site]("http://www.r-project.org/") may be useful to you.

---

### Post by rockstallion on 2009-07-01
Yes but using gedit i cannot run the command using a short cut (or can I?). 
For example in R script i could just press Control+R to run the selected commands but here in ubuntu I have to copy it from text editor and paste it in the the terminal which is very painful do especially when testing some code.

---

### Post by niteshifter on 2009-07-01
Hi,

I know there exist "integrated" approaches to this: emacs / xemacs with the ess module (what I used to do) - it ties together the editor with an R session. Googling "R script" came up with that and one using the vim editor (shudder).

Since an R session runs in Terminal a very weak workaround would be copy and paste. I did find an [R forum]("http://www.nabble.com/R-f13819.html"), you'll probably have better success asking there. Not meaning sound unfriendly, Ubuntu is quite popular but R's a pretty arcane area of knowledge with respect to the general population. Just sayin' you should fish where they be bitin' ;)

Sorry I can't be of more help - my needs for stats techniques have been reduced to that of spreadsheet and the winging something up in Python, i.e. very light duty.

---

### Post by Philotus on 2009-09-13
Hey Rockstallion,

I know this comes a bit late for you and you've probably long since solved your issue but I thought I'd throw in the 2 most common possibilities for getting what you want in Ubuntu for R. 
Without inciting a riot let me just say that R can be integrated in a sense with either vim or emacs. It's up to you which you prefer.

The vim-r plugin from Johannes Ranke allows you to open an R script file in vim and send commands to R using highlighting and ctrl-r (He provides a readme on how to set it up on his web page).
[http://www.uft.uni-bremen.de/chemie/ranke/?page=vim_R_linux]("http://www.uft.uni-bremen.de/chemie/ranke/?page=vim_R_linux")
There is also a newer version of the vim-r-plugin by a different author, but I moved to emacs before experimenting with it.

If you prefer emacs then ESS is an excellent choice. This allows you to set up a script file and send commands to R, but also allows other methods of using R that can come in real handy (like running R in a buffer with all of the emacs tools in hand for editing and sending commands, e.g., C-c <RET> being one of my favorites, for messing with plots I'd like to tweak).

I've used both and must say I prefer emacs for the R, Sweave and LaTex work I do, but that's just personal preference really. I can see the appeal of both.

---

### Post by PGScooter on 2009-12-02
another simple solution would be to just have a shortcut open up a terminal and run the command that runs an R script. The annoying thing is that you would have to edit the name of the script run in the shortcut. But it would be worth it for a non-trivial project.

---

