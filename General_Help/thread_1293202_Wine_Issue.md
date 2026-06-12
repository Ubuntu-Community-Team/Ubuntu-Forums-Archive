---
title: "Wine Issue"
date: 2009-10-16
forum: General Help
---

### Post by Fluffy13 on 2009-10-16
I installed Doom3 via WINE with no issues, but im having a problem copying a modified .exe file into the wine "drive" in place of the original. 

The WINE directory is 

/home/steve/.wine/drive_c/Program Files/Doom 3

And the modified exe is at 

~/Desktop/Doom/Doom3.exe

I deleted the original off the wine drive no problem, but you can't just drag and drop due to permissions. So i used the terminal and tried

Quote
steve@Laptop:~/Desktop/Doom$ sudo mv Doom3.exe /home/steve/.wine/drive_c/Program Files/Doom 3


and 

Quote
steve@Laptop:~/Desktop/Doom$ sudo cp Doom3.exe /home/steve/.wine/drive_c/Program Files/Doom 3


and both say "target 3 is not a directory"

the "3" is from the end of the target, but it IS a folder....i dont get it

---

### Post by Rocket2DMn on 2009-10-16
You can't have whitespace in the name the way you have it written out, it thinks the final "3" is another directory.
First set yourself as the owner since you shouldn't have anything in your /home directory structure that you don't control:
```
sudo chown *yourusername*:*yourusername* ~/Desktop/Doom/Doom3.exe
```
Then move:
```
mv Doom3.exe /home/steve/.wine/drive_c/Program\ Files/Doom\ 3
```
or
```
mv Doom3.exe "/home/steve/.wine/drive_c/Program Files/Doom 3"
```

---

### Post by Fluffy13 on 2009-10-16
Thanks man! Had to edit it a little:

mv Doom3.exe /home/steve/.wine/drive_c/Program\ Files/Doom\ 3
but it worked great!

---

### Post by Rocket2DMn on 2009-10-16
Oops, missed the Program\ part, I edited my post for anybody who runs across this in the future - you got the idea!

---

### Post by Fluffy13 on 2009-10-16
Thanks again man :)

---

