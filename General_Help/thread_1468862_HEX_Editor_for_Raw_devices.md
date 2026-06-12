---
title: "HEX Editor for Raw devices"
date: 2010-05-01
forum: General Help
---

### Post by vibra on 2010-05-01
Hi guys


I'm trying to hack my htc smartphone to get root access from it. Some  guys did an amazing work writing down a tutorial to do it, but, shame of  shames, they did it in Windows OS. 

No problem until here, because what it can be done in M$Win can be done  in Linux too. But, at certain point of the procedure we need to  write/mapping to the device (to produce a goldcard).

In windows there is a tool HxD Hex Editor with the functionality of open  a disk  (in this case a SD Card) in hexdecimal. It runs in wine, but,  that specific feature is not working. :(

I know there are some hex editors in linux I tried lots of them, e.g. ghex, okteta, hexedit, etc, but most of them only can open files and the others are to hard to do the simple operation that i need.  I know I can do  'sudo hexdump /dev/sdb1' to dump to the shell the  device in hex format, or hexedit to edit the device. But,  I'm getting huge troubles to do it. 



I should say that what i need to do is copy the contents of an hex file and paste it into the device. :P



So, can you point me out a tool to perform this operation in an  automated way, or, suggest me a site with examples to do this in shell? :)




.

---

### Post by robvas on 2010-05-01
Can you dump it with dd to a file, and then open that file in a traditional hex editor? Then dump it back with dd.

---

### Post by vibra on 2010-05-01
> **robvas said:**
> Can you dump it with dd to a file, and then open that file in a traditional hex editor? Then dump it back with dd.

Hmm. Yes. That can be an acceptable workaround. 

But, I would like to do it directly with an editor, because doing this with files will be very slower. :(

---

### Post by themuddler on 2010-07-24
Vibra,

I'm also trying to root my HTC smartphone using Ubuntu and have met the same problem as you have after presumably following the same guide.  How did you solve this in the end?

Thanks.

---

### Post by vibra on 2010-07-24
> **themuddler said:**
> Vibra,

I'm also trying to root my HTC smartphone using Ubuntu and have met the same problem as you have after presumably following the same guide.  How did you solve this in the end?

Thanks.


Well...  I didn't solve the problem. I think I have installed all the hex editors for linux in the world to do the goldcard, but without any luck... It doesn't exist any hex editor intuitive and with the functionalities as the one for windows.  

In the end I figured out that my phone don't need a goldcard, because it's unblocked (and only phones blocked to a newtwork operator need the goldcard).

---

### Post by kev77 on 2010-10-15
Found a link for ubuntu goldcard, not tested by me!  [http://www.nazriawang.com/2010/04/how-to-create-goldcard-with-ubuntu.html]("http://www.nazriawang.com/2010/04/how-to-create-goldcard-with-ubuntu.html")  :)

EDIT: it worked! this guide is a bit patchy, it mentions writing the goldcard image to sdx1, when it should be sdx (x being b etc your SD card prefix) Also as i'm using LXDE i replaced "gedit" in the bash to "leafpad" change to suit your Xversion, i will attempt flashing my hero (t-mobile g2) with villain 1.5 and post the results,

---

