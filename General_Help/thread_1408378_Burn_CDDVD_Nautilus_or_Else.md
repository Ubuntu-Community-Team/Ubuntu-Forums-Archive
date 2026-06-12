---
title: "Burn CD/DVD: Nautilus or Else?"
date: 2010-02-16
forum: General Help
---

### Post by Gias Kay on 2010-02-16
Hello all,

I am interested to know if it is recommended to install some specific applications for the burning task, or if the default burning option in Nautilus would just be safe enough. By safe enough I mean get the job done for every burning with either CDs or DVDs, because I had some rather bad experience with open source authoring applications before. Thanks for the help in advance.

---

### Post by ratcheer on 2010-02-16
I have been using Nautilus / CD DVD Creator with decent results. But, I too would like to have something more full-featured like Nero on Windows. Nero allows you to have full control of burning speed, what type of disc you are burning, and does post-burning verification.

I suppose there are Linux apps available with these features, I just don't know what they are. Maybe someone will tell us.

Tim

---

### Post by 2hot6ft2 on 2010-02-16
I prefer brasero myself and have better luck with it.
```
sudo apt-get install brasero
```
There is a nero for linux just FYI, or k3b.

---

### Post by ratcheer on 2010-02-16
Do you have to install KDE to use k3b?

Also, Brasero seems to be part of the standard installation. At any rate, I have it but did not explicitly install it. I will try it the next time I burn a disk.

Tim

---

### Post by Gias Kay on 2010-02-16
Just checked out Brasero and I have to say the GUI is not very friendly. I guess I'll check out K3b.

---

### Post by drpjkurian on 2010-02-16
> **ratcheer said:**
> Do you have to install KDE to use k3b?

Tim

Hi
I have been using Ubuntu for the past 3 years, I have so far used two programmes namely Brasero and K3B.
I never got any glitches in K3b.
No need to install KDE Desktop to install K3B

---

### Post by drpjkurian on 2010-02-16
> **ratcheer said:**
> Do you have to install KDE to use k3b?


Tim
Hi
No need to install KDE to use K3B

---

### Post by 2hot6ft2 on 2010-02-16
> **drpjkurian said:**
> Hi
No need to install KDE to use K3B
What he said, what he said...
```
sudo apt-get install k3b
```
Nero for linux is not free by the way.

---

### Post by Lord Stig on 2010-02-16
The only burner I use is K3B after encountering tonnes of problems with Gnomebaker on my system (I imagine Gnomebaker is the closest Gnome equivalent). Problems like clicking on a file that would cause it to quit the program without warning! (this was true for me about a year ago).

K3B has lots of features and has been totally reliable for me (and I don't use KDE either).

---

### Post by 2hot6ft2 on 2010-02-16
> **Lord Stig said:**
> The only burner I use is K3B after encountering tonnes of problems with Gnomebaker on my system (I imagine Gnomebaker is the closest Gnome equivalent). Problems like clicking on a file that would cause it to quit the program without warning! (this was true for me about a year ago).

K3B has lots of features and has been totally reliable for me (and I don't use KDE either).
I had issues with gnomebaker too so I didn't mention it for that very reason.

---

### Post by Steel-Bunz on 2010-02-16
I believe k3b uses the same libraries (wodim?) in the background as Brasero. I had no trouble burning CDs with Brasero, but, going through hell in buring DVDs :(
 
Here is my thread, [http://ubuntuforums.org/showthread.php?t=1407915](http://ubuntuforums.org/showthread.php?t=1407915)
 
I am looking for something that doesn't use wodim/mkisofs libraries; going to try out Xfburn. Do we have any other options for CD/DVD burning in Linux?

---

### Post by philinux on 2010-02-16
K3b has had some love recently. It's been almost flawless for me.

It would not do a verify but it does now.

---

### Post by Gias Kay on 2010-02-17
Seems like K3b is not flawless after all. I burned 3 DVDs with it yesternight and everytime, it freezed after the burning and before the verification process. Force quit and the program won't be back. Had to reboot to burn another DVD. I searched a bit and this appears to be a long-standing bug with no solution. Any ideas?

---

### Post by Steel-Bunz on 2010-02-17
Gias,
 
Can you tell us which version of k3b and Ubuntu you are using? Do you have error logs?

---

