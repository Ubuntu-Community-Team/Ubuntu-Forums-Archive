---
title: "How to mount an ubuntu hard drive in OSX?"
date: 2011-02-19
forum: General Help
---

### Post by DnDer on 2011-02-19
I want to pull a few things off this external hard drive I have that is an ubuntu install from last year. However, my mac won't recognize the file system and mount it so I can pull the few files I need off of it.

What's the trick to getting a mac to find an ubuntu hard drive? 

My other option is removing my laptop hard drive, installing the ubuntu one, opening ubuntu manually, burning the information I need to a CD, or a usb key, and then removing the ubuntu hard drive, and reinstalling my mac osx drive to the laptop bay.

I'd prefer not to spend that much energy if I don't have to.

---

### Post by PaulReaver on 2011-02-20
how full is the hard drive.....  

you could resize the partition with a live cd
create a new mac osx friendly partition   (like fat32)
and copy the files from one to the other
boot up mac osx 
enjoy your rescued files

maybe??? it's just an idea

---

### Post by MrRichard on 2011-02-20
EDIT: The above idea just may work! (you beat me to the post) :)

---

### Post by DnDer on 2011-02-20
Nevermind. Sorry.

I found gparted on the 10.04 live disc I had laying around.

---

### Post by DnDer on 2011-02-20
Made the partition. Woo! When I try to copy everything over to that new partition, it tells me that I can't copy half my folders in it because I don't have permissions to.

What do I need to do to copy that folder over whole?

---

### Post by Jonher937 on 2011-02-20
i think you can do a "dd" in single user mode. Google it

---

### Post by PaulReaver on 2011-02-20
sorry for taking so long to respond....


gksu nautilus 
or
sudo nautilus

should do it I think.......

and when you copy them to the fat32 partition it 'should' remove the unix type file permissions as well... hopefully

---

### Post by DnDer on 2011-02-20
Worked like a charm. Thank you!

---

