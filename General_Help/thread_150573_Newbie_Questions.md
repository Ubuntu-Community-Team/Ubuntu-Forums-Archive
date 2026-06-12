---
title: "Newbie Questions"
date: 2006-03-26
forum: General Help
---

### Post by stocker on 2006-03-26
Hello, I am a newbie to Linux and was wondering something, 

I have two questions:

How am I able to install drivers for a ATI Radeon 9200 SE

AND

How do I install software that is in source or .tar format?

Thank you,

Matt

---

### Post by Ramses de Norre on 2006-03-26
1) in terminal: sudo apt-get install xorg-driver-fglrx
Then sudo gedit /etc/X11/xorg.conf and search the line that says 'Driver: "ati"' and change ati in fglrx.

2) You'll need to compile it, first sudo apt-get install build-essential. Then tar -xvzf path_to_file to untar a .tar.gz or tar -xvjf path_to_file for a .tar.bz2 file.
Then run ./configure in the source dir and take a look at the output, everything should be ok, otherwise install the needed packages. (Ask if you don't know what to install).
If ./configure says everything is ok do make && sudo make install.

---

### Post by halitech on 2006-03-26
not much help on installing the drivers as mine worked out of the box (intel onboard piece of junk)  but for the software you will need to open a terminal and type 

tar -xvfz name_of_file.tar 
./configure
make

from memory that "should" work but hopefully someone will come along shortly and tell me if I'm right or wrong


***edit 
okay, Ramses beat me to it and got it correct for me, looks like I was on the right trail for it though so point for starting to ermember things

---

### Post by TwistesdTexan on 2006-03-26
I think its best to go to your home folder an create a new folder and name it so you will remember what is in it. Then move the tar file into the new folder. Right click the tar file and extract it in the new folder.:) As for the driver, There is a tar you might want to find called EasyUbuntu. It will correct alot of problems and includes a few video drivers.[http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2](http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2)

---

### Post by stocker on 2006-03-26
OK thanks for the advice, where would I find this EasyUbuntu that you were talking about TwistedTexan?

---

### Post by TwistesdTexan on 2006-03-26
I sent a pesonal but thought it good to repost it here. It is in the launch pad. This is the address. [http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2](http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2)
I spent about a week trying to make my DVDs work the first time but the second time took minutes. Good luck!!!

---

### Post by stocker on 2006-04-02
Ok thanks a lot for the help everyone.

Matt

---

### Post by Iandefor on 2006-04-02
It might also be useful to note that, in order to compile software from source, you need the package build-essential. Install it via Synaptic or open up a terminal and use the command ```
sudo aptitude install build-essential
```

---

### Post by stocker on 2006-04-02
Is there anyway that I can get the packages that EasyUbuntu needs because I cannot get onto the internet with my Ubuntu PC, only my Windows PC which is downstairs.

Thanks

Matt

---

### Post by mdm4301 on 2006-04-03
You can download the .tar file on your windows computer and then burn it to a cd or put it on a usb drive to move  the file to your ubuntu computer.

---

### Post by nanotube on 2006-04-03
by the way... a really good idea is to replace the final "make install" step with "checkinstall". checkinstall makes a .deb package out of the stuff, and installs it using the apt system, so that you can later uninstall it through apt-get or synaptic. a really nice thing, because otherwise you are likely to be unable to uninstall cleanly, if you do decide to do that. 

checkinstall is available as a package in the repositories. :)

---

### Post by stocker on 2006-04-03
[QUOTE=mdm4301]You can download the .tar file on your windows computer and then burn it to a cd or put it on a usb drive to move  the file to your ubuntu computer.[/QUOTE]

Yeah, I did this, but it kept saying that it had to connect to places like wine.sourcefourge.net and places like that.

---

