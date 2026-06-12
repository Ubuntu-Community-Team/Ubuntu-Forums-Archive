---
title: "ndiswrapper help?"
date: 2006-06-19
forum: General Help
---

### Post by Dave-Ed on 2006-06-19
Can someone help me with setting up the driver for my wireless card.

I have used ndiswrapper to install the driver, but the problem is that it is not installed properly. I can't uninstall it because I'm told that it is not installed but if I try to install it again then it tells me it is already installed.

---

### Post by semperfiguy on 2006-06-19
type "ndiswrapper -l" into a terminal and then post the output here

---

### Post by Dave-Ed on 2006-06-19
Ok, I got this:

```
Installed ndis drivers:
aeiwlnic          invalid driver!
```

---

### Post by semperfiguy on 2006-06-19
try reinstalling ndiswrapper then installing the driver.. after that post the output again

---

### Post by Dave-Ed on 2006-06-19
Reinstalled, same thing happening.
Removed and then installed, same again.
Still the same invalid driver.

In the ndiswrapper folder in etc there is an empty folder with the aeiwinic driver name. Could this be causing the problem?

---

### Post by semperfiguy on 2006-06-19
That might be.. try deleting it. 

when I type ndiswrapper -l I get
Installed ndis drivers:
lsbcmnds                driver present, hardware present

and I have a folder by that name in /etc/ndiswrapper

so give it a shot and post what happens

---

### Post by msak007 on 2006-06-19
First of all, what kind of card is it and what driver did you use?

---

### Post by Dave-Ed on 2006-06-19
When I try it it says I don't have permission to delete it.

I apparently need root access, according to the properties of the folder.
How would I go about doing this? 
Or would using the terminal be better?

It is an Actiontec 802UIG-1 wireless card. I used the Actiontec 802UI3 drivers.

---

### Post by az on 2006-06-19
[QUOTE=Dave-Ed]Ok, I got this:

```
Installed ndis drivers:
aeiwlnic          invalid driver!
```[/QUOTE]


sudo ndiswrapper -e aeiwlnic

if that does not work, 

sudo rmdir /etc/ndiswrapper/aeiwlnic

But doesn't the actiontec work out-of-the-box?

---

### Post by Dave-Ed on 2006-06-20
Right I used the sudo rndir /etc/ndiswrapper/aeiwlnic, then used the sudo ndiswrapper -i ~/drivers/aeiwlnic/AEIWLNIC.inf

It returned this...

Installing aeiwlnic
couldn't copy /home/drivers/aeiwlnic/AEIWLNIC.inf at /usr/bin/mdiswrapper line 135.

It apparently isn't work out of the box, well not for me anyway.

Any ideas?

Edityness: Thanks for the help, very friendly forums here! But it was all caused by my stupidity, the needed all the files when I was giving it only a couple. Thanks anyway. 

But, it still isn't recognised in the Networking in the admin section. Oh well... Can all .exe be extracted using zip?

---

### Post by az on 2006-06-20
[QUOTE=Dave-Ed]Right I used the sudo rndir /etc/ndiswrapper/aeiwlnic, then used the sudo ndiswrapper -i ~/drivers/aeiwlnic/AEIWLNIC.inf

It returned this...

Installing aeiwlnic
couldn't copy /home/drivers/aeiwlnic/AEIWLNIC.inf at /usr/bin/mdiswrapper line 135.

It apparently isn't work out of the box, well not for me anyway.

Any ideas?[/QUOTE]
I mean work *without* ndiswrapper....

As for your ndiswrapper problems, are you using the ndiswrapper from ubuntu or did you compile it from source (which you don't have to do, 99 percent of the time and causes problems like this)  and are you sure that .inf file is the correct one?

---

### Post by Dave-Ed on 2006-06-21
I am using the one that came with Ubuntu. As for the correct .inf I got it from the [http://linux-wless.passys.nl/query_part.php?brandname=Actiontec]("http://linux-wless.passys.nl/query_part.php?brandname=Actiontec").

How would you install it without ndiswrapper?

---

