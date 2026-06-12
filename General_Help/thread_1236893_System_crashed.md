---
title: "System crashed"
date: 2009-08-10
forum: General Help
---

### Post by Detrol on 2009-08-10
Hello, so this is the case. My system crashed when we had an electrical blackout where i live. When i try to start ubuntu again all i get is this Grub prompt, what do i have to do to get ubuntu working again?

---

### Post by lildigiman on 2009-08-10
You probably had some damage done when during the power failure. I mean damage as in, lost some data while the machine was still running.

First step would be to take a LiveCD, and make sure your ubuntu partition looks kosher in terms of having all of its files and whatnot. I'm sure others here will elaborate much more once we know what the problem really is.

---

### Post by wojox on 2009-08-10
Enter this:

grub> 
```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)
```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)
Next enter the command to install grub to the mbr

```
setup (hd0)
```
Finally exit the grub shell
```
quit
```

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

---

### Post by Detrol on 2009-08-10
Hmm, well i currently dont have a CD nor a working writer, so will have to get that if i really need it first.
About the last post, i wrote just as in your first citation and i got File not found.
Which i suppose is not a good thing. Any other suggestions? or will i need to get a CD? Would be a very sad loss if i lost the data on the partion since i have important SQL tables lying there.

---

### Post by Yvan300 on 2009-08-10
We won't no for sure until you are able to check your partitions, but i highly doubt that all your data is corrupted.

---

### Post by lildigiman on 2009-08-10
Hopefully most of the data will be ok, It could be as simple as one important system file getting corrupted while it was running and then immediately shut off.

I would suggest getting a friend to burn a LiveCD for you, just so you can *at least* save your files if you must.

---

### Post by Detrol on 2009-08-11
Alright, thanks, i will try to get a CD asap.
How will i check the partion though once i have the CD?, also while at it, i suppose this is nothing i can do with a downloaded edition with wubi.exe and all that? since im running it as a sister OS, got win2003 on the first partion and ubuntu on the other.

---

### Post by Barafu Albino Cheetah on 2009-08-11
If you have frequent blackouts and no means of backup, you should keep important data on ext3 filesystem with data=journal option provided. it prevents damages to files as much as possible. Additionally, you may look for apps like dvdisaster, they make an image of file with size only 10% of original. After that they can repair damage of any 10% of the file.

---

### Post by Detrol on 2009-08-14
Its actually the first blackout ive ever had, so there is nothing i have to worry about really, just my bad luck :). Thanks though!
Anyhow, i got myself an ubuntu CD now, how will i use it to check for problems with my current installation?

---

### Post by Detrol on 2009-08-14
Alright im having some serious problems now it seems, and i really need all the help i can get.

I tried the steps above, just trying the "root (hd?,?)" until i found that 0,1 and 0,0 works, and my best guess was that its installed on 0,1. So i did the root command for it, then i did setup (hd0).
But then im getting these errors:

Checking if "/boot/grub/stage1" exists... no"
Checking if "/grub/stage1" exists... no

Error 15: File not found.


Now i feel really stuck, anyone have any ideas? 
Thanks!

---

### Post by Detrol on 2009-08-14
Bump

---

### Post by Yvan300 on 2009-08-14
Ok, since you are able to boot to the live cd, try and save your files before going any further, i think the problem of grub not existing is some kind of system corruption of some sort, not sure if i remember right though.

---

### Post by Detrol on 2009-08-17
Sorry for the long time, been away this weekend.
Well i can boot from it, though im unable to see any of the files from the old installation, as far as i can see atleast.
I can see that the old ubuntu installation was installed in a seperate folder on the D:/ drive called Ubuntu, and the only thing i can see in there from the live CD is the swapfile.
Any suggestions?

Thanks in advance!

---

### Post by Yvan300 on 2009-08-17
Yup, i'm out of ideas, fiddle with it a bit more and see what is the outcome, sorry if i was no helpful :P

---

