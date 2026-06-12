---
title: "Word Mole for Linux"
date: 2011-07-26
forum: General Help
---

### Post by TFrog on 2011-07-26
For those who have a Blackberry cellular phone and found the game Word Mole addictive as I have, I've found the answer for you running it on your Linux based PC.  Follow the instructions below:

1)  Download the WordMoleSetup.msi from [http://sourceforge.net/projects/wordmole/files/Current%20Releases/](http://sourceforge.net/projects/wordmole/files/Current%20Releases/)

2)  Make sure you have cabextract installed via your favorite package manager (mine is Muon).

3)  Open a terminal and navigate to the folder in which you downloaded the file into or copied it over into as a temporary file/folder.

4)  Extract the files from the compressed file using:
            cabextract WordMoleSetup.msi

5)  Keep the .jar, .ico, .txt file from the extraction process.  Delete all other files

6)  Move the saved files to any folder you choose then you can do one of two things:
            A)  execute the game from a terminal via:
                    java -jar (jar file name)
            B)  create a menu item for it and execute it via a bash
                script.

Myself, I run Kubuntu so all I did was created a bash script that would navigate to the game folder and execute the jar file once there.  Then I opened up Kmenuedit and created a menu item for it and used the bash script as an executeable once the proper properties were set.

As to why saving the ico file.  Simple.  Use a graphics program and convert the ico to a png file for your menu's icon.

Happy Gaming :-)

P.S.  There is no sound as of yet.  It appears the developer hasn't gotten around to it yet.  Nor is there options or bonus rounds.

---

### Post by Fardin on 2012-05-06
Help Please
I followed up to step 6 then I got lost. (I'm not familiar with terminal and commands etc.)
Could someone explain how I could do step 6.
I guess option 6-a is easier than 6-b.
Thanks

---

