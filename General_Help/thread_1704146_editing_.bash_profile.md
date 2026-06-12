---
title: "editing .bash_profile"
date: 2011-03-10
forum: General Help
---

### Post by Umbrix on 2011-03-10
Hiya, I have just started using ubuntu and use the terminal a lot. I would like to edit it (blue username?). I have tried changing the .bash_profile file, but my changes do not seem to affect it. 

I also added an alias to bash.bashrc, but my computer started looping at login so I reinstalled. I dont know if that caused it (I doubt it, but I didnt do anything else, though undoing it didnt work). 

Can anyone tell me exactly what to put in the .bash_profile file. It is currently blank, and nothing I add seems to work (using online tutorials).

Using ubuntu 10.10 (netbook) and normal - I would like to edit the netbook edition, though I thought they would be the same.

---

### Post by mcduck on 2011-03-10
Take a look at ~/.bashrc and ~/.profile instead of the files you are now trying to use... ;)

---

### Post by Rushyang on 2011-03-10
I don't understand what you were trying to change, what you're calling it a BLUE USERNAME.. 

But let me assume.. if you were trying to change a **Prompt Settings** then that settings are loaded when you open a new terminal through **PS1** variable through the ~/.bashrc file. 

generally there should be a line like.. \u@\h: \w \$ in your .bashrc file assigning your PS1 value..
1. Open your .bashrc file in your favourite text editor.
2. Find PS1
3. In \u@\h: \w \$ 
**u** - username
h - hostname
w - display hole path

well.. in above setting... write anything after slicking **u**.
I hope that helps.. if not... google "How to change PS1 variable in linux".

---

