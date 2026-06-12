---
title: "acer one d250 wireless issues"
date: 2010-01-11
forum: General Help
---

### Post by selectum on 2010-01-11
May i get some help please with my mom's acer netbook. Thought it be great for her to have remix for simplicity, if only the wireless driver issue was so simple. 
I've done everything as i should on the acer d250 page. 
([https://help.ubuntu.com/community/AspireOneAOD250?action=show](https://help.ubuntu.com/community/AspireOneAOD250?action=show) redirect=AspireOne%2FAOD250)
I downloaded the wireless driver from Atheros , but I keep getting a 'no such file or directory', I have the correct driver and then typed in cd /home/user(moms name)/atheros and immediately get the no such file etc...i make sure every thing is exact to the instructions. Does it have to be in a file called /home/user(moms name)atheros? It must be pretty clear I'm new to this.
Other than this remix is awesome.

---

### Post by bkratz on 2010-01-11
> **selectum said:**
> May i get some help please with my mom's acer netbook. thought it be great for her to have remix for simplicity,if only the wireless driver issue was so simple. 
I've done everything as i should on the acer d250 page. 
([https://help.ubuntu.com/community/AspireOneAOD250?action=show](https://help.ubuntu.com/community/AspireOneAOD250?action=show) redirect=AspireOne%2FAOD250)
I downloaded the driver, but I keep getting a 'no such file or directory', I have the correct driver and then typed in cd /home/user(moms name)/atheros and immediately get the no such file etc...i make sure every thing is exact to the instructions. Does it have to be in a file called /home/user(moms name)atheros? It must be pretty clear I'm new to this.
Other than this remix is awesome.

I read the instructions (don't have one myself) but it says that you have to download to that directory. Where is your download file currently residing? Your are going to have to create that directory and put the file in it before proceeding the way I read it.

---

### Post by selectum on 2010-01-11
Hi thanks for the reply, Its in a download file.

---

### Post by selectum on 2010-01-11
umm.. Whats a directory? i not kidding, would that be a file called atheros?

---

### Post by bkratz on 2010-01-11
> **selectum said:**
> umm.. Whats a directory? i not kidding, would that be a file called atheros?

No Atheros would be a file within a dirctory. See this for a description of directories. Remember a directory can contain another directory which contains another directory which contains files.


[http://ubuntuforums.org/showthread.php?t=465842](http://ubuntuforums.org/showthread.php?t=465842)

---

### Post by selectum on 2010-01-11
Well I think i created a directory but when i gunzip it told me "ignored"

---

### Post by bkratz on 2010-01-11
I guess i am really confused I reread the thread and you say you are trying to install wireless---I don't see anything about wireless in the Aspire directions you pointed to.  Are you trying to work on wireless or wired?

---

### Post by selectum on 2010-01-11
Opps! sorry, trying to install a wireless driver. its a seems to be a standard issue with the acer one d250 and remix.

---

### Post by bkratz on 2010-01-11
> **selectum said:**
> Opps! sorry, trying to install a wireless driver. its a seems to be a standard issue with the acer one d250 and remix.

OK go to this thread and see post 8 specifically. If you substitute   karmic (and are using karmic) where it say jaunty you should be good to go.  At least you have a good long thread to see all the problems others have had.



[http://ubuntuforums.org/showthread.php?t=1141529&highlight=acer+d250](http://ubuntuforums.org/showthread.php?t=1141529&highlight=acer+d250)

---

### Post by selectum on 2010-01-11
The acer remix on my previous post, contents number 5, Getting the rest of the hardware to work right below install webcam there's.. Enabling wired network.

---

### Post by bkratz on 2010-01-11
> **selectum said:**
> That page, contents number 5, Getting the rest of the hardware to work right below install webcam there's.. Enabling wired network.

So once again--what are you trying to do? There is a difference between a wired connection and a wireless one. The page you keep referring to is for wired (that means it plugs in).

See post 8 of the one I pointed you to it is for wireless.

Again this is a link to the wireless repeatedly mentioned and just that post although I think you might want to read the whole thread previously linked to.

[http://ubuntuforums.org/showpost.php?p=7177298&postcount=8](http://ubuntuforums.org/showpost.php?p=7177298&postcount=8)

---

### Post by bkratz on 2010-01-11
If you go to the first link I sent to you (I just went though all 127 posts) it tells you how to wireless,wired and make sure that the microphone works.

---

### Post by selectum on 2010-01-11
Sorry i was flipping out. Its the wireless, everything works perfect but this issue with wireless as before mentioned on the acer d250 unbuntu remix page. I managed to extract the driver by transferring it to a vista machine and then back to the netbook, ( i was getting errors) so i have a extracted copy to work with. Just tried the broadcom driver it came with and ..nothing, it knows theirs a network but no connection, I was using wifi radar. Mic, mouse, track pad usb's working.

---

### Post by selectum on 2010-01-11
Any advice on installing a wireless driver now a src file.

---

