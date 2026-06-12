---
title: "Help with a school Project."
date: 2009-11-29
forum: General Help
---

### Post by jerrad4220 on 2009-11-29
Hi there Im Jerrad, I am very new to the linux world. I am currently in a linux class for my degree, and i really need help with my final project. I am not very good at linux yet so be very descriptive if you decide to help me out, Any help is really appreciated. I have already searched the forums but am coming up with very little usefull info for my specific circumctance. Basicall what i am trying to do is make a custom live ubuntu cd that has been stripped down, and then i need to make this live cd load up with a ready made Gameserver for a game called tremelous. I also need to put the generic video drivers for various other machines, so that whom ever has my live cd could boot from the cd and have tremelous and the dedicated server ready to go. 
 
SO..
1. strip down ubuntu 9.04
2. get generic video drivers for various cards
3. make a dedicated game server
4. make the cd redistributable (in this case i just need one live cd to take to class)
 
Is this a difficult task, my teacher says he could do it in about an hour.
 
A little back ground info, I already have ubuntu 9.04 installed and running in sun virtual box. I have a copy of the game tremelous (open source) and i have an ISO of ubuntu 9.04.
 
Where do i start.

---

### Post by Defiant Rat on 2009-11-29
Im new to ubuntu too, but this might help

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Personally, i haven't tried it so wouldn't know if it works or not. I think i found the page from a link in someone's signature on here, so hopefully it'll be helpful. I do know that the people on here are really helpful, so im sure someone a lot more knowledgeable than me will be along in a second.

Good luck with it :)

---

### Post by jerrad4220 on 2009-11-29
cool, i saw that earlier, It looked like that was just showing how to compact the customized cd once you take all the crud off. I am definatly going to use that guide to finish up. Thanks !

---

### Post by jerrad4220 on 2009-11-29
Really no one else can help !!??

---

### Post by NoaHall on 2009-11-29
Simple. There's already a generic driver included, so you don't need to worry about that.

Then just add your softwware with remastersys.

---

### Post by jerrad4220 on 2009-11-29
apt-get install remastersys gives a dependancy error. I have already apt-get install update, it says im missing some software call miksofs, i tried to get that and it says its already installed. Catch 22

---

### Post by audiomick on 2009-11-29
hallo. I'm another non-expert, part I have seen a couple of posts that seem to have been similar to your catch 22. 
Try de-installing the package first, then re-installing.

---

### Post by davec64 on 2009-11-29
Here's one to try, Linux From Scratch (LFS):

[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

Using this enables you to create your own Linux distro rather than remastering another. From what I can gather (I've not tried it myself) it's pretty in depth with decent tutorials.

Have a look and see what you think!  :)

---

### Post by k3nz13 on 2009-11-29
There shouldn't be any need for a graphical environment to begin with if you're using the contents of the disk for nothing more than hosting a game server. If you use a textual interface it will reduce load on the server as well.

---

### Post by jerrad4220 on 2009-11-29
Heh, i need the GUI. I stink at the text part...

---

