---
title: "How to open .bin files?"
date: 2009-10-04
forum: General Help
---

### Post by ErikEhlert on 2009-10-04
The title pretty much explains it, any game I download for linux that isn't in the repositories is usually in .bin format. I heard its supposed to be done in terminal, which I don't know how to access either. What exactly do I do?

---

### Post by nbtrap on 2009-10-04
Right-click >> Properties >> Permissions

Check the box labeled "Allow executing file as program". Close the Permissions dialogue, then double-click the file.

---

### Post by credobyte on 2009-10-04
```
sudo chmod +x unknown.bin
./unknown.bin

```

---

### Post by ErikEhlert on 2009-10-04
Yeah, I have done with nbtrap says, but still it asks me what program to open it with.

I clicked the permissions tab and checked the box that says "is executable".

---

### Post by ErikEhlert on 2009-10-04
> **credobyte said:**
> ```
sudo chmod +x unknown.bin
./unknown.bin

```

Now where exactly do I input this?

---

### Post by credobyte on 2009-10-04
> **ErikEhlert said:**
> Now where exactly do I input this?

Applications / Accessories / Terminal - be sure to be in the right directory when executing these commands ( eg., use cd /home/user/Downloads to go to Downloads folder in your home directory ).

---

### Post by ibutho on 2009-10-04
Applications -> Accessories -> Terminal.

Replace unknown.bin with the actual filename.

---

### Post by ErikEhlert on 2009-10-04
Eh, I can go to Applications, but theres no accessories, I tried looking in System and Utilities, and I still could not find it.

---

### Post by wojox on 2009-10-04
Look through your menu for konsole

---

### Post by credobyte on 2009-10-04
> **ErikEhlert said:**
> Eh, I can go to Applications, but theres no accessories, I tried looking in System and Utilities, and I still could not find it.

Press [COLOR=Gray]*Alt+F2*[/COLOR] and enter* [COLOR=Gray]konsole[/COLOR]* ( not sure if it works on KDE :D ).

---

### Post by ErikEhlert on 2009-10-04
> **credobyte said:**
> Press [COLOR=Gray]*Alt+F2*[/COLOR] and enter *[COLOR=Gray]terminal[/COLOR]* ;)

Found it :D

Hm, I thought I tried Alt+F2 to look for it before..

anyways... I guess I will try that code now..

 Edit: Egh. Okay, well, my user folders name is erik. So I tried:

```
 erik@LinuxK:~$ cd/home/erik/Download
bash: cd/home/erik/Download: No such file or directory 
```

If I try just entering cd /home it will find my home directory.

```
 erik@LinuxK:~$ cd /home
erik@LinuxK:/home$ 
```

after that I can't access the erik folder or download.

Could I move the .bin file to my home directory and open it there?

---

### Post by ibutho on 2009-10-04
Are you using Kubuntu? If so do ALT-F2 and enter the command "konsole" (minus the double quotes).

Edit We are all too eager to help eh. ;)

---

### Post by ErikEhlert on 2009-10-04
Yes yes, I already got to Konsole. What I need help with is what exactly I have to type in Konsole.

Edit: Okay, well I am trying 2 different games, I moved both the .bin files into my home directory.

One is PlaneShift, the filename is "PlaneShift-v0.4.03-x86.bin"

The other is Savage2: "Savage2Install-2.1.0.1-i686.bin"

---

### Post by credobyte on 2009-10-04
> **ErikEhlert said:**
> Found it :D

Hm, I thought I tried Alt+F2 to look for it before..

anyways... I guess I will try that code now..

 Edit: Egh. Okay, well, my user folders name is erik. So I tried:

```
 erik@LinuxK:~$ cd/home/erik/Download
bash: cd/home/erik/Download: No such file or directory 
```If I try just entering cd /home it will find my home directory.

```
 erik@LinuxK:~$ cd /home
erik@LinuxK:/home$ 
```after that I can't access the erik folder or download.

Could I move the .bin file to my home directory and open it there?

If your username is erik, your home directory is /home/erik, not /home. Download folder was just an example.
Execute the following commands to get the basics of what I'm talking about :)

```
cd /home/erik
ls
cd Desktop
ls
```All you need to do is to find out in which folder you saved your .bin file and use it's path when executing cd command.

As a temporary solution, move your .bin file to desktop and execute the following commands:
```
cd $HOME/Desktop
sudo chmod +x unknown.bin
./unknown.bin
```
** Replace unknown with the name of your .bin file.

---

### Post by ErikEhlert on 2009-10-04
> **credobyte said:**
> If your username is erik, your home directory is /home/erik, not /home. 

Oh my g- ... I always make stupid mistakes like that!
I feel like the EFG of Ubuntu Forums :P

Edit:
```

erik@LinuxK:~$ cd /home/erik
erik@LinuxK:~$ ls
[COLOR=Blue]Desktop    Pictures     [/COLOR]               [COLOR=Lime]Savage2Install-2.1.0.1-i686.bin[/COLOR]
[COLOR=Blue]Documents [/COLOR] [COLOR=Blue][COLOR=Lime]PlaneShift-v0.4.03-x86.bin [/COLOR] Templates
Download   Public                      Videos
Music      Rush Discography[/COLOR]

 
```Progress!

```
 sudo chmod +x Savage2Install-2.1.0.1-i686.bin
 ./Savage2Install-2.1.0.1-i686.bin
 
```After that the installer appeared!
Oh joy!

Well, I learned something today, every day is a new adventure with Linux :B

Edit Edit:
```

erik@LinuxK:~$ cd /home/erik/Savage2
erik@LinuxK:~/Savage2$ sudo chmod +x savage2.bin
erik@LinuxK:~/Savage2$  ./savage2.bin
warning: The VAD has been replaced by a hack pending a complete rewrite
Savage2 - Fatal Error: OpenGL 2.0 not available.
Segmentation fault (core dumped)
erik@LinuxK:~/Savage2$

```What an anti-climactic ending to that :|

I need to DL OpenGL?

---

### Post by credobyte on 2009-10-04
> **ErikEhlert said:**
> Oh my g- ... I always make stupid mistakes like that!
I feel like the EFG of Ubuntu Forums :P

No one has born as a genius ;)

---

### Post by Vaphell on 2009-10-04
what's your gfx adapter? internet says that intel chipsets won't work with ogl2

---

### Post by Khushboo_khan on 2009-10-08
there is no Allow executing file as program check box?
what to do?

---

