---
title: "CDs"
date: 2006-05-13
forum: General Help
---

### Post by Masterminds on 2006-05-13
I have tried to install a few things from CD but none of the CDs seem to boot and install the program.
is there a reason to this or is there some way of getting them to work???

---

### Post by louis_nichols on 2006-05-13
Well... What CD are you talking about? And what programs? And how did you try to install them?

---

### Post by Masterminds on 2006-05-13
well the main one i tired was a tiscali for the driver.
i got a driver downloaded off a website but that didnt help either 
i want to know if i can install it from a CD

---

### Post by louis_nichols on 2006-05-13
You can install a program from almost anything, if it's the right kind of install package. What did Tiscali give you? rpm,deb,bin package or something else? Can you read the CD at all?

---

### Post by Masterminds on 2006-05-13
well you can browse the CD and thats it.
in the CD it sayd things like Setup but if you click it nothing come up

---

### Post by louis_nichols on 2006-05-13
setup(.exe I presume) sounds like a windows application. You can not install under Linux drivers meant for windows.

If it's just setup and is indeed meant for Linux, then go to that folder in terminal and then type:

./setup

---

### Post by linbetwin on 2006-05-13
Maybe the CD contains drivers for Windows.
In that case, it won't work in Linux, setup or no setup.

---

### Post by Masterminds on 2006-05-13
well on the CD case it doesn't say if its windows, Mac or Linux so i though it would be compatible with all

---

### Post by linbetwin on 2006-05-13
[quote=Masterminds]well on the CD case it doesn't say if its windows, Mac or Linux so i though it would be compatible with all[/quote]

My guess is it's a Windows CD and Windows drivers don't work in Linux, or the other way round. There is 0.000001 % chance that you might find a "Linux" folder on that CD, but I doubt that. Try to search for linux drivers on the manufacturer's website.

Anyway, what kind of software is there on the CD? If I'm not mistaken, Tiscali is a UK ISP.

---

### Post by Masterminds on 2006-05-13
Yes In the UK 
I have tried the drivers on other web pages but didnt work

---

### Post by Masterminds on 2006-05-13
Yes In the UK 
I have tried the drivers on other web pages and openint them through terminal.
but when i type the command in it all loads and everything but the nothing happens it says somthing like opening from folder but then nothing

---

### Post by louis_nichols on 2006-05-13
I'm guessing, then, that what you've got on the cd aren't actually drivers, but rather connection settings. If so, yoy actually don't need any drivers. The cnnection settings can be done very easily ina GUI utility under System>Administration>Networking

Or does the cd contain drivers for your modem?

---

### Post by Masterminds on 2006-05-13
well it is drivers aswell because i connect through USB.
can you do that int the Networking area on Ubuntu??

---

### Post by louis_nichols on 2006-05-13
That's a complicated question to answer. It isn't Ubuntu's fault that companies don't offer even the most elementary support for it, but the open-source community is pretty resourceful and most of times solutions are found ("made" would be a better word).

Help for your question may be found [here.]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinmodemHelp")

---

