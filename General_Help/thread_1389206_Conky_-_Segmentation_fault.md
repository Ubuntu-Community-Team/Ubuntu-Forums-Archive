---
title: "Conky - Segmentation fault"
date: 2010-01-24
forum: General Help
---

### Post by houserparker on 2010-01-24
On the initial installation of conky i was able to run conky from the terminal successfully. After installing conk-colors config i now recieve the message below:-

Can anyone help?

ben@ben-laptop:~$ conky
Conky: desktop window (1a000a8) is subwindow of root window (9b)
Conky: window type - override
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer
Conky: obj->data.i 2 info.cpu_count 1
Conky: attempting to use more CPUs than you have!
Segmentation fault
ben@ben-laptop:~$

---

### Post by VCoolio on 2010-01-24
Your config is made for pc's with dual processors; apparently you have only one, so edit your config accordingly. Also check [this thread]("http://ubuntuforums.org/showthread.php?t=1370286").

---

### Post by Saiko Berry on 2010-01-24
Yeah erase the cpu2 stuff in your configuration.

---

### Post by houserparker on 2010-01-24
Thanks for the replies but how do i get to the configuration? There seems to be so many different ways that have been posted.

---

### Post by VCoolio on 2010-01-24
Isn't there a hidden .conkyrc file in your home folder?

---

### Post by Saiko Berry on 2010-01-24
Open terminal and type locate conkyrc.
Go there, edit that.

---

### Post by houserparker on 2010-01-24
At an earlier stage in configuring conky i created a directory called Conky in my home folder. This is the only .conkyrc file i know of. 

Since compiling conky-colors.tar.gz i don't know whether conky is using another .conkyrc file that conky-colors.tar.gz has created or the file i created in my home folder.

---

### Post by houserparker on 2010-01-24
At an earlier stage in configuring conky i created a directory called Conky in my home folder. This is the only .conkyrc file i know of. 

Since compiling conky-colors.tar.gz i don't know whether conky is using another .conkyrc file that conky-colors.tar.gz has created or the file i created in my home folder.

---

### Post by houserparker on 2010-01-24
> **Saiko Berry said:**
> Open terminal and type locate conkyrc.
Go there, edit that.

This is what it returned:-

ben@ben-laptop:~$ locate conkyrc.
ben@ben-laptop:~$ locate conkyrc
ben@ben-laptop:~$ 

It didn't seem to do anything

---

### Post by Saiko Berry on 2010-01-24
open terminal type man conky-colors?
go to where you compiled conky-colors check the readme?

Can you do these things and return with results? Surely it says where it configures it somewhere..

I suspect ~/.config/conky

@ Above post: What? Shouldnt you have one in your home folder according to above posts? o.O

---

### Post by houserparker on 2010-01-24
> **Saiko Berry said:**
> open terminal type man conky-colors?
go to where you compiled conky-colors check the readme?

Can you do these things and return with results? Surely it says where it configures it somewhere..

I suspect ~/.config/conky

@ Above post: What? Shouldnt you have one in your home folder according to above posts? o.O

man conky-colors returned nothing

I found a hidden folder inside /home/ben called .conkycolors that im guessing was created when i compiled but i can't see a conkyrc file anywhere.

---

### Post by Saiko Berry on 2010-01-24
Well the script youre running to start the conky, can you go to that and paste the contents? Im confused, I neve used conky-colors because its generally simple out of the box imo.
What IS running the Conky? You should have a start script somewhere thats how Conky works.

---

### Post by houserparker on 2010-01-24
> **Saiko Berry said:**
> Well the script youre running to start the conky, can you go to that and paste the contents? Im confused, I neve used conky-colors because its generally simple out of the box imo.
What IS running the Conky? You should have a start script somewhere thats how Conky works.

Yep im confused to. I think the best way to solve this is to start from scratch. 

How do i go about getting rid of the conky colors compile and return the conky that i installed from the repos back to the way it was initially (when it worked)?

And can you recommend the best way of configuring conky successfully?

Thanks for your help

---

### Post by VCoolio on 2010-01-24
If you did "make install" like the conky-colors site on gnome-look.org says, go into that folder again in a terminal and try "make uninstall".  The config file isn't necessarily named conkyrc though, it can be anything; look into that ~/.conky-colors folder.

Best way to configure conky and learning is to look at the [manual]("http://conky.sourceforge.net/docs.html") for options; then at [other peoples conky's]("http://ubuntuforums.org/showthread.php?t=281865") for inspiration, and [here]("http://conky.linux-hardcore.com/") for howtos.

---

### Post by houserparker on 2010-01-24
> **VCoolio said:**
> If you did "make install" like the conky-colors site on gnome-look.org says, go into that folder again in a terminal and try "make uninstall".  The config file isn't necessarily named conkyrc though, it can be anything; look into that ~/.conky-colors folder.

Best way to configure conky and learning is to look at the [manual]("http://conky.sourceforge.net/docs.html") for options; then at [other peoples conky's]("http://ubuntuforums.org/showthread.php?t=281865") for inspiration, and [here]("http://conky.linux-hardcore.com/") for howtos.

Thankyou all for your help. It is very much appreciated.

---

