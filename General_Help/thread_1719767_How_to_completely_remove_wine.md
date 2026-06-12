---
title: "How to completely remove wine"
date: 2011-04-02
forum: General Help
---

### Post by nearlymagicman on 2011-04-02
Hey,


i got the following Problem:

I want to completly remove wine, so i figured that using the package manager, and apt-get remove will make it work.
Using apt-get, i get the message that there is no wine installed, even though the package manager is telling me the opposite.
After that i removed wine via the package manager, but i can still run wine. 
And that is the point where i am getting completly lost, how the hack can i run a removed program?
I did compile and install wine myself once, so the problem might hide there. But how to i remove a program without the routines of the package manager?

I seriously need to deinstall wine completly to figure out a couple misterious problems i am having lately.

thx for your help


(I am using 10.10 64-bit)

---

### Post by Spyderkid on 2011-04-02
go to synaptic package manager and find the package, right click on it and then choose complete removal.... click apply.

then what you'll want to do is delete a couple of leftover folders and files ( im not sure why they don't get deleted) just go to your home directory in file manager press <Ctrl> and <H> then you'll se the hidden folders....
Delete .Wine and its contents..


SOLVED!

---

### Post by 3Miro on 2011-04-02
> **Spyderkid said:**
> go to synaptic package manager and find the package, right click on it and then choose complete removal.... click apply.

then what you'll want to do is delete a couple of leftover folders and files ( im not sure why they don't get deleted) just go to your home directory in file manager press <Ctrl> and <H> then you'll se the hidden folders....
Delete .Wine and its contents..


SOLVED!

+1 for Synaptic Package Manager to get rid of all wine packages and  then Ctr + H for the hidden files. Delete .wine in Places -> Home.

---

