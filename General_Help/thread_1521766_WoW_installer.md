---
title: "WoW installer"
date: 2010-07-01
forum: General Help
---

### Post by Blue Summer on 2010-07-01
I've got the original WoW and the burning crusade add on, and i've started a free trial of Wrath Of The Lich King, I downloaded the installer and when I select WOTLK and click OK the installer just freezes and sits there till I terminate Wine. I've done all the correct port forwarding within my router and firestarter and cannot figure out why it is hanging, any help would be great! Thanks.

---

### Post by Blue Summer on 2010-07-01
I forgot to mention i'm using the latest Ubuntu and I was using the latest Wine but i've downgraded to 1.2.6 or something

---

### Post by xxxLinuxxx on 2010-07-01
Does this tread help at all?

 :KS [http://ubuntuforums.org/showthread.php?t=980629](http://ubuntuforums.org/showthread.php?t=980629) :KS

---

### Post by Blue Summer on 2010-07-01
not really sorry, i've downloaded the installer off the website

---

### Post by Blue Summer on 2010-07-01
> **Blue Summer said:**
> not really sorry, i've downloaded the installer off the website

I also did that chown the folder or something, ended up deleting all my wine and getting the new beta one and wine won't even load up anymore I don't know what's going wrong =(

Basically i think i've changed the folder to only be run by root, its saying the folders locked for wine, whats the command to get it back to normal?

i've figured out how to unlock the files: chown rej3kt /home/rej3kt/.wine but I can't figure out how to do the entire folder

edit i've done it ^_^ chown -R /home/rej3kt/.wine

and time for a 5th edit! It's working since I just installed the newest wine :)


Right so that's my problem with wine sorted and i'm now running 1.2 -RC5 and the Blizzard installer is still hanging/freezing/crashing so any help would be valued thanks =)

I do now have a problem with it sitting at: Preparing to install, it's not frozen due to the music playing and the ability to read the story and progress it through the buttons but it's not advancing from preparing to install

---

