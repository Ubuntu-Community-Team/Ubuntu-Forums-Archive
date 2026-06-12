---
title: "&quot;This script must be run as root&quot;"
date: 2012-06-15
forum: General Help
---

### Post by Ali_Barba on 2012-06-15
Hello. 

I am trying to install a program, but when I enter "./install" in the terminal, I get the message: 

"This script must be run as root"

How can I run it as root, and what does that mean ?

---

### Post by diesch on 2012-06-15
Use
```
sudo ./install
```root is the privileged adiminstrator's account in Linux. It's usually needed for example to install software outside your home folder.

Be careful what you do and run as root. Only run programs and scripts from trustworthy sources that way as the can harm your system.

---

### Post by Ali_Barba on 2012-06-15
Thank you. 

I used the "sudo ./install" command and it asked me for my password, which I entered. Then I got the message "command not found", though I navigated exactly to the directory where it is inside. 

I am trying to install Avira Antivir Personal for Linux, if that helps. I unzipped the gz package to the /tmp folder in the main drive, where Linux is installed. I renamed it to "antivir" since the original name was long and complicated. 

Yet I cannot get it to install.   :(

---

### Post by Ali_Barba on 2012-06-15
Do I have to enter "sudo ./install" exactly or something like "sudo cd /tmp/antivir/install" ?

---

### Post by Ali_Barba on 2012-06-15
I quote from the Terminal with translations in bold, since it is the German version: 

> axel@axel-ESPRIMO-P:/tmp/antivir$ ./install
bash: ./install: Keine Berechtigung** (No permission)**
axel@axel-ESPRIMO-P:/tmp/antivir$ sudo ./install
sudo: ./install: Befehl nicht gefunden **(Command not found)**
So first it asks me for permission, and when I enter "sudo" before the "./install" it suddenly does not find the command anymore ?!   :confused:

But when I open the folder with the file manager, the install command/file is clearly there !

---

### Post by Ali_Barba on 2012-06-15
Could it be that the program, though written for Linux, is not compatible with Ubuntu ?

It's quite annoying that such a simple task like installing a downloaded program is so complicated under Linux. I'm not a computer illiterate, i have been working with Windows computers extensively since 1996 and some would call me a power-user with some reason. But Linux beats me.

---

### Post by Ali_Barba on 2012-06-15
Maybe somebody could download the program, too, and see whether it works ? The source is definitely trustworthy, one of the major antivirus companies. But maybe they made some mistake while writing the installer and it is corrupted ? :mad:

---

### Post by lisati on 2012-06-15
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Please post back if you have any further questions or comments.

---

### Post by Ali_Barba on 2012-06-15
> **lisati said:**
> Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Please post back if you have any further questions or comments.

Yeah, I got the sudo thing now, but it still will not install. 

See the quote from the Terminal above.

---

### Post by HarryTorry on 2012-06-15
Could you show the output of an 'ls' in the install directory?

---

### Post by MedianMajik on 2012-06-15
You are probably not located in the same working directory as the script you are attempting to run.  Instead of ```
sudo ./install
``` try entering the full path to the script, starting at the root directory.  It'll be something like ```
sudo /tmp/antivir/install
```

---

### Post by Ali_Barba on 2012-06-15
> **MedianMajik said:**
> You are probably not located in the same working directory as the script you are attempting to run.  Instead of ```
sudo ./install
``` try entering the full path to the script, starting at the root directory.  It'll be something like ```
sudo /tmp/antivir/install
```

I tried it before, and now again, but no luck. It asks me for the password, then tells me that it did not find the command. 

Also my Terminal is behaving strange -- i cannot see the characters I am typing in it until I press Enter and it shows up in a new line. I therefore write everything in an editor and paste it into the Terminal.

---

### Post by Ali_Barba on 2012-06-15
> **HarryTorry said:**
> Could you show the output of an 'ls' in the install directory?

A what ?  :confused:

---

### Post by dodo3773 on 2012-06-16
Does it work if you move the installer somewhere other then the /tmp directory? Just a guess. Not sure on the default exec permissions of ubuntu these days.

Secondly, the reason HarryTorry was asking you to give us the output of "ls" was (I am guessing) that we can see what is in that directory (ls is similar to dir in windows if that is where you are coming from). To make sure that there was in fact a file or script called install in that directory.

Just so you know by default an executable is not actually executable in gnu unless the executable bit is set. This can be done with the chmod program. For an example in your case (if the name of your install script is simply "install") it would be something like this:

```

chmod +x install

```

I say this because I am not sure how you extracted it. Or for that matter how it wound up in /tmp in the first place.

---

### Post by diesch on 2012-06-16
What's the ouput of
```
file ./install
```
and
```
head ./install
```

---

### Post by dodo3773 on 2012-06-16
> **diesch said:**
> What's the ouput of
```
file ./install
```
and
```
head ./install
```

Why would the "./" be needed? What is the reasoning behind this? Just curious.

---

### Post by diesch on 2012-06-16
For *file* and *head*  "./" is not needed, but doesn't harm either.

---

### Post by dodo3773 on 2012-06-16
> **diesch said:**
> For *file* and *head*  "./" is not needed, but doesn't harm either.

Now that I think about it a little more I guess it would not matter much at all since "./" is probably being interpreted by the shell as "currentdirectory/filename". Since the commands head and file are not taking external commands as arguments. Interesting though.

---

### Post by stinkeye on 2012-06-16
> **Ali_Barba said:**
> Could it be that the program, though written for Linux, is not compatible with Ubuntu ?

It's quite annoying that such a simple task like installing a downloaded program is so complicated under Linux. I'm not a computer illiterate, i have been working with Windows computers extensively since 1996 and some would call me a power-user with some reason. But Linux beats me.

Do you need antivirus?
[**_[COLOR="DarkRed"]https://help.ubuntu.com/11.04/ubuntu-help/net-antivirus.html[/COLOR]_**]("https://help.ubuntu.com/11.04/ubuntu-help/net-antivirus.html")
It's very easy to install programs using the software centre or third party  repositories where you can download a deb file or add the repo so you get updates.

---

### Post by Ali_Barba on 2012-06-16
> **stinkeye said:**
> Do you need antivirus?
[**_[COLOR=DarkRed]https://help.ubuntu.com/11.04/ubuntu-help/net-antivirus.html[/COLOR]_**]("https://help.ubuntu.com/11.04/ubuntu-help/net-antivirus.html")
It's very easy to install programs using the software centre or third party  repositories where you can download a deb file or add the repo so you get updates.

Yes, thanks for the suggestion. I already installed ClamAV via the Software Center and let it run for hours, but it finds thousands of false positives (and maybe some real infected files, but how to find them amongst 3,000 "PUA" ?    I guess I already deleted the four real virus files before with the Linux file manager, before even starting ClamAV.   ;-)

I'll give Net-Antivirus a try, and apart from that download some of the latest Live-CDs available from the big antivirus companies. 

I guess I'll give up on the Avira Antivir install ... 

PS: I downloaded it as a package (*.gz), then unzipped it to the download folder, copied it subsequently into the *tmp folder and renamed it there to "antivir" -- and yes, it does contain a file called "install" with slightly above 100kB - 107kB, I guess - which I can open in an editor and see a lot of code in uncompiled programmer language there (i.e. understandable programmer's code, not machine code). You can download the program for yourself to see, it's free after all.

---

### Post by 3rdalbum on 2012-06-16
Try this:

Type 'sudo' as you've been doing, plus a spacebar. Then drag the "install" file to the terminal, which will fill in its whole file path. Click on the terminal again to bring it to the front, and press Enter.

If you get "permission denied" then you need to add execute permissions:

```
sudo chmod a+x <drag the file into the terminal>
sudo <drag the file into the terminal>
```

---

### Post by HarryTorry on 2012-06-16
> **dodo3773 said:**
> Secondly, the reason HarryTorry was asking you to give us the output of "ls" was (I am guessing) that we can see what is in that directory (ls is similar to dir in windows if that is where you are coming from). To make sure that there was in fact a file or script called install in that directory.

Correct, I was wondering if it was a script, and he was lacking .sh etc

---

