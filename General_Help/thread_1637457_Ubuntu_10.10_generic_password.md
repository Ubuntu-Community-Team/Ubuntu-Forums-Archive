---
title: "Ubuntu 10.10 generic password???"
date: 2010-12-04
forum: General Help
---

### Post by deckoff on 2010-12-04
OK
So I have this weird problem - I want to install 3d drivers for my video , which are disabled by default in 10.10. I test the system runnung from a USB flash, so to have the drivers enabled, I have to log out and log in again. When I the login screen appears, I am asked for a password, which I did not set!!! My question is:
 Does anyone know what the password is???
What about the 11.04 password??

---

### Post by RJ12 on 2010-12-04
The password is blank I believe and the username is ubuntu

If there is no one on the login screen click on "other" and type ubuntu as the username and nothing as the password, if it doesn't work try using ubuntu as the password too.

---

### Post by deckoff on 2010-12-04
Neither ubuntu nor blank are valid passwords!!! :(•••••••

---

### Post by canaillou on 2011-05-06
I have exact same issue,
I start the installation from a CD i burnt with the Ubuntu 11.04.  (same issue with 10.10)
I never told to create a login or timezone etc..
Installation starts and after a while a login prompt is displayed with
Unbutu  with a circle  and an available field with : other...
No way to get of rid of this.
when i ckicl on other...  a username need to be provided with a psw  however i never 
create one so hard to provide one.
i made searches on the web and i'm not alone, however hard to find a real solution
few says :
try user : ubuntu  with psw ubuntu   --> failed
try user : ubuntu  with psw (blank) -> failed
try oem with psw (blank) -> failed

when i rebbot the machine of course nothing is installed and i cannot access the GRUB as few say to go to.
I'm a newby in Linux  but really wish to be able to complete the installation
i would really appreciate any help
Thanks a lot

---

### Post by coffeecat on 2011-05-06
> **canaillou said:**
> I have exact same issue,
I start the installation from a CD i burnt with the Ubuntu 11.04.  (same issue with 10.10)
I never told to create a login or timezone etc..
Installation starts and after a while a login prompt is displayed 

I don't follow this. If you start the installer, you do not get a login prompt. I think what you mean is that you are trying to boot up the live CD and that you get the login prompt before it has finished booting. Booting up the live CD is not the same as starting the installer. The normal sequence is that as soon as the CD begins to boot, you are presented with a purple screen with two icons at the bottom. If you tap any key at this point, you are presented with an old-style text menu with various options. If you do not tap any key, booting contimues after a short delay and you are presented with a graphical choice: "Try Ubuntu" or "Install Ubuntu". if you choose "Install Ubuntu" the graphical installer starts. If you choose "Try Ubuntu" you are taken to the live desktop where you have access to the complete  system running live (i.e. not yet installed) with all the default applications. You can then start the installer from the live desktop.

Having said all that, if you are getting the login screen when you first boot up with a live CD, it means you have a faulty CD and the correct live username and password - "ubuntu" and blank - will not work.

Did you check the md5sum of the downloaded ISO before you burnt it to CD? See here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, if you tap any key  when the CD first starts to boot as described above, you can choose a disc integrity check from the menu. Worth doing if you are having problems.

**Or** - do you mean that you have finished installing Ubuntu to the hard drive and that you were not asked to create a username and password during the installation process? Sorry, not possible with the live desktop CD. That's only possible, I believe, by doing an OEM installation from the alternate CD.

---

### Post by canaillou on 2011-05-06
Hello Coffeecat. Thanks for your help on this

I did check my ISO with the cheksum utility  -->  Checksum is the same
no prob on this side.
Now how i proceed to be exact.
I boot from the CD then when the "try Ubutu" or "Install Ubuntu" screen is displayed
i choose "Install Ubuntu", then installation starts and after a while the Login screen requiring me to enter a Usernane and Password is displayed. 
But Neither the Create Login nore the specify Location sceens etc... are displayed.

Do you mean i should try to click on "Try uBuntu' then when system is up i should then 
click on 'Install Ubuntu' ?
 Canaillou

---

### Post by coffeecat on 2011-05-06
> **canaillou said:**
> 
i choose "Install Ubuntu", then installation starts and after a while the Login screen requiring me to enter a Usernane and Password is displayed.

Are you sure that's not the screen that asks you to create a username account and password? That is displayed only a minute or so after installation starts. I haven't got time to find a screenshot now as I must go out for a few hours, but you can tell the screen I'm referring to: it has a number of choices at the bottom for whether you want to autologin or not. It defaults to "ask for password" or words to that effect. If that's what you are seeing, that's not a login screen - that's where you create your account.

---

### Post by canaillou on 2011-05-06
Yes
i know the screen you are talking about .. i wish i could receive that screen because this would mean i'm in the normal path of the installation.
But the screen displayed  is only :
Ubuntu  (with the Big circle icon on the top.  Which i guess mean this is Ubuntu login default)
and the a field with :  others.....
if i click on Ubuntu then no effect..  
if i click on Others  then system asks me for a Username and a psw 
[IMG]file:///C:/WINDOWS/TEMP/moz-screenshot-11.png[/IMG][IMG]file:///C:/WINDOWS/TEMP/moz-screenshot-12.png[/IMG][IMG]file:///C:/WINDOWS/TEMP/moz-screenshot-13.png[/IMG]

---

### Post by coffeecat on 2011-05-06
> **canaillou said:**
> 
[IMG]file:///C:/WINDOWS/TEMP/moz-screenshot-11.png[/IMG][IMG]file:///C:/WINDOWS/TEMP/moz-screenshot-12.png[/IMG][IMG]file:///C:/WINDOWS/TEMP/moz-screenshot-13.png[/IMG]

Nope. Even my special magical spectacles can't make those out. :wink:

You need to attach your images as thumbnails. Use the "Manage Attachments" button below the message field, or the paperclip icon above it to upload the images to the forum.

---

### Post by canaillou on 2011-05-08
hello, forget the attachement, this was not done on purpose ...
my problem is still there and no way to install Ubuntu, i wanted to avoid coming back to Windows, thinking Ubuntu was much easier to install and maintain but now i start thinking windows was not that bad

---

### Post by canaillou on 2011-05-10
Hello.
Coffeecat, i'll continue to attempt installing Ubuntu, and if i succeed i'll let you know ... 
in the meantime thanks a lot for your help you provided to me i really appreciate people willing to help.
Bye for now

---

### Post by canaillou on 2011-05-12
Hello I finally got rid of the problem. the way i solved it is the following.
I burnt the ISO file to a fash drive  versus the CD . And installing from the flash drive (USB Key) worked just fine .. While installing from CD did never work.
Bottom line  it is much better and faster to install from the USB Key vs a CD.
Thanks

---

### Post by coffeecat on 2011-05-12
I'm glad you've solved it.

The problem could have been a speck of dust on the CD causing a misread of the files that constitute Ubiquity (the installer app). I get odd things happening with CDs occasionally and much prefer to use bootable USBs now which, as you say, are much faster.

Good luck! :)

---

### Post by kmjohnson02 on 2011-08-05
having the exact same problem. Like you, I looked everywhere and all I could find was try this and that password. Just like you, nothing worked. 

Off of the USB installation, did you go the try or install route?

Looking deeper into what else it could be. will post later.

---

### Post by kmjohnson02 on 2011-08-05
FIXED!!! I took away the partition set aside for ubuntu and added it again, reinstalled. good to go

---

