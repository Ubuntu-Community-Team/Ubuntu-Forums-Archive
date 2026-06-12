---
title: "Problem installing tar.gz files!"
date: 2010-05-18
forum: General Help
---

### Post by gunraidan on 2010-05-18
Hello, I'm very new to Linux (I'm currently on Ubuntu 10.4). I've managed to get by the installation and setup process and am getting use to where all the files and applications are located.

However I'm not sure how to install tar.gz files. I've looked on Google for some previous threads and found that people asking the same question and it usually result to entering some codes in the terminal, however when I do that the terminal asks me for my password and I enter it and it says it isn't valid. 

Can anybody offer me more insight on the process of installing tar.gz files please?

---

### Post by eltonw on 2010-05-18
> **gunraidan said:**
> Hello, I'm very new to Linux (I'm currently on Ubuntu 10.4). I've managed to get by the installation and setup process and am getting use to where all the files and applications are located.

However I'm not sure how to install tar.gz files. I've looked on Google for some previous threads and found that people asking the same question and it usually result to entering some codes in the terminal, however when I do that the terminal asks me for my password and I enter it and it says it isn't valid. 

Can anybody offer me more insight on the process of installing tar.gz files please?

These are zipped files, you need to untar / un-zip them. Some help to get you more familiar with linux: [http://ubuntuforums.org/showthread.php?t=1483371]("http://ubuntuforums.org/showthread.php?t=1483371")

HTH...

---

### Post by mac9416 on 2010-05-18
Hi, gunraidan. Welcome to Ubuntu!

What program are you trying to install? Most programs available can easily installed using Applications > Software Center without ever messing with a tar.gz file. You should check Software Center and see is the app you are looking for is available there.

---

### Post by gunraidan on 2010-05-18
> **mac9416 said:**
> Hi, gunraidan. Welcome to Ubuntu!

What program are you trying to install? Most programs available can easily installed using Applications > Software Center without ever messing with a tar.gz file. You should check Software Center and see is the app you are looking for is available there.

I'm trying to install file-roller, I'm just wondering the steps for installation.

I could look at the guides but I guess I'm a little lazy and would prefer someone to just tell me the 2 or 3 steps of doing it instead of navigating through endless pages.  :P

---

### Post by CharlesA on 2010-05-18
Do it this way:

```
sudo apt-get install file-roller
```

So much easier.

---

### Post by pizza-is-good on 2010-05-18
> **CharlesA said:**
> Do it this way:

```
sudo apt-get install file-roller
```So much easier.

Ahh...{reliefed} the amazing power of the terminal:guitar:
and sudo

makes me feel so sad for windows users....

---

### Post by CharlesA on 2010-05-18
apt-cache is your friend if you aren't able to get access to synaptic or software center. :)

---

### Post by v1ad on 2010-05-18
he said that his sudo password was not working, whats up in that case. it should be same as login.

---

### Post by CharlesA on 2010-05-18
> **v1ad said:**
> he said that his sudo password was not working, whats up in that case. it should be same as login.

It should work, unless he isn't an administrator and isn't in the sudoers file.

---

### Post by 3rdalbum on 2010-05-19
> **gunraidan said:**
> 
However I'm not sure how to install tar.gz files.

A .tar.gz is just a compressed archive. It can contain source code, binaries, themes, pictures of my aunt, the latest Metallica album, whatever you want.

The procedure for running or installing anything inside them will differ; of course you decompress it first using your archive manager, but then there's usually a file called INSTALL that tells you how to install it. Assuming it's something that has to be installed, because as I mentioned, it could just be pictures of my aunt.

Before trying to compile source code from a .tar.gz, first check with your package manager to see if the program is available there. If not, look on Google for the name of the program and the word "repository" or "PPA". If there's a repository or PPA that contains the program, then you'd best add it to your system and then you'll be able to install the program the same as if it was in the normal Ubuntu repositories; you'll get updates pushed out automatically too.

---

### Post by gunraidan on 2010-05-19
> **v1ad said:**
> he said that his sudo password was not working, whats up in that case. it should be same as login.

Exactly.

I press enter. And it says:

[sudo] password for myname:

and a box pops up and it doesn't resond to anything but "enter" and I assume that means that I have to put my password on the next line down but when I do it says "Sorry, try again."

---

### Post by CharlesA on 2010-05-19
Oh. If you do sudo in a terminal, it won't show you the password. Have you been typing your password, then hitting enter, or just hitting enter, since the password isn't showing up?

If that isn't the case, it sounds like sudo might be broken.
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by wojox on 2010-05-19
File roller is already installed. Hit Alt+F2 and enter:

```
file-roller
```

---

### Post by Dkkline on 2010-05-19
You might be a little confused by now...

ok here is a few tips:

1.) you're known to the windows interface where you have to download from webpages around the globe, here in Ubuntu you might wanna try the software center ("Applications -> Ubuntu Software Center")

