---
title: "Dual Boot (Ubuntu 11.10) the solution to all guitar pro 6 problems"
date: 2011-10-20
forum: General Help
---

### Post by Finn bjerke on 2011-10-20
A lot of people have problems with Guitar pro 6 and Ubuntu, guitar pro costs money (59 usd) 
 
1. The programme does not install (maybe due to "dependencies" what ever that is ..) 
2. The import function is not working 
 
If you want Ubuntu and guitar pro 6 to work together and have the import facilities, here is how you do it. This is the solution to all your problems I kid you not. 
 
1. forget about 64 bits, it not really needed for guitar pro 6. 
2. Install Ubuntu 11.10 AND 10.10 using Dual boot option, its easily done. 
3. Install Guitar pro under Ubuntu 10.10 it works very well including soundbanks. 
4. Install tuxguitar under Ubuntu 10.10,this little program can batch convert from any format (almost) to Gp5 format so you convert all your files in 5 minutes. Tuxguitar is freeware. 
5. Use Ubuntu 11.10 for 64 bit stuff. 
 
Reboot time is 27 seconds you can live with that. (?) 
 
Et voila you now have a machine with Ubuntu 10.10 and guitar pro 6 plus tuxguitar it works, its easy to install you can convert files. Also you have Ubuntu 11.10 64 bits version for other PC things you want to do. 
 
One fine day guitar pro 6 will work with Ubuntu 11.10, you see the guitar pro people just need to talk to the canonical (ubuntu) people about it, in civilised parts of the world this is called "teamwork" When Ubuntu and Guitar pro work together you can delete the Ubuntu 10.10 partition. This operation will take some hours of your precious time, but you will have no more technical problems and yu can focus on MUSIC. 
 
Do dualboot and then play guitar.

---

### Post by Finn bjerke on 2011-10-21
Regarding dependencies The support people for guitar pro 6 wrote this to me, when I complained about guitar pro 6 not launching under Ubuntu 11.10:
 
*"You are right, we have forget to put libssl on the dependencies. It is now fixed, we will release the new package as soon as possible. In the meantime simply install libssl 0.9.8 before using GP6.1" *
 
I Dont know if its relevant or helpfull.

---

### Post by Finn bjerke on 2011-10-28
NOW it seems to be working Using Ubuntu 11.10 and guitar pro 6.1, the import is not working. So forget about the dual boot.

---

### Post by Finn bjerke on 2011-11-09
If you prefer to have guitar pro in Ubuntu 11.10 Unity 32 bits you will need 

libssl.so.0.9.8


So here is how you do it in Ubuntu 11.10 

Install Guitarpro 6.1 

[LIST]
[*]
In case its not loading  

Install synaptic from the software center 
From synaptic install libssl.so.0.9.8  
Enter password etc.  (dont forget: password is not your guitar pro password but your Ubuntu password)  
Download sounbanks from internet (2gig) 
ENJOY...  




[*]
[/LIST]
So you dont need dual boot after all, unless off course you have problems with 64 bits. In that case you might consider a combination og dual boot with 32 bits and 64 bits. However the guitar pro people believe they have solved that problem.

---

