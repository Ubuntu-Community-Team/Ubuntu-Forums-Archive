---
title: "need help with keyboard!!!!!!!!!!"
date: 2010-07-29
forum: General Help
---

### Post by Razor_bmw123 on 2010-07-29
I have been using Mandriva 2010 linux for the last 1 year n now I m trying ubuntu 10.04......usually I do a lot of programming stuffs in linux......... I have installed ubuntu 10.04 dekstop as dual boot with windows 7 n i liked it very much...everything is cool n awesome....but i am having one strange problem when i write on a file in the terminal....after opening a file and pressing INSERT i start to write normally....but when I press UP it prints A, when I press DOWN it prints B, when I press RIGHT it prints C, when I press LEFT it prints D........its kinda strange......when i press delete button and backspace button also acts strange.......but everything is fine when i write commands in the termonal and use oppenOffice.........bt couldnt understand what is going on!!!!is it for the ubuntu????or something else???my default keyboard layout is set USA..........

HELP ME OUT!!!

---

### Post by dcollier on 2010-07-29
Are you using vi or vim?  I would try vim and see if you get the same results.

---

### Post by Razor_bmw123 on 2010-07-29
i am using VI..............plz help me with it...i just want to type normally like the way how we use openOffice or MSWord......when I type commands in the terminal, its even fully ok.....i really dont know whats happening....

---

### Post by ankspo71 on 2010-07-29
> **Razor_bmw123 said:**
> but when I press UP it prints A, when I press DOWN it prints B, when I press RIGHT it prints C, when I press LEFT it prints D........its kinda strange......when i press delete button and backspace button also acts strange.......


Hi, I have that problem in VI too. My keyboard layout is USA with &#8364; sign on 5. Everything works on my keyboard for every application, including my numberpad, but in VI my keyboard acts strangely.

I prefer to use "nano" for my command line text editing needs, have you tried that text editor? At the bottom of the nano screen it shows several options such as:
"^O WriteOut" (means to use Ctrl+o to save the file)
"^X Exit" (means to use Ctrl+x to exit nano)
and so on.
Hope this helps you

---

### Post by Qwantumz on 2010-07-29
VI is a powerful file editor that can be confusing sometime for new users (especially between the 'Command Mode' and the 'Insert Mode'. I suggest you to look at 
[http://glaciated.org/vi/](http://glaciated.org/vi/) or type  'man vi' in a terminal to know more about it. If you want something simplier, just use 'nano' instead of 'vi' (E.g : nano file.txt), It is simplier and has less function than VI but will surely do the job in your case.
 
Hope this helps

---

### Post by Razor_bmw123 on 2010-07-29
just now I have installed VIM and now it works fine!!!!!!!!!!:p....now i can write normally both in VI n VIM.....:p.......

but could u just help me out in one thing......how can I enable INDENTATION in the VI editor in writing programming languages like C/C++/Java????????

---

### Post by ankspo71 on 2010-07-29
Now the arrow keys work for me in vi too. Installing vim did the trick. :rolleyes:
Thanks everyone

---

### Post by simosx on 2010-07-29
> **ankspo71 said:**
> Now the arrow keys work for me in vi too. Installing vim did the trick. :rolleyes:
Thanks everyone

Actually both 'vi' and 'vim' are vim. The issue is that the plain 'vi' is vim under an old compatibility mode that has issues with the arrow keys, does not support syntax highlighting and what more.

So, if you want vi/vim, install the 'vim' package.

---

### Post by Razor_bmw123 on 2010-07-29
> **simosx said:**
> Actually both 'vi' and 'vim' are vim. The issue is that the plain 'vi' is vim under an old compatibility mode that has issues with the arrow keys, does not support syntax highlighting and what more.

So, if you want vi/vim, install the 'vim' package.



How can I enable INDENTATION in VIM while coding C/C++/JAVA programming languages??????????


help

---

### Post by simosx on 2010-07-29
> **Razor_bmw123 said:**
> How can I enable INDENTATION in VIM while coding C/C++/JAVA programming languages??????????

Hey, don't put those repeated characters. In Web terms, you appear as if you are disrespectful, and people tend either not to help or help at a minimum.

There are vim options for any of these features; search at [http://www.vim.org/](http://www.vim.org/)

You add those features in /etc/vim/vim.local
You can edit this file with

sudo gedit /etc/vim/vim.local

or 

sudo vi /etc/vim/vim.local

---

