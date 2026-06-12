---
title: "vi error on start"
date: 2009-07-06
forum: General Help
---

### Post by c0mput3r_n3rD on 2009-07-06
Hello all!

My text editor of choice is giving me a problem right when it starts.  It says:

Error detected while processing /home/matt/.vimrc: 
line    1: 
E492: Not an editor command: ^[[?1049h^[[1;24r^[[m^[(B^[[4l^[[?7h^[[?12l^[[?25h^[[?1h^[=^[[?1h^[=^[[?1h^[=^[[39;49m^[[39;49m^[[m^[(B^[[H^[[2J^[[0;7m^[(B  GNU nano 2.0.7      File: /usr/share/vim/vim64/vimrc_example                  ^[[22;35H[ New File ]^M^[[23d^G^[[m^[(B Get Help  ^[[0;7m^[(B^O^[[m^[(B WriteOut  ^[[0;7m^[(B^R^[[m^[(B Read File ^[[0;7m^[(B^Y^[[m^[(B Prev Page ^[[0;7m^[(B^K^[[m^[(B Cut Text  ^[[0;7m^[(B^C^[[m^[(B Cur Pos^M^[[24d^[[0;7m^[(B^X^[[m^[(B Exit^[[14G^[[0;7m^[(B^J^[[m^[(B Justify   ^[[0;7m^[(B^W^[[m^[(B Where Is  ^[[0;7m^[(B^V^[[m^[(B Next Page ^[[0;7m^[(B^U^[[m^[(B UnCut Text^[[0;7m^[(B^T^[[m^[(B To Spell^M^[[3d^[[22;16H^[[0;7m^[(B[ line 1/1 (100%), col 1/1 (100%), char 0/0 (0%) ]^M^[[3d^[[m^[(B^[[24;1H^[[?1049l^M^[[?1l^[> 
Press ENTER or type command to continue 

It's such mumbo jumbo, I don't even have a file /usr/share/vim/vim64/vimrc_example, it's /usr/share/vim/vim72/vimrc_example

Can anyone help me out with this?

---

### Post by mbeach on 2009-07-06
I would temporarily rename .vimrc

```
mv ~/.vimrc ~/copy.vimrc
```

then start vi, see if you have the error.

---

### Post by c0mput3r_n3rD on 2009-07-06
Yeah that works, thank you.  Do I need to do anything with that copy or can I just delete it?

---

### Post by mbeach on 2009-07-06
I would probably take a look at it

vi ~/copy.vimrc

and see if it looks like a valid .vimrc file or not. If on line 1 there is something that needs to be commented out, do so and rename it back to .vimrc

For many the default is fine, but after awhile individuals like to tweak their own, adding their own preferences. Even though I'm the only user on a particular machine I tend to create my own .vimrc file in my home directory instead of editing "/etc/vim/vimrc" as I believe that gets overwritten during an upgrade (or has potential to).

if your ~/copy.vimrc is complete garbage, I see no reason to hold on to it, but I'm one who deletes very little so I'd probably just let it sit there just in case it becomes obvious to me 4 days from know why it was that way and I need it back for some reason.

---

### Post by frenkel on 2009-07-06
Did you install vim or vim-full? Default is vim-tiny and it doesn't support all settings. Also check if it was a valid vimrc indeed.

---

### Post by c0mput3r_n3rD on 2009-07-06
I installed vim full and that file wasn't a valid vimrc file, so I just deleted it and vi is working great now.  Thanks every one

---

