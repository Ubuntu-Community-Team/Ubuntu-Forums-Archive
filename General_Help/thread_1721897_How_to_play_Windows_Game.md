---
title: "How to play Windows Game?"
date: 2011-04-05
forum: General Help
---

### Post by chand.sethi77 on 2011-04-05
I had windows 7 and I was addicted to play GTA san andreas multi-player. It is still in my computer > C:/ PROGRAM FILES/ROCKSTAR GAMES/samp.exe
I want to play that now but when I click on samp.exe it opens with File Roller 2.30.1.1
HOW TO PLAY THAT! PLEASE HELP. 
THANKS!

---

### Post by Grenage on 2011-04-05
Linux and Windows are very different operating systems; applications written for one will not work on the other.  There are compatibility apps, such an WINE, but there is never a guarantee that it will work.

---

### Post by chand.sethi77 on 2011-04-05
So, Does that mean I can't play the game on UBUNTU or I have to download the game again compatible with ubuntu? O.o

---

### Post by Grenage on 2011-04-05
> **chand.sethi77 said:**
> So, Does that mean I can't play the game on UBUNTU or I have to download the game again compatible with ubuntu? O.o

It's not quite that simple.  Most (99.9%) games are made for Windows alone; some also have Mac versions, but those are few and far between.  As I said before, you can try using WINE and/or a GUI for it called PlayOnLinux - but there are no guarantees.

I recommend using Windows to play Windows games - it's a hell of a lot easier.

---

### Post by 3Miro on 2011-04-05
You can try wine, many windows game can run under Linux, however, getting them to run is often tricky. You should start by installing wine from the software center and then going to:

[http://www.winehq.org/](http://www.winehq.org/)

Look into their database for the game that you want to play and then follow precise instructions for that game in particular. This is also the best place to report problems as the people on winehq are the most knowledgeable on the subject. I have a feeling very few people here actually use wine.

Wine is very specific. I use wine myself, but I wouldn't know how to help you since I don't play GTA in particular.

---

### Post by chand.sethi77 on 2011-04-05
Okay. Thanks. 
I have another query..
I want to copy some files from home folder > DAV (my directory in which I have those files)
to /var/www/dav
I tried ```
 sudo cp /home/dav /var/www/ 
```
but it gives the following error:
```
 cp: cannot stat `/home/DAV': No such file or directory 
```
BUT THAT DIRECTORY EXIST!

---

### Post by Grenage on 2011-04-05
Linux is case sensitive, and the output makes reference to DAV, not dav.  You'll also likely need the recursive option (-R) if copying a folder.  Dare I ask why you'd copy it to var/www?

---

### Post by mastablasta on 2011-04-05
more info on your particular question can be found here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780)
 
EDIT this is regarding San Andreas quesiton.

---

### Post by chand.sethi77 on 2011-04-05
Hmm i tried :
```
 sudo cp /home/DAV /var/www 
```
Error was ```
cp: cannot stat `/home/DAV': No such file or directory
 
```
Then I tried ```
sudo cp /home/chaand/DAV /var/www
 
```
then it says cp: omitting directory `/home/chaand/DAV'

---

### Post by Grenage on 2011-04-05
> **chand.sethi77 said:**
> Hmm i tried :
```
 sudo cp /home/DAV /var/www 
```
Error was ```
cp: cannot stat `/home/DAV': No such file or directory
 
```
Then I tried ```
sudo cp /home/chaand/DAV /var/www
 
```
then it says cp: omitting directory `/home/chaand/DAV'

These directories do actually exist, right?  For example, my user name is *grenage*, so my home directory is *grenage*.  I have a directory called *photos*, and I want to copy it:

```
cp -R /home/grenage/photos /var/www/
```

Not sure why you'd use /var/www, though.

---

### Post by chand.sethi77 on 2011-04-05
```
 sudo cp -R /home/chaand/DAVI /var/www 
```
This code worked! 
Thanks :)
Well what does that -R means though?

---

### Post by Grenage on 2011-04-05
Recursive ;)

---

### Post by chand.sethi77 on 2011-04-05
Oh man.. another problem.... Some pages (I can count them - Yahoo-login, Hotmail- Login and the files I just copied- index.html ) These pages doesn't open at all. It just shows me title of pages and keep loading for years still doesn't appears  in browser. :(

---

### Post by Grenage on 2011-04-05
Are these pages you're browsing on the internet, or pages you're trying to host on your own computer?

---

### Post by Mark Phelps on 2011-04-05
You started out asking about Windows games -- now you just keep branching out. It's considered bad form to just keep adding and adding to the same thread -- each time, for a very different problem.

Please start a new thread for each new problem.  That way, folks experienced in solving the new problem will see your thread.  You will get better overall community support that way.

---

### Post by mastablasta on 2011-04-06
did you install restricted extras package? 
 
and you really should open a new thread for new issue.

---

