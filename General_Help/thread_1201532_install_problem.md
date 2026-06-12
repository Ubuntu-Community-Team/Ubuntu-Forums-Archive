---
title: "install problem"
date: 2009-07-01
forum: General Help
---

### Post by *Gilly* on 2009-07-01
[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG] 				**install problem** 			
 			 			 		   		 		 		trying to install ubuntu ,to dual boot with windows 7 

  after click install then the loading bar starts and after about 30 seconds get this


[ 2.436018 ] ata1; softreset failed device not ready

[ 3.084018 ] ata2; softreset failed device not ready

loading please wait

bus box v1.10.2 (ubuntu1.1.10 2-2 ubuntu7) built-in shell (ash)

enter help for a list of built in command.

(initamps)




any idea what wrong?

i just installed this on a vista computer using this cd with no problem

---

### Post by *Gilly* on 2009-07-01
> ***Gilly* said:**
> [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]                 **install problem**             
                                                                trying to install ubuntu ,to dual boot with windows 7 

  after click install then the loading bar starts and after about 30 seconds get this


[ 2.436018 ] ata1; softreset failed device not ready

[ 3.084018 ] ata2; softreset failed device not ready

loading please wait

bus box v1.10.2 (ubuntu1.1.10 2-2 ubuntu7) built-in shell (ash)

enter help for a list of built in command.

(initamps)






any idea what wrong?

i just installed this on a vista computer using this cd with no problem
cough,cough ,bump bump

---

### Post by ronaldprettyman on 2009-07-01
Yes your installed failed, ATA sounds like a harddrive problem(no experts) when you get an ash prompt its usually from a failure on disk. (SEE /etc/fstab you / partition has a line mount=ro on failure so when in the ash console your partition is ro anyway not much you can do).
Start over best bet. Partition the disk from the live cd using gparted(alt+f2 gparted). Leave an empty section at the beginning of the drive for windows 7(unless your doing seperate drives).

Install Windows First.
Then install Ubuntu.

It works better to partition in advance rather then trying to rely on a resize during installation.

I hope this helps, but more details would help me to better assist you.

---

### Post by Bucky Ball on 2009-07-01
+1. As above; go again and let us know how you went, along with Ubuntu version, hardware details, computer make/model and anything else you can think of. :)

---

### Post by *Gilly* on 2009-07-01
acer aspire m3 201
phenom quad core
2 gb ram

2 hardrives**(c*). 149GB NTFC
                  (d*). 147gb NTFC

not sure what version of ubuntu i presume the latest one because i only just downloaded it a few day ago downloading from official site

---

### Post by ronaldprettyman on 2009-07-01
> ***Gilly* said:**
> acer aspire m3 201
phenom quad core
2 gb ram

2 hardrives**(c*). 149GB NTFC
                  (d*). 147gb NTFC

not sure what version of ubuntu i presume the latest one because i only just downloaded it a few day ago downloading from official site

I will asume windows is already installed to C and assume that D is empty if not migrate everything off of D
Run the install and do a complete install to disk and make sure its the D drive which is more then likely going to be called
/dev/sdb
or
/dev/hdb
Do a full disk install to the second disk and your be good to go. If you want to access it from windows google ext2 windows drivers and install support for ext2 in windows and your be able to read your linux drive

---

### Post by *Gilly* on 2009-07-01
> **ronaldprettyman said:**
> I will asume windows is already installed to C and assume that D is empty if not migrate everything off of D
Run the install and do a complete install to disk and make sure its the D drive which is more then likely going to be called
/dev/sdb
or
/dev/hdb
Do a full disk install to the second disk and your be good to go. If you want to access it from windows google ext2 windows drivers and install support for ext2 in windows and your be able to read your linux drive
 no its full witgh media that drive .
but regardless that doest matter because it just refuses to install it even wont let me do the demo option 
 
 
i boot the cd   then choose my language  then click install (and ive tried the demo option with same results)
 
then the screen goes black for a second then the error message pops up for a few seconds.. n then the ubuntu starts loading  and after about 30 seconds i get ^^that^^ error message what i posted in 1st post.
 
ive just reinstaled windows and still have the same problem  **HUGE SIGH**

---

### Post by ronaldprettyman on 2009-07-02
> ***Gilly* said:**
> no its full witgh media that drive .
but regardless that doest matter because it just refuses to install it even wont let me do the demo option 
 
 
i boot the cd   then choose my language  then click install (and ive tried the demo option with same results)
 
then the screen goes black for a second then the error message pops up for a few seconds.. n then the ubuntu starts loading  and after about 30 seconds i get ^^that^^ error message what i posted in 1st post.
 
ive just reinstaled windows and still have the same problem  **HUGE SIGH**
When booting you want to get advanced option and add the end of the kernel out put add 
nomsi
after splash
or under advanced options nomsi
Can someone else explain the nomsi thing its been awhile

but i had a similar problem with a dell machine at work and the nomsi did the trick, I ended up going with debian on it though cause it was the easiest one to get around the hurdle with

---

### Post by *Gilly* on 2009-07-02
> **ronaldprettyman said:**
> When booting you want to get advanced option and add the end of the kernel out put add 
nomsi
after splash
or under advanced options nomsi
Can someone else explain the nomsi thing its been awhile
 
but i had a similar problem with a dell machine at work and the nomsi did the trick, I ended up going with debian on it though cause it was the easiest one to get around the hurdle with
 what so this is a known issue then 
 
ive tried installing [Mandriva]("http://www.mandriva.com")and another one i cant remember the name of 
with the same problems 
 
ill give debian a crack

---

### Post by *Gilly* on 2009-07-06
> ***Gilly* said:**
> what so this is a known issue then 
 
ive tried installing [Mandriva]("http://www.mandriva.com")and another one i cant remember the name of 
with the same problems 
 
ill give debian a crack
 had the same problem tried 4 different linux now and none will install 
 
i googled that error message and seems alot of people are experiencing the same problem  
 
my hardware is all fine ive reinstalled everything same errors though
 
could someone explain that nomsi thing in abit more depth please

---

### Post by Bucky Ball on 2009-07-06
BTW, Gilly; not sure if I suggested this but have you tried the Alternate Install version of 8.04 LTS? You never know.

---

### Post by *Gilly* on 2009-07-06
> **Bucky Ball said:**
> BTW, Gilly; not sure if I suggested this but have you tried the Alternate Install version of 8.04 LTS? You never know.
ill give it a go
 
[http://linux.softpedia.com/progDownload/Ubuntu-Hardy-Heron-Download-32974.html](http://linux.softpedia.com/progDownload/Ubuntu-Hardy-Heron-Download-32974.html)
 
which one of these should i download i want 32 bit and direct download rather than torrent because my torrents are slow as **** at this time of the day but fast direct from web

---

### Post by Bucky Ball on 2009-07-07
Go here:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Click on the 'complete list of download locations.' Choose a location and navigate to the '8.04' or '8.04.2' folder and then navigate to the 'alternate i386' iso.

Wherever you download from the i386 alternate installer is the one you are looking for. :)

---

