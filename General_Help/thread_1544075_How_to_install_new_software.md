---
title: "How to install new software?"
date: 2010-08-02
forum: General Help
---

### Post by no1ninja on 2010-08-02
Hi,
 
I am new to linux and ubuntu. I have installed the x64 10.4LST on my laptop. I need to run this emulator that i downloaded, but its a command and when i unpack it to the desktop and try to execute it in terminal window it does not work.
 
I am so lost, someone please help. Also its says its a i386 command and it may need a 64 bit emulator in the text file. 
 
 
so confused

---

### Post by no1ninja on 2010-08-02
should i install a diffrent unix?

---

### Post by no1ninja on 2010-08-02
ok, what do i do when i have just a file, its a blue diamond in the icons, opening does nothing to it, its not a tar or anything its just  file with a text file that shows me the usage from the command prompt.
 
but its doesn't work when i go to the terminal window and try to run it

---

### Post by Elfy on 2010-08-02
Please don't keep bumping your thread.

As to your issue - no-one here is a mind reader - we'll need a bit more to go on - like what is it you are talking about.

Possibly it will run from a terminal 

```
cd ~/Desktop
./*nameofdownload*
```

---

### Post by no1ninja on 2010-08-02
I need to install:
 
[http://bit.ly/bE7qUa](http://bit.ly/bE7qUa)  this file to my ubuntu
 
[http://bit.ly/bgNh1L](http://bit.ly/bgNh1L) and this one

---

### Post by no1ninja on 2010-08-02
I have read [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) and I am more confused.  I followed this to step 2, but step 3 just make no sense, not sure what i am supposed to do.
 
 
 
 
I coppied both packages to \usr\local\src

---

### Post by worksofcraft on 2010-08-02
Well I have no idea what it is supposed to do, but I downloaded and extracted one of the archives on my desktop. Then I went to a command prompt and this is what it did...


$> ./wfemu
Opening serial device '/dev/ttyS0' (19200,8N1)...OK
Created PTY device '/dev/pts/2'
Startup complete, waiting for commands...
<<([CaID Map], cksum OK)
<<([CaID Map], cksum OK)
<<([CaID Map], cksum OK)
<<([CaID Map], cksum OK)
<<([CaID Map], cksum OK)
<<([CaID Map], cksum OK)
^C

so... um... well it appears to be running but I have no idea what it is doing :shock:

Incidentally if I were you I would run it on a 32 virtual machine in virtualbox.... Well just in case it isn't very safe ;)

---

### Post by no1ninja on 2010-08-02
perfect, that is what I need !! but it doesn't do it on my machine
 
it says that file is not a command, how do i run a virtual 32 bit box?
 
should i just install i386 instead?
 
 
(its nothing bad, its just an emulator for your serial port to deal with satellite recievers, its nothing illegal)

---

### Post by worksofcraft on 2010-08-02
hum... well you can just install the 32 bit Ubuntu and be done with it.

OTOH if you have some spare time you can do
System-Administration->Synaptic Package Manager

then search for Virtualbox.

This lets you create virtual (i.e. pretend) computers in separate windows that can run different operating systems and have different setups and programs installed and you can even network them all together.

When I'm experimenting I wouldn't do it any other way because I can simply restore these virtual machines to an earlier snap shot if anything goes wrong.

---

### Post by mcduck on 2010-08-02
you have to run the command in the same place where the file you want to execute is...

---

### Post by no1ninja on 2010-08-02
thanks for the replies.   I have run the file in its directory, these files are i386 and as such its best i change the distro... will update you guys when that is done

---

### Post by no1ninja on 2010-08-02
Just wanted to say that I solved all my issues.  Got both programs to run perfectly and using an ubuntu machine without complication for my aplication.  
 
 
The key was installing the i386 version, instead of the 64amd because the files i had were compiled with i386.
 
Thanks to all that helped to point me on the right track.
 
 
100% RESOLVED   --  END THREAD

---

