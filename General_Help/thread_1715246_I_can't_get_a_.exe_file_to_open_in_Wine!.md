---
title: "I can't get a .exe file to open in Wine!"
date: 2011-03-26
forum: General Help
---

### Post by linuxuser12345 on 2011-03-26
Hey, I have bought the game Rollercoaster Tycoon 2 from Trymedia.com and Gamestop.com, and whenever I download the .exe file, I can never open it. I tried the .exe file in Windows and it is a program set to download the actual Rollercoaster Tycoon 2 game.

Can someone PLEASE help me with this? I have tried it alone with Wine *AND* with PlayonLinux.

---

### Post by TeoBigusGeekus on 2011-03-26
Try from command line
```
wine /path/file.exe
```
and see what error messages you get.

---

### Post by linuxuser12345 on 2011-03-26
How do I do that? Do I just copy and paste exactly what you gave me, or what?

---

### Post by vivek.pandey on 2011-03-26
when you try to open what error message do you get?

---

### Post by mrhhug on 2011-03-26
> **linuxuser12345 said:**
> Hey, I have bought the game Rollercoaster Tycoon 2 from Trymedia.com and Gamestop.com, and whenever I download the .exe file, I can never open it. I tried the .exe file in Windows and it is a program set to download the actual Rollercoaster Tycoon 2 game.

Can someone PLEASE help me with this? I have tried it alone with Wine *AND* with PlayonLinux.

since wine 1.1.4 wineHQ has it assigned a platinum
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3766](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3766)

so it should be seamless, cept that you bought the digital license without the physical disk.

when you run it from command line like TeoBigusGeekus suggest what errors do you get?

---

### Post by linuxuser12345 on 2011-03-26
I don't get any error message. It simply ties to load for 10 seconds, and does nothing afterwards. And, I am not using the Retail 1.0 version, I am using the Triple Thrill pack, which has a platinum rating

---

### Post by vivek.pandey on 2011-03-26
> **linuxuser12345 said:**
> I don't get any error message. It simply ties to load for 10 seconds, and does nothing afterwards. And, 
strange....however have you marked the file as executable and checked the permissions?

---

### Post by linuxuser12345 on 2011-03-26
Yup. The .exe file is a program that downloads the game

---

### Post by vivek.pandey on 2011-03-26
> **linuxuser12345 said:**
> Yup. The .exe file is a program that downloads the game

no.. what i meant is right click on the .exe file . go to permissions and see whether the checkbox there which reads as execute is checked or not... if not then check it or select it whatever  you call that

---

### Post by linuxuser12345 on 2011-03-26
Yes, I already told you! lol 
sorry for the confusion

---

### Post by TeoBigusGeekus on 2011-03-26
No executable permissions needed for exe files with wine.
What is the location of the exe file?

---

### Post by linuxuser12345 on 2011-03-26
My downloads folder

---

### Post by TeoBigusGeekus on 2011-03-26
Go to Applications>Accessories>Terminal
Give
```
wine ~/Downloads/nameoffile.exe
```
Replace nameoffile with the name of the file (dah) and post us the output.

---

### Post by linuxuser12345 on 2011-03-26
This is what I got when I typed it in:

jeb@Kitchen-PC:~$ wine ~/Downloads/RCT2TripleThrillSetup-dm.exe
jeb@Kitchen-PC:~$

---

### Post by jwbrase on 2011-03-26
> **TeoBigusGeekus said:**
> No executable permissions needed for exe files with wine.
What is the location of the exe file?

Yes and no. An .exe will run in Wine without executable permissions set, but it won't necessarily run the same. (I have a game that runs with much better framerates if the execute bit is set).

---

### Post by TeoBigusGeekus on 2011-03-26
> Yes and no. An .exe will run in Wine without executable permissions set, but it won't necessarily run the same. (I have a game that runs with much better framerates if the execute bit is set).

Good to know that, thanks.

