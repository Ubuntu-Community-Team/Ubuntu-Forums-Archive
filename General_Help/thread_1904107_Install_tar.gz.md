---
title: "Install tar.gz"
date: 2012-01-04
forum: General Help
---

### Post by mrbambocha on 2012-01-04
Hey.
Ive succeded to unpack it with : tar -xzvf /home/bob/compressedfile.tar.gz 

Then I "cd" into the location of the source code. But I cant get further then that. (This is the first time im doing this.)


When I type .configure/ nothing happens. It says that the file or direction doesnt excist. What should I do after this?

---

### Post by lisati on 2012-01-04
You might have better luck with:
```
./configure
```

---

### Post by crazy bird on 2012-01-04
A file with the extension .tar.gz is nothing more than a zipped file also calle a tarball. If you unpack it (right click > Unpack here) you will geet a new directory with all the files. One of those files is a text file called READ.ME or README.txt. In this file you will find all the information on how to install a tarball.
 
Normally the steps for installing a tarbal are:
/.configure
make
make install

---

### Post by mrbambocha on 2012-01-04
doesnt work. Nothing happens.

Now ive read the readme file. it says:
1. cd to folder. (Should I hit enter here? Ive done so)
2. type: $ sudo ./install.4.18.1.X.sh i (the first time I did it it asked me for password, but then said it was wrong and since then it never asked me for it again. Should I include the $ symbol when typing it out? Now it only says that command not found)

---

### Post by Maleificus on 2012-01-04
Try exiting out of your terminal, re-entering it, cd to the folder, and type the install command without the $.

---

### Post by lisati on 2012-01-04
> **mrbambocha said:**
> doesnt work. Nothing happens.

Now ive read the readme file. it says:
1. cd to folder. (Should I hit enter here? Ive done so)
2. type: $ sudo ./install.4.18.1.X.sh i (the first time I did it it asked me for password, but then said it was wrong and since then it never asked me for it again. Should I include the $ symbol when typing it out? Now it only says that command not found)

Don't include the "$" symbol, that represents your command line prompt. 

Try typing in this, without pressing Enter:
```
sudo ./install.4.18
```
Then press the "Tab" key. The rest of the command should now be filled in automatically. If it is and it looks similar to what the "readme" file says, press Enter. Just a note: when typing in your password at the terminal, it is normal for it to not show.

---

### Post by sj1410 on 2012-01-04
> **mrbambocha said:**
> doesnt work. Nothing happens.

Now ive read the readme file. it says:
1. cd to folder. (Should I hit enter here? Ive done so)
2. type: $ sudo ./install.4.18.1.X.sh i (the first time I did it it asked me for password, but then said it was wrong and since then it never asked me for it again. Should I include the $ symbol when typing it out? Now it only says that command not found)

if your prompt says $ than you are not a root user and need to type sudo, you need to type the password to gain root access. Try typing the same password of the user you are logged in, if you are on a # prompt you don't need to type sudo.

---

### Post by Rodney9 on 2012-01-04
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by crazy bird on 2012-01-04
> Now ive read the readme file. it says:
1. cd to folder. (Should I hit enter here? Ive done so)
Yes, always hit Enter after each command!
 
> 
2. type: $ sudo ./install.4.18.1.X.sh i (the first time I did it it asked me for password, but then said it was wrong and since then it never asked me for it again. Should I include the $ symbol when typing it out? Now it only says that command not found)
No, never inculde that $ synmbol. Just sudo followed by the command and hit Enter. 
 
What you should do first is this:
- open a terminal
[COLOR=black]- type the following command: [/COLOR]
[COLOR=black]> [COLOR=black]sudo chmod +x install.4.18.1.X.sh[/COLOR]
[/COLOR][COLOR=black]- Hit enter and if requried, type your password[/COLOR]
 
This will make that file executable. Now you can type this command: 
> sudo install.4.18.1.X.sh

If everything goes well, the file will be installed. In fact, it is not even necessary to add sudo before ./install.4.18.1.X.sh. But you could try both ofcourse!
 
 Just some questions: what is the name of that tarbaal you downloaded? What kind of program is it? Is it not available in Synaptic?

---

### Post by mrbambocha on 2012-01-04
It worked. Thanks guys. 
Just wondering why I have to install something through the terminal? Why cant I just klick on the files to start the install? 

Need to read that "Lubuntu One Stop Thread " maybe will understand it better then. Is there a smiliar guide for ubuntu?

---

### Post by crazy bird on 2012-01-04
> **mrbambocha said:**
> It worked. Thanks guys. 
Just wondering why I have to install something through the terminal? Why cant I just klick on the files to start the install? 
Because a tarball is a container file which contains the package files. Compare it with a zip file which contains a Windows exe file.

---

