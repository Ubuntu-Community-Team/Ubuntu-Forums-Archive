---
title: "ubuntu music problem"
date: 2010-10-31
forum: General Help
---

### Post by coreyscx on 2010-10-31
does anyone know of a software to get rid of album art?? i used easytag and i edited m album then saved it, took the pic off then i copied the music to my mp3 and bam..theres the album art, so wth??

---

### Post by eric_1982 on 2010-10-31
You could always use a bash command to get rid of the art work for example if all the art work was in .jpg format and stored in your music dir you could do something like 

find ~/Music -name "*.jpg" | xargs rm 

this will go through your music dir and search for any file that has .jpg and then pipe it and delete each file with a .jpg extension

---

### Post by coreyscx on 2010-11-01
how do i do that??

---

### Post by eric_1982 on 2010-11-01
If you open a terminal by going to Applications > Accessories > Terminal

and paste this command 

***find ~/Music -name "*.jpg"***


It should return a big list of all the files that end with .jpg 

If you find it to hard to read in a terminal and would like to have the output saved to a file (You could then open with gedit, open office..etc) You can do this by using the **> filename** at the end of the find command. (file1.**JPG** and file1.**jpg** are seem as two different files (Note the upper / lowercase))


***find ~/Music -name "*.jpg" > list-of-artwork***



This would save the output to a file called list-of-artwork and save it in your home directory. /home/yourusername/list-of-artwork


If you feel comfortable with all the results being deleted you can then enter the command below



***find ~/Music -name "*.jpg" | xargs rm***



This will delete all the .jpg in the music directory and the sub directories. Keep in mind in Linux, commands, files, directories...etc, are  case sensitive. Also the images could be in different formats such as .png or .bmp ..etc. 


To remove images with other extensions such as .png, just edit the command were it says .jpg  to something like 



find ~/Music -name "*.png" | xargs rm

This would remove all the .png files



How it works ...

This command does a search in /home/youruser/Music folder and finds all the files with a specific value(.*.jpg, *.png). Then it passes what it finds to xargs which does the rm (delete command). Its kind of like a loop. It finds file1.jpg passes it to xargs and then deletes it, it then finds file2.jpg and pass it to xargs / rm and deletes it. It keeps repeating till all the files matching that value are deleted. 



**Just be careful because if you use a broad search like just an * with the [B]| xargs rm** it would take out all your music as well![/B]

---

