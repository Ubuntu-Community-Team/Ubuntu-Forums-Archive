---
title: "Stray sudo rm = BAD BUSINESS"
date: 2010-09-28
forum: General Help
---

### Post by alphaamanitin on 2010-09-28
Hey guys,  

Well, here is my first big Linux OH NO moment.  While using the rm command to delete some files in a dircetory /home/Programs/FigTree I thoughtlessly typed in sudo rm /lib/*.*  

Well, you can imagine the resaults.  Any thoughts on what all I have deleted?  Don't worry about this though, it is just something I mess around with I don't store any 100% necessary data on this computer.

Also, on another interesting note:  I run Ubuntu off of a external HD.  One day I moved and accidentally unplugged my drive.  To might great surprise I could continue browsing the website I was looking at and even hit F5 to refreash the page and that worked.  Of course when I tried existing firefox things went down the hill.

Please- hit me with your best shots on my incredably stupid sudo rm usage.

AlphaA

---

### Post by nothingspecial on 2010-09-28
I would say you`ve pretty much borked it. If apt or dpkg still work you may have a chance.

---

### Post by lrgmmc on 2010-09-28
wow. how long did you have to watch it delete your files and know it was killing important ones? thats horible. feel your pain. but like you said nothing to valuble lost. i did that in a shell script once and later that nite instead of my browsing history it got my whole home directory. luckly i back up my photos of my family.

---

### Post by rhoparkour on 2010-09-28
To be honest, looks like you will need a fresh install if apt is broken...

BTW: it helps to create an alias for all users (even for root, specially for root!) for rm so that it really means rm -i and it asks you if you are sure. That way I have never done something like this.

---

### Post by alphaamanitin on 2010-09-28
> **nothingspecial said:**
> I would say you`ve pretty much borked it. If apt or dpkg still work you may have a chance.

Nope I borked it.  Nothing is working.  The command prompt I had up is still functioning but other than that nothing seems to be opening.  Although when I plugged in a ether net cable it did disconnect me from wireless and give me the message.  I think I have deleted just about everything the computer needs to run.  Looks like some of the files I would like to keep are still there as I can cd to the directory.  Thing is I have lost the ls and dir commands.  I know I should be able to recover by rebuilding /lib/ with everything I need (at least I think I should be able to), but a reinstall seems a much simpler solution.

AlphaA

---

### Post by nothingspecial on 2010-09-28
> **alphaamanitin said:**
> Nope I borked it.  Nothing is working.  The command prompt I had up is still functioning but other than that nothing seems to be opening.  Although when I plugged in a ether net cable it did disconnect me from wireless and give me the message.  I think I have deleted just about everything the computer needs to run.  Looks like some of the files I would like to keep are still there as I can cd to the directory.  Thing is I have lost the ls and dir commands.  I know I should be able to recover by rebuilding /lib/ with everything I need (at least I think I should be able to), but a reinstall seems a much simpler solution.

AlphaA

If you can be bothered, have a look into chrooting from a live cd and using apt and dpkg from that to repair.

I do this sort of thing for fun sometimes just to see if I can

You`re right though, reinstall would be much quicker and easier.

---

### Post by alphaamanitin on 2010-09-28
Yeah that was my game plan if I have time to do it today.  Otherwise it will just be pushed off until I find time, or do just have to get it done and do a reinstall.  At least I should be able to save the files I want by booting into a liveCD and moving the files to the laptops internal HD.

AlphaA

---

