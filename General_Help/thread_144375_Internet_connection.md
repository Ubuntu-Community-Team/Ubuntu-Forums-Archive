---
title: "Internet connection?"
date: 2006-03-14
forum: General Help
---

### Post by baysl on 2006-03-14
I have adsl connection and router. My IP is dynamic.
In windows I dont have to do anything and internet works.

What do I have to do to start using internet in Ubuntu?

And another question:
I have a program on my PC that is compatible with linux.
When I double click install error accurs.
How do I install programs in ubuntu?

---

### Post by mavr on 2006-03-14
About the connection there are a few things you need to know before u can get it working with linux. If you are using a dhcp on windows and that is possible if u say that is automatically configured, you will have to know your gateway ip address. You can find it looking at the state of your internet connection on windows. Insert that when promted during the installation, or go to your internet connection secting on linux e say automatic and insert that ip address when asked. 

About the program that is working on both linux and windows i am sorry but that is not possible unless u are using some crossover application. Most of the programs, like yours, comes with a linux installation, that u have to download and install. How to install on ubuntu is a bit more complicated to explain, but if u tell us what program u were going to install we can be more helpful. Normally u can find what u are looking for in Synaptic or Adept. If not, just look on one of the guides you find on internet about add more repositories to your source.list

---

### Post by cjazz on 2006-03-14
It will be interesting to hear the OP's reply. As I read his or her post, I see nothing about a program that works under both Windows and Linux. He or she describes it as "compatible with Linux," but it's not clear what that means.

baysl, what is the program you're trying to install? What is the name of the install file? If it has an .exe extension, it's a Windows program, which means it doesn't run natively under Linux, although it might run in an emulation-like environment.

For many Wndows programs, there is a perfectly good Linux equivalent, which can be installed, as mavr describes, through synaptic or adept.

---

### Post by cjazz on 2006-03-14
baysl, I forgot to address your last question. There are some very nice tutorials on installing software at [www.psychocats.net/ubuntu/installingsoftware.php](www.psychocats.net/ubuntu/installingsoftware.php) and [www.psychocats.net/ubuntu/sources.php](www.psychocats.net/ubuntu/sources.php). In fact, you might find the entire site worth reading.

Thanks to aysiu for the tutorials.

---

### Post by mavr on 2006-03-14
The only way to be "compatible" with linux is to be in java or in another portable language. That is why i thought he/she was talking about a program that does have a version for linux as well.

---

### Post by baysl on 2006-03-14
That program is emule.exe.
Did I have to download a different file?
Exe files dont work in Linux?

---

### Post by cjazz on 2006-03-14
Exe files are generally Windows (or in some cases DOS) programs, and of course Linux is a different operating system. There are ways to make such programs run under Linux, but I strongly suggest you look for native Linux equivalents. If you google the terms "emule+Linux," a number of Linux equivalents turn up. You may want to look into those.

I also strongly suggest you do some reading on installing programs under Linux, including the Web sites I suggested earlier. With Ubuntu, that knowledge will be a godsend.

---

### Post by zubrug on 2006-03-14
[QUOTE=cjazz]baysl, I forgot to address your last question. There are some very nice tutorials on installing software at [www.psychocats.net/ubuntu/installingsoftware.php](www.psychocats.net/ubuntu/installingsoftware.php) and [www.psychocats.net/ubuntu/sources.php](www.psychocats.net/ubuntu/sources.php). In fact, you might find the entire site worth reading.

Thanks to aysiu for the tutorials.[/QUOTE]
great info, thanks
baysl - for adsl use "sudo pppoecof" in terminal (Applications - Accessories) then password, hit enter, if a detection is made prior to reaching 100%, follow instructions (username/password) yes,yes etc. until the terminal returns with a connection, exit.
if unsuccesfull your connection is dhcp/other, good luck

---

