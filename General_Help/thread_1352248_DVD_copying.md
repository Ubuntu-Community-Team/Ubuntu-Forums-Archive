---
title: "DVD copying"
date: 2009-12-11
forum: General Help
---

### Post by Newklear on 2009-12-11
So im new to this ubuntu OS and i've got everything set up . When i tried to copy a dvd it copied the dvd but when i enter a blank dvd it says there's no dvd drive im breaking my head . Help thanks .

---

### Post by Mark Phelps on 2009-12-11
Don't know how you're "copying" the DVD but if it's a standard 9GB commercial DVD, you'll need a dual-layer writer and 9GB medium to make the copy.

If you used some app that claimed to be copying it, there's no telling what it really did.

Need more details about kind of DVD, and what app you're using to do the copying.

---

### Post by Newklear on 2009-12-14
Well im trying to copy a standard dvd 4.7 GB , do you recommend any apps to do so ?

---

### Post by NTHQ on 2009-12-14
Brasero works fine no? And it comes with Ubuntu.

---

### Post by Newklear on 2009-12-16
nope doesn't work . It says there's no disk when there is .

---

### Post by philinux on 2009-12-16
Does the blank disk get mounted on your desktop?

---

### Post by Newklear on 2009-12-16
Okay lets say I insert the dvd to watch it , it works great but if I insert a blank disk it doesn't get mounted . Also I dont understand if i can watch the dvd why can't I copy it ?

---

### Post by running_rabbit07 on 2009-12-16
Are you sure that your system writes DVDs?

---

### Post by Newklear on 2009-12-16
I have a DVD and CD  writer why wouldn't it ?

---

### Post by philinux on 2009-12-16
> **Newklear said:**
> Okay lets say I insert the dvd to watch it , it works great but if I insert a blank disk it doesn't get mounted . Also I dont understand if i can watch the dvd why can't I copy it ?

Open a terminal and post the output of this. Copy and paste into the the terminal.

```
sudo lshw | grep dvd
```

Maybe a bad blank disk?

---

### Post by Newklear on 2009-12-16
> **philinux said:**
> Open a terminal and post the output of this. Copy and paste into the the terminal.

```
sudo lshw | grep dvd
```Maybe a bad blank disk?
logical name: /dev/dvd1
                capabilities: removable audio dvd


and its not the disk i've tried a bunch .

---

### Post by running_rabbit07 on 2009-12-16
I was asking because it sounds like your system doesn't have DVD~R.

What method are you using to copy the DVD to your system?

---

### Post by running_rabbit07 on 2009-12-16
> **Newklear said:**
> logical name: /dev/dvd1
                capabilities: removable audio dvd


and its not the disk i've tried a bunch .

If it was writable, this is what it would look like. ```
rabbit@rabbit-desktop:~$ sudo lshw | grep dvd
[sudo] password for rabbit: 
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram

```

---

### Post by Newklear on 2009-12-16
Yes , it does . And I tried using Brasero and other DVD copying/ripping programs .

---

### Post by running_rabbit07 on 2009-12-16
My only other thoughts are that if you do have DVD~R, the CD drive isn't supported. What brand is it?

---

### Post by Newklear on 2009-12-16
I guess it was my dvd drive i went out and got a usb dvd writer and it works .

---

### Post by running_rabbit07 on 2009-12-16
Cool.

---

### Post by ean5533 on 2009-12-16
> **Newklear said:**
> I guess it was my dvd drive i went out and got a usb dvd writer and it works .

It's likely that the drive you were using wasn't a DVD writing drive. Does it say DVD+R on the front of the drive?

Glad the new USB drive you got works :)

---

