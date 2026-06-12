---
title: "Adobe Flash Player 10 Crashes Firefox 3"
date: 2009-09-15
forum: General Help
---

### Post by Magnys on 2009-09-15
Hi, 

I am currently using Ubuntu 8.10, Adobe Flash 10.0.32.18, and AMD 64.
I am a complete noob to linux and have considered setting my laptop on fire numerous times over the weekend.:lol: 

I just installed Adobe 10, and it seems to crash firefox quite often.  Any help would be greatly appreciated.:P


Thanks in advance, 
Magnys

---

### Post by NoaHall on 2009-09-15
The 64 bit alpha? If not, follow this -> [http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html)

---

### Post by Magnys on 2009-09-15
Yes 64 bit alpha

---

### Post by NoaHall on 2009-09-15
Hm. Try updating to 9.04? It's wise to move now, so you're ready for the change to 9.10 :)

---

### Post by Magnys on 2009-09-15
I tried to install 9.04 yesterday, however i couldn't even enter my user name in the login screen. It completely froze up my comp. I did a fresh install of 8.10 earlier. 

Thanks for the fast reply.

---

### Post by NoaHall on 2009-09-15
Hm, maybe you should go back to 8.04, and wait for karmic and see if repairs anything for you :)

What graphics card do you have?

---

### Post by Magnys on 2009-09-15
Sorry for the delayed response.
Perhaps I should try 8.04. I'll probably play with that later tonight.
I have an ATI Radeon Mobility 9600.


Also the method I used to install the plugin was as follows:

Downloaded the tar.gz file from adobes site.
Saved it to my desktop.
Tried to remove any existing flash players but found none installed using synaptic, and the terminal.
Extracted the adobe file and copied the libflashplayer.so file to my home .mozilla/plugins folder.




[COLOR=Red]EDIT SOLVED:[/COLOR] I seem to have fixed the problem by installing the Ubuntu Restricted Extras Package.

Open terminal

sudo apt-get install ubuntu-restricted-extras


Full guide located here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)


Thanks very much for your help NoaHall. I certainly appreciate your time.

---

