---
title: "copy files to a usb at random?"
date: 2010-04-14
forum: General Help
---

### Post by antaresca on 2010-04-14
Hello
I have the following problem
I want to  copy files to a usb at random?
My_mp3_400GB to my_usb_32GB
jijiji:) is enough?

But I have  little idea how to do it on command, Greetings!
 I want to  copy files to a usb at random?
cp My_mp3_400GB/  /my_usb_32GB????

---

### Post by kaibob on 2010-04-14
Someone asked a similar question a while back, and I wrote a shell script in the following post. It's a bit more complicated because the OP in that thread wanted to limited the total size of all files copied. 

[http://ubuntuforums.org/showpost.php?p=8920735&postcount=6](http://ubuntuforums.org/showpost.php?p=8920735&postcount=6)

Perhaps another forum member will have a simple one-liner for you.

---

### Post by LaptopU on 2010-05-07
[http://ubuntuforums.org/showthread.php?t=1475003](http://ubuntuforums.org/showthread.php?t=1475003)

Copy the code to a new blank file and call it something like 'Random file copy'.  Then place this file in ~/.gnome2/nautilus-scripts directory.  Then you will be able to right-click on your USB drive on the desktop, select scripts - random file copy, it will say what is the source directory, you point it to wherever you want, it then says how much space is free on the device and how much of that space do you want to fill, you choose then press OK.  It does the rest.

---

