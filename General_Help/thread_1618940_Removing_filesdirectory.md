---
title: "Removing files/directory"
date: 2010-11-11
forum: General Help
---

### Post by Konbuntu on 2010-11-11
i want to delete a movie file/directory in my download directory but it says the file/directory doesn't exist. im probably doing something wrong...

here's a look at what i did:

> konlah@konlah-laptop:~/Downloads$ ls
867950721.pdf
answers_to_all_toefl_essay_questions (tuanhoang2909@gmail.com).pdf
AQMRL2EDV1.pdf
ARACLOG-1.pdf
ARACLOG-2.pdf
ARACLOG-3.pdf
ARACLOG-4.pdf
ARACLOG-5.pdf
Barron_s_How_to_Prepare_for_the_TOEFL_Essay.pdf
detton449c76a8cb13152edf00bc9066029af6.rar
Legendas.tv.txt
Lições de Umbanda - Autor W.W. DA MATTA E SILVA.pdf
LinuxCBT.part01.rar
LinuxCBT.part02.rar
LinuxCBT.part03.rar
LinuxCBT.part04.rar
LinuxCBT.part05.rar
LinuxCBT.part06.rar
LinuxCBT.part07.rar
LinuxCBT.part08.rar
LinuxCBT.part09.rar
LinuxCBT.part10.rar
LinuxCBT.part11.rar
LinuxCBT.part12.rar
LinuxCBT.part13.rar
LinuxCBT.part14.rar
LinuxCBT.part15.rar
LinuxCBT.part15.rar.part
LinuxCBT.part16.rar
LinuxCBT.part16.rar.part
UMBANDA_SEM_MEDO_VOL_III.pdf
UMBANDA_SEM_MEDO_VOL_II.pdf
UMBANDA_SEM_MEDO_VOL_I.PDF
Wall Street Money Never Sleeps (2010) R5 XviD-MAXSPEED
the name of the file is  " Wall Street..."

so in order to delete it did is what i did:

> konlah@konlah-laptop:~/Downloads$ rm -i "Wall Street Money Never Sleeps (2010) R5 Xvid-MAXSPEED"
rm: cannot remove `Wall Street Money Never Sleeps (2010) R5 Xvid-MAXSPEED': No such file or directory

im a newbie... =/

---

### Post by Bucky Ball on 2010-11-11
Don't think you need the quotation marks and if you get 'permission denied' try with a 'sudo' at the beginning of the command. :)

```
konlah@konlah-laptop:~/Downloads$ rm -i Wall Street Money Never Sleeps (2010) R5 Xvid-MAXSPEED
```

PS: Could you please ask when Airto and Flora are coming to Australia??????? If only! ;(

---

### Post by Konbuntu on 2010-11-11
thanks.. but this is what i got... 

>  konlah@konlah-laptop:~/Downloads$ sudo rm Wall Street Money Never Sleeps (2010) R5 XviD-MAXSPEED
bash: syntax error near unexpected token `('


:confused:

---

### Post by Bucky Ball on 2010-11-11
You're missing the '-i'

```
sudo rm -i Wall Street Money Never Sleeps (2010) R5 XviD-MAXSPEED
```

---

### Post by Hippytaff on 2010-11-11
Also bash doesn't like spaces. you can either put a \ before each space or type the start of the file name and press TAB for autocompletion if your in the directory where the file is :-)

---

### Post by Bucky Ball on 2010-11-11
Thanks for the tip, Hippytaff. Love the nick!

The 'copy terminal command from webpage then click mouse roller to paste in terminal' continues to impress me also!

---

### Post by Konbuntu on 2010-11-11
thanks guys! =)

---

### Post by mcduck on 2010-11-11
> **Konbuntu said:**
> i want to delete a movie file/directory in my download directory but it says the file/directory doesn't exist. im probably doing something wrong...

here's a look at what i did:

the name of the file is  " Wall Street..."

so in order to delete it did is what i did:


im a newbie... =/

At least based on this ls output, and the error message you got, you are mistyping the file name  (XviD -> Xvid).

The easiest way, really, is to use the autocompletion. Just type the beginning of the file name and hot the tab key to autofill the rest.

For example in this case you could just type "rm Wa" and then hit Tab key. :)

Same works for commands, packages you install from the repositories and so on. Also, if the part you have typed matches several files/commands hitting tab twice gives you a list of all possibilities. You can then just type a bit more and then try hitting Tab again.

---

### Post by tad1073 on 2010-11-11
actually, you fill spaces with a back slash "\" or you can do something like this:
 ```
rm 'blah bla blah blah'
```

---