> This is what I got when I typed it in:

 jeb@Kitchen-PC:~$ wine ~/Downloads/RCT2TripleThrillSetup-dm.exe
 jeb@Kitchen-PC:~$

That's really strange; no error message at all...
The things I'd try:
1)Re download the exe file and try again.
2)Reinstall wine
```
sudo apt-get install --reinstall wine
```
3)Reconfigure wine
```
sudo dpkg-reconfigure wine
```

---

### Post by vivek.pandey on 2011-03-26
I guess the problem is with the .exe file OP is trying to install

---

### Post by TeoBigusGeekus on 2011-03-26
> **vivek.pandey said:**
> I guess the problem is with the .exe file OP is trying to install

Possibly, but I'd expect an error message or something.

---

### Post by Morbius1 on 2011-03-26
It may not be that it is an exe. It may be that it is that exe:
[https://answers.launchpad.net/ubuntu/+source/wine/+question/149228](https://answers.launchpad.net/ubuntu/+source/wine/+question/149228)
>                      [Christian Dannie Storgaard]("https://launchpad.net/%7Ecybolic")          said     on 2011-03-15:   
    No, they seemed to be on Windows, but facing the same "nothing happens" problem. The problem might simply be with the program.

     
                                                

---

### Post by TeoBigusGeekus on 2011-03-26
> **Morbius1 said:**
> It may not be that it is an exe. It may be that it is that exe:
[https://answers.launchpad.net/ubuntu/+source/wine/+question/149228](https://answers.launchpad.net/ubuntu/+source/wine/+question/149228)

Good find!!!

---

### Post by linuxuser12345 on 2011-03-26
Lol, that was me! haha
So, all I do is go to a terminal and type the following to reconfigure Wine, am I correct?
sudo dpkg-reconfigure wine

---

### Post by TeoBigusGeekus on 2011-03-26
Yeap.

---

### Post by linuxuser12345 on 2011-03-26
Okay, I tried that, and nothing worked. :(

---

### Post by TeoBigusGeekus on 2011-03-26
I'm sorry to hear that mate...
Anyone else?

---

### Post by vivek.pandey on 2011-03-26
i will still say make sure everything id fine with your .exe file.
also i have heard about something called windows installer package (its not wine )which works togather with wine ti install windows essential . you can try that. windows installer isnt found in sc so you need to download then install it and try to work... see i have just heard about it never used it .

---

### Post by linuxuser12345 on 2011-03-26
> **vivek.pandey said:**
> i will still say make sure everything id fine with your .exe file.
also i have heard about something called windows installer package (its not wine )which works togather with wine ti install windows essential . you can try that. windows installer isnt found in sc so you need to download then install it and try to work... see i have just heard about it never used it .

Where can I find that?

---

### Post by vivek.pandey on 2011-03-26
ok i guess its better known as microsoft installer. you can google it .one link is [http://www.fileguru.com/apps/exe_installer_for_ubuntu](http://www.fileguru.com/apps/exe_installer_for_ubuntu) 
read about it and then go for its installation

---

### Post by mrhhug on 2011-03-27
does that .exe have any dependencies? like do you need ie8 installed since it is a downloader? 

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

im suprised it gives no errors. can you post the .exe for me? how large is this file, you said it was just a downloader right, so i guessing its not that big.

---

### Post by linuxuser12345 on 2011-03-27
> **mrhhug said:**
> does that .exe have any dependencies? like do you need ie8 installed since it is a downloader? 

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

im suprised it gives no errors. can you post the .exe for me? how large is this file, you said it was just a downloader right, so i guessing its not that big.
I don't think so. It doesn't open up in Internet Explorer

---

### Post by mrhhug on 2011-03-27
> **linuxuser12345 said:**
> I don't think so. It doesn't open up in Internet Explorer

right but does it need .net or ffdshow libraries or steam? you could use winetricks to install pretty much anything needed. but we need to figure out what this program uses to download the game. how big is the exe? can you post it?

---

