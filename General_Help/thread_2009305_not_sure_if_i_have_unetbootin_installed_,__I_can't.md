---
title: "not sure if i have unetbootin installed ,  I can't use it?"
date: 2012-06-24
forum: General Help
---

### Post by tbrownarcher on 2012-06-24
I accomplished these 3 commands.  I assume they installed unetbootin on my system.  How do i get it to create a bootable USB drive.  I have the Ubuntu 12.04 in several places on the computer ...
 the thumb drive....
 the Downloads directory ......
 cd rom

UNetbootin in ubuntu

Option1:For Ubuntu 9.10 and higher,just run following three commands in Applications->Accessories->Terminal to install UNetbootin from PPA:

[B]sudo add-apt-repository ppa:gezakovacs/ppa
sudo apt-get update
sudo apt-get install unetbootin[/B]



How do i use unetbootin to make a bootable USB drive?


Thanks,
Nate

---

### Post by sgage on 2012-06-24
> **tbrownarcher said:**
> UNetbootin in ubuntu

Option1:For Ubuntu 9.10 and higher,just run following three commands in Applications->Accessories->Terminal to install UNetbootin from PPA:

sudo add-apt-repository ppa:gezakovacs/ppa
sudo apt-get update
sudo apt-get install unetbootin

I accomplished these 3 commands.  I assume they installed unetbootin on my system.  How do i get it to create a bootable USB drive.  I have the Ubuntu 12.04 in several places on the computer ...
 the thumb drive....
 the Downloads directory ......
 cd rom

How do i use unetbootin to make a bootable USB drive?


Thanks,
Nate

First of all, unetbootin is right there in the Precise repos, so you didn't need to fiddle around with a ppa. In fact, I'd purge that ppa and reinstall unetbootin from the official repos.

Then, you need to launch unetbootin as root. From there it's pretty self-explanatory. You can select a distro and version and it will download it, or you can select an iso that you've already downloaded. Select a USB drive. Go. It's always worked fine for me.

---

### Post by tbrownarcher on 2012-06-24
"First of all, unetbootin is right there in the Precise repos, "

I don't know how to get anything from the repository could you help me with that ?

"Then, you need to launch unetbootin as root"


actually how to launch is my biggest problem.  

Thanks,
Nate

---

### Post by robtygart on 2012-06-24
> don't know how to get anything from the repository could you help me with that ?

Look for your software center, it looks like an orange paper bag. 

> actually how to launch is my biggest problem.

 To launch look in Applications>System or even type it in to the search&Launch

---

### Post by sgage on 2012-06-24
> **tbrownarcher said:**
> "First of all, unetbootin is right there in the Precise repos, "

I don't know how to get anything from the repository could you help me with that ?

"Then, you need to launch unetbootin as root"


actually how to launch is my biggest problem.  

Thanks,
Nate

Well, you can launch it from a terminal: gksu unetbootin

Or you can type Alt-F2 and launch it from there: gksu unetbootin

---

### Post by tbrownarcher on 2012-06-24
Well, you can launch it from a terminal: gksu unetbootin

Or you can type Alt-F2 and launch it from there: gksu unetbootin 

I opted for the Alt-F2 method I got it to run no problem thank you very much.

I cannot figure out how to put the file name in the interface.  I got the distribution in the field but it only goes up to 11.01 for a version and so I am trying to install 12.04 which is on a USB drive (thumb drive).  I do not know how to put the name of the iso into any field at all.  there is a field that seems to be asking where I want to go for the file but it only gives me 2 options ---computer &  Root.  It's on a usb drive in a usb slot or it is on a cd or it is in the downloads but i don't know how to tell it that.  And being on a limited data plan for the internet I cannot afford to go out on the internet to get it right now.


thanks,
Nate

---

### Post by raja.genupula on 2012-06-24
navigate as  **Click at Computer  ,then it will give you" \ "and select and choose media among the list . In the media you can find your USB .**

its better to paste the ISO somewhere in the PC .

---

### Post by sgage on 2012-06-24
> **tbrownarcher said:**
> Well, you can launch it from a terminal: gksu unetbootin

Or you can type Alt-F2 and launch it from there: gksu unetbootin 

I opted for the Alt-F2 method I got it to run no problem thank you very much.

I cannot figure out how to put the file name in the interface.  I got the distribution in the field but it only goes up to 11.01 for a version and so I am trying to install 12.04 which is on a USB drive (thumb drive).  I do not know how to put the name of the iso into any field at all.  there is a field that seems to be asking where I want to go for the file but it only gives me 2 options ---computer &  Root.  It's on a usb drive in a usb slot or it is on a cd or it is in the downloads but i don't know how to tell it that.  And being on a limited data plan for the internet I cannot afford to go out on the internet to get it right now.


thanks,
Nate

If you've already downloaded the iso, ignore the "Distribution" part, go down and click on the Diskimage button and navigate to your iso.

---

### Post by tbrownarcher on 2012-06-25
> **sgage said:**
> If you've already downloaded the iso, ignore the "Distribution" part, go down and click on the Diskimage button and navigate to your iso.


That did it thanks. If I should start a new thread tell me.  I am actually installing from the USB drive.  However it tells me the same thing it said before.  Which is   "the installer has encountered an unrecoverable error. A desktop session will be started so you can correct the problem."  So I have a deskyop session in front of me with no idea what to do with it and no instructions that I can find.Can someone help with that?

Thanks,
Nate

---

### Post by sgage on 2012-06-26
> **tbrownarcher said:**
> I am actually installing from the USB drive.

I'm not sure what's going on here. The idea is to install the iso file TO the USB drive, not FROM it.

You should have a distro iso image file on your hard drive somewhere and an empty USB key. Unetbootin will install the iso file onto the USB key such that it will be bootable.

---

