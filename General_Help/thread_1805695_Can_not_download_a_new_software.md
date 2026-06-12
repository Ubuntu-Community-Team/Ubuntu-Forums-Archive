---
title: "Can not download a new software"
date: 2011-07-16
forum: General Help
---

### Post by Salahuddin on 2011-07-16
hi 
i'm new with ubuntu and linux at all 
when i was trying to play a video or an mp3 file , it asks for downloading an add-in and asks my permission to search , when i click search , there's a window appear in a second an disappears again 

i tried to search for a new media player in " ubuntu software center ' 
but when i write what i want to search for , it still searching for a long time and nothing happen .

please i need your help with these two problems .

thanks for your time

---

### Post by mvmacd on 2011-07-16
The default player doesn't have the MP3 codec pack.  Simply install and  use VLC Media Player, for it is much better than Banshee or whatever it's called, and you do not have to worry about codecs.  If your Software center thing doesn't work for searching, open a terminal. Type
```
sudo apt-get install vlc
```
Type in your password, and then it will install.  :)

---

### Post by Salahuddin on 2011-07-16
i have typed what you told me but there was an error


Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

??

---

### Post by mvmacd on 2011-07-16
Hmm.. apparently it's not the front end software program's fault ["Install Software" program],  but the backend [apt-get].  Well, try this:
```
sudo apt-get update
```
Does that work? If it does, then try the previous command after it.

---

### Post by Rubi1200 on 2011-07-16
Hi and welcome to the forums Salahuddin :)

Open a terminal with Ctrl+Alt+T and run the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command removes any corrupted package lists, the second refreshes them.

For best results and to avoid errors, copy and paste the commands to the terminal.

---

### Post by Salahuddin on 2011-07-17
Thank you for your replies 
but [mvmacd]("http://ubuntuforums.org/member.php?u=705988") when i wrote the code [[
sudo apt-get updateThere were alot of links and downloads i guess but ther was a message below 
{{
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
}}

Then i wrote the code 
sudo apt-get install vlc


and the same error appeared
{{
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n  _Translation-en
E: The package lists or status file could not be parsed or opened.
}}

Thank you again.


Thank you [Rubi1200]("http://ubuntuforums.org/member.php?u=1040746") very much 
your code worked very well , and the problem of ubuntu software center is solved by now , and i feel so good now 

Now i want to learn how to write this code and when to write what . you understand . ?
i just want a book . or video or any good thing to teach me 

thanks

---

### Post by Swagman on 2011-07-17
download this book

[http://ubuntupocketguide.com/ubuntukungfu.html](http://ubuntupocketguide.com/ubuntukungfu.html)

---

### Post by Rubi1200 on 2011-07-17
I am glad you got this fixed :-)

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

### Post by Salahuddin on 2011-07-18
thanks for all of you .

---

