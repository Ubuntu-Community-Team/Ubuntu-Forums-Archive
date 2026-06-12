---
title: "Matlab R2008b on ubuntu amd64"
date: 2009-10-11
forum: General Help
---

### Post by jayeshbhat55 on 2009-10-11
hi

I downloaded matlab for linux from this link [http://thepiratebay.org/torrent/4510366/Mathworks.Matlab.R2008b.UNIX.DVD.ISO-TBE](http://thepiratebay.org/torrent/4510366/Mathworks.Matlab.R2008b.UNIX.DVD.ISO-TBE) 

I am unable to unpack it using archive manager. Any soln?? 

Thank u

---

### Post by StuartN on 2009-10-11
> **jayeshbhat55 said:**
> I downloaded matlab for linux from this link thepiratebay
I am unable to unpack it using archive manager. Any soln??

Yes, try [http://www.mathworks.com/products/matlab/tryit.html?ref=ml_b&s_cid=ML_b1008_ltdn](http://www.mathworks.com/products/matlab/tryit.html?ref=ml_b&s_cid=ML_b1008_ltdn)

---

### Post by jayeshbhat55 on 2009-10-11
hey tats not what I meant. I know torrent downloads are illegal n all but I wanna jus give it a try.

The downloaded document contains .rar files like matu2k8b.r1 to matu2k8b.r78 and matu2k8b.rar. I have no idea how to unpack it!..if i try to use archive manager to unpack  matu2k8b.rar  i get the msg--Could not open "matu2k8b.rar" Archive type not supported..

Kindly help.

---

### Post by cb951303 on 2009-10-11
just extract the matu2k8b.rar file and you will end up with an iso
then extract it because you will have to make the "install" script executable. run it. you're done :popcorn:

---

### Post by jeneverboy on 2009-10-11
Have you installerd unrar?
[http://tips.webdesign10.com/how-to-open-a-rar-file-in-linux]("http://tips.webdesign10.com/how-to-open-a-rar-file-in-linux")

Also, there are some known problems with Matlab on UBUNTU. For instance when you 've edited a .m file and run it, you cannot change the .m file again unless you close the file and reopen it. I run into that problem but just had no time to give it a closer look yet.

Good luck

---

### Post by jayeshbhat55 on 2009-10-11
Thats exactly what I had done. My archive manager didnt hve unrar package. The .rar file did not get extracted completely however installation went on smoothly. Now trying to run n customise it.

@ jeneverboy
 What are the other issues with running matlab on ubuntu?? i read that plotting isnt as great as in windows..

---

### Post by cb951303 on 2009-10-11
I'm running R2009a (the latest student version) and I don't have any problem (including the above)

---

### Post by jeneverboy on 2009-10-12
I'm running matlab R2007b (legal version) with the problems mentioned by meself. The plotting works fine as far I know. guess I'll have to switch to 2009 version.

---

### Post by keplerspeed on 2009-10-12
As an alternative, try octave, and the GUI frontend, qt-octave. I did a course on Matlab at Uni last year, where I coded all my assignments in octave. It is 'generally' transferable code. And octave is FOSS!

---

### Post by jayeshbhat55 on 2009-10-12
Working on matlab in ubuntu has been so far so good.N its way faster than windows:). As i mentioned earlier my prob is wid plotting figures

 Ex.
figure (1)
subplot(2,1,1)
plot(1:k,yp,'-g',1:k,ym)
subplot(2,1,2)
plot(1:k,change)
figure (2)
plot(1:k,error)

It will plot figure (1) properly but when figure (2) is about to be plotted it will get garbled with other windows. I have attached screenshots. 
Kindly observe figure (2) carefully. This happens 4/10 times when I plotting multiple figures.

Do i need any additional packages to get around this prob. My java is up-to-date. 

Thanx

---

### Post by cb951303 on 2009-10-12
What version are you using?
I'm using R2009a 64-bit and I don't have that problem. Screenshot below.

---