2.) .tar.gz is like a .zip file, gz stands for "Gnome-Zip (correct me if I'm wrong, quite new to ubuntu myself)" 

3.) a very useful tool is the "Gnome-Terminal" (or just terminal) it 's a non graphic way to get around your OS (operative system) here at ubuntu forums, when you see a ```
code box like this one it usually means type this in the terminal, e.g in your case.
you might want to type this:
sudo apt-get install file-roller
```
what that means is : sudo (switch user, and do(sudo is default "root" which is "Admin")) apt-get: application-get is a command that allows you to download applications from the internet, via ubuntu, basicly ubuntu has the stuff on their website and it's a built-in download manager! (correct me if I'm wrong, and sorry for my bad english) 
install is a parameter in the command apt-get
well as I've seen you have noticed that when you use sudo commands it will ask for the password of the user, it doesn't show anything cause it's very secret! :) basicly don't care about it doesn't show it, just type and click enter
when it have downloaded it will ask you for your approval something like (want to install y/n) just type "y" and click enter

Welcome to Ubuntu, just ask if there is anything you need, Ubuntu people are unbelievable friendly and helpful, there is no shame in asking :)

hope this helped you, sorry about long post

---

### Post by Dkkline on 2010-05-19
Ohh yea, here is a example:

1.) try open a terminal (Applications -> Accessories -> Terminal) 
2.) we want to find something called "abuse" type ```
apt-cache search abuse
``` this will search for abuse, (notice you wont need sudo infront of this command because it's only a search, not installation)
3.) type ```
sudo apt-get install abuse
```
3.b.) this should install the game abuse once you have typed your password and types "y"
4.) now we want to remove it again, try type: ```
sudo apt-get remove abuse
```

hope this example helped

---

### Post by gunraidan on 2010-05-19
> **CharlesA said:**
>  or just hitting enter, since the password isn't showing up?


That one.

And looking at the user settings I'm still the administrator of my system.

It's like this:

[IMG]http://i48.tinypic.com/2w1zhc8.png[/IMG]

Then text won't appear when I press letters so i press enter than a blank line comes up and I enter my password. Then it greets me with:

[IMG]http://i49.tinypic.com/23s87b.png[/IMG]

---

### Post by CharlesA on 2010-05-19
> **gunraidan said:**
> That one.

Ah ok. Just type your password and hit enter and it should work.

---

### Post by gunraidan on 2010-05-19
> **CharlesA said:**
> Ah ok. Just type your password and hit enter and it should work.

Oh thanks. I didn't know it didn't display character movement. I feel quite silly now.

---

### Post by oldos2er on 2010-05-19
> **Dkkline said:**
> .tar.gz is like a .zip file, gz stands for "Gnome-Zip (correct me if I'm wrong, quite new to ubuntu myself)" 


gz = gzip. Nothing to do with Gnome.

---

### Post by CharlesA on 2010-05-19
> **gunraidan said:**
> Oh thanks. I didn't know it didn't display character movement. I feel quite silly now.
Happens to everyone. :)

---

