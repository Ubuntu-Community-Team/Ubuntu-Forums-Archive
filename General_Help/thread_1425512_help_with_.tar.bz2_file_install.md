---
title: "help with .tar.bz2 file install"
date: 2010-03-09
forum: General Help
---

### Post by jhaskins75 on 2010-03-09
First, I would like to extend my appreciation to all the help I have received so far from forum users to Moderators, and advanced Geeks. I am relatively new to Linux / Ubuntu and need all the help available to get up to speed. I have pretty well mastered the basics, now I need help with these pesky .tar files. I use the softwares that are available in the install add/remove program, but most seem to be out dated in terms of versions. An example of this is ' Vuze '. I have Vuze on my Windows OS, and it was offered with Linux, but now I do not see it in the add /remove softwares. I went to their web page and it stated clearly the newer version for Linux, and I proceeded to download it, but of course, there I was again faced with the .tar.bz2 scenario. I go through the process of open / extract / all files / and everything runs to successful, but I can't find the program to open or run. I have not mastered the use of the terminal in entering commands. I have followed some examples such with 'sudo' and ~cd, but with very limited results. If I can just get pass the .tar road block, I will be off to the races. All and any help appreciated. ' Oh, I forgot, I went to Synaptic Package Manager and typed in ' tar ' and seen multiple programs listed and I read their description, highlited them for install / upgrade / closed. I have not tried to download a .tar file, untill I get a answer from the community. thank you, John

---

### Post by cjhabs on 2010-03-09
tar is a command line utility, installed by default.
In a terminal:
which tar
will return which folder the system found the tar executable.
man tar
will list the man page.
tar xvf tar_file.tar
will extract the tar file into the current folder, recreating the folder structure of the tar file.
Note: I have come across tar files which were created using absolute path names, so they extract into those absolute folders - so I always first run:
tar tvf tar_file.tar
which lists the contents without extracting.

---

### Post by 2hot6ft2 on 2010-03-09
You can also use alien
```
sudo apt-get install alien
```
in a terminal
Applications > Accessories > Terminal
Then run
```
sudo alien PackageName.tar.bz2
```
With the PackageName.tar.bz2 in your home folder
And it will create a PackageName.deb you can install with in your home folder.

---

### Post by dcnlwfh on 2010-03-09
This had previously been a problem for me, but I realized you have to extract the files first with the GUI by right clicking the file, then you have to copy the files from there to the hidden applications folder in your home directory.  Once you've done that, make a shortcut on the applications menu using menu editor.  If you don't have it go to Applications>Add/Remove and find menu editor.  It's a little more complicated than Windows.

---

### Post by dcnlwfh on 2010-03-09
> **2hot6ft2 said:**
> You can also use alien
```
sudo apt-get install alien
```in a terminal
Applications > Accessories > Terminal
Then run
```
sudo alien PackageName.tar.bz2
```With the PackageName.tar.bz2 in your home folder
And it will create a PackageName.deb you can install with in your home folder.

that's a great idea I didn't know how to do that myself

---

### Post by jhaskins75 on 2010-03-18
I downloaded Realtek-linux-audiopack-5.14 and of course it is a tar.bz2 which I am still having a fit in trying to open / install. I tried the sudo apt-get install *name *but that does not work. I open the read me text file and it is saying something to the extent of a source code to a web address, which I am not yet familiar with this process. I was given a list of commands that helped me to install tar files, but my installation crashed a while back and I lost all my bookmarks to that information. Can someone assist me with this request. Thank you. John

---

### Post by jhaskins75 on 2010-03-25
> **2hot6ft2 said:**
> You can also use alien
```
sudo apt-get install alien
```in a terminal
Applications > Accessories > Terminal
Then run
```
sudo alien PackageName.tar.bz2
```With the PackageName.tar.bz2 in your home folder
And it will create a PackageName.deb you can install with in your home folder.
**tohot6. Thanks for the info you provided me awhile back on tar.bz2 questions I had. I have another problem with the installation of Realtek linux-audio package 5.14. I downloaded the version for linux [ I run ubuntu ] and I reloaded / updated it in my synaptic Manager, but I am having a dificult time in opening / running the program. I read the read me text instructions for manual install, but it will not reconize the commands I was told to enter, even using the sudo prefix. I am still in the infancy stage of linux and I have some sucess with the terminal commands, Like apt-get updates, install, source etc. etc.**Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
    (soundcore module, default turn on)

Step 3. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure (--with-cards=hda-intel)<= for HDA options
    c. make
    d. make install
    e. alsaconf

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
     (Please refer to the attached modules.conf)
     
        snd-xxxx is the card ID.

    -- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
       --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
             but that's as far I have learned to date**. here is the script message given to me.** Really would love all the help you can give me with this. Thank you, John [ Oh ] The reason I want to use Realtek, cause it has a audio Manager program which gives you tons of sound effects and it uses the AC97 Driver. I have it installed in my Windows OS and the sound is super. The standard Alsa drivers are somewhat flat and scratchy with no Equalizer to taylor your sound output and I installed the necessary driver packs but the quality is still undesirable....

---

