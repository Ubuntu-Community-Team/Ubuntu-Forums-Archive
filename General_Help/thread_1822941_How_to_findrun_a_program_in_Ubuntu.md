---
title: "How to find/run a program in Ubuntu ?"
date: 2011-08-11
forum: General Help
---

### Post by Amoranemix on 2011-08-11
(I am a Linux newbie)
 
 I am trying to make a bootable backup image of a 300GB HD (of which 36GB is used with a Win XP OS) onto a 60GB HD and am trying Linux for the sake of learning.
 
 I read about the program Partimage that should be able to do the trick. I downloaded it but I couldn't install it. Then I read about the Ubuntu Software center (UBC). I used it and it pretended to install an older version of Partimage. Partimage appears in History of UBC, but not in Installed Programs. UBC has a help page called 'Using a program once it's installed', which I read.
 
 Now I would like to use that program. How can I do that ? I don't know where it is installed and the search engine only finds the files I downloaded.
 
 Last minute change. When about to post I tried the forum button to look whether the subject is already posted. In a thread michy99 recommends the command which.
 Which partimage returns
 /usr/sbin/partimage
 which is an executable file, but I still have a few questions :

 - Why didn't the graphic search function find it ?
 - Why doesn't it appear in the applications menu ?
 - Why doesn't it appear in the Installed Software list of UBC ?
 - I can start Partimage from the terminal, but how can I start it using the GUI ?

---

### Post by haqking on 2011-08-11
> **Amoranemix said:**
> (I am a Linux newbie)
 
 I am trying to make a bootable backup image of a 300GB HD (of which 36GB is used with a Win XP OS) onto a 60GB HD and am trying Linux for the sake of learning.
 
 I read about the program Partimage that should be able to do the trick. I downloaded it but I couldn't install it. Then I read about the Ubuntu Software center (UBC). I used it and it pretended to install an older version of Partimage. Partimage appears in History of UBC, but not in Installed Programs. UBC has a help page called 'Using a program once it's installed', which I read.
 
 Now I would like to use that program. How can I do that ? I don't know where it is installed and the search engine only finds the files I downloaded.
 
 Last minute change. When about to post I tried the forum button to look whether the subject is already posted. In a thread michy99 recommends the command which.
 Which partimage returns
 /usr/sbin/partimage
 which is an executable file, but I still have a few questions :

 - Why didn't the graphic search function find it ?
 - Why doesn't it appear in the applications menu ?
 - Why doesn't it appear in the Installed Software list of UBC ?
 - I can start Partimage from the terminal, but how can I start it using the GUI ?

Create a new launcher for the app and point it to the app in /usr/sbin/partimage

Edit: Looking at the partimage site it doesnt have a GUI associaetd with it ? It is a text based Gui see here [http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

---

### Post by raja.genupula on 2011-08-11
Why doesn't it appear in the applications menu ?---> some application dont have icon , so they didnt

---

### Post by mcduck on 2011-08-11
> **Amoranemix said:**
> 
 - Why didn't the graphic search function find it ?
 - Why doesn't it appear in the applications menu ?
 - Why doesn't it appear in the Installed Software list of UBC ?
 - I can start Partimage from the terminal, but how can I start it using the GUI ?
It's not a graphical program, so you can only run it from a terminal. Therefore it wouldn't make any sense to have an icon for it in any graphical menu.


What's "UBC"?

---

### Post by Frogs Hair on 2011-08-11
This program may run from the terminal . Check the main menu to see if the application is listed and the box is checked , only applications with icons appear on the main menu . If a program runs from the terminal typing the name and pressing enter will start it .

---

### Post by Amoranemix on 2011-08-12
I don't know how to create an launcher program, but maybe that doesn't matter anymore since I can start Partimage from the terminal.
 
 So, if I understand correctly, Partimage is a program that is designed to run in it's own environment rather than in an OS, therefore does not have an icon and Ubuntu copes badly with programs that lack an icon, which explains some anomalies.
 
 UBC stands for Ubuntu Software Center.
 
 I asked Partimage to make an image of the the original disk. I don't remember the name (it contained PC and VUB, perhaps PC_VUB with an extension) or where (I typed something that resembled a top location on the partition where Ubuntu is installed). Partimage then pretended to create an image file and the remaining free space the program indicated suggests the image was indeed created in the 60GB  partition.
 
 Now back in Ubuntu, how can I find that image ? The explorer (or whatever it's called in Linux) show the following locations :
 
[LIST]
[*]500GB Hard Disk : 94GB file system
[*]500GB Hard Disk : 328GB file     system
[*]500GB Hard Disk : 500GB file     system
[*]File system
[/LIST]
They corresponds to the main partitions (i.e. not counting the swaps) on the PC, except that the 60GB parition is missing and there is 'File System' instead. File System contains more than 90GB according to its properties. I verified in Vista that the image is not on one of the two Windows partitions (the 500GB and 94GB ones). In Ubuntu the GUI search function did not find any file containing VUB in File System nor in the 328GB partition and the command “which VUB” or “which PC” doesn't find anything either. File System takes long to search and Ubuntu crashed before the search finished.

 How can I find the image file or verify that it doesn't exist ?

---

### Post by mcduck on 2011-08-12
I would have  expected Ubuntu Software Center to be "USC" ;)

Anyway, it's not intended to be used outside of the operating system, it's just that it's a command-line application. You can just open a terminal and run it from there.

It doesn't have any entry in menus simply because it's supposed to be used form a terminal. Most of the time it makes no sense to start a command-line application from a menu because you often set options and giv parameters to command-line applications at the time you launch them, and a menu entry wouldn't be able to do such thing.

Also, it *does* appear in Software Center, it's just that most command-line programs, libraries and other packages that aren't exactly desktop applications are hidden in USC by default. In Ubuntu 11.04 you can go to "Installed"-section and click the "Show technical items"-link neat the bottom of the window to show them. They also appear in searches, but only if you type the *exact* name of the package. In older Ubuntu versions the Software Center only handles a selection of desktop applications, and packages like this need to be installed using Synaptic Pacakage Manager or apt-get instead.

---

