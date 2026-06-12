---
title: "Trying to install CRASH PLAN need help"
date: 2012-03-19
forum: General Help
---

### Post by ec1955 on 2012-03-19
Newbie here - I have had Ubuntu for over a year and love it! 
But...I don't know squat a out how to install programs etc.
I have downloaded CRASH PLAN for Linux I have it on my desktop but do not understand how to install it!

I have read an README file it says something about installing in 'this' directory - What? What directory?
How do I get to know what the heck is being told to me in this regard?
I have been to numerous pages where people said to go about learning this stuff...didn't seem to explain much.

I would appreciate any suggestions.

My External harddrive has over 230 g of my files on it and it won't openb which is why I am looking at CRASH PLAN.
Thanks
Ernest

---

### Post by PhantomTurtle on 2012-03-19
I've never used Crash Plan but I checked out the website and the Linux version gives you a .tgz file. So that means that you have to compile it yourself.

---

### Post by jerrrys on 2012-03-19
You don't have to compile, just open it.

[ATTACH]214576[/ATTACH]

I prefer dropbox

 [https://www.dropbox.com/](https://www.dropbox.com/)

---

### Post by claypole on 2012-03-25
Unfortunately it is not as easy as just opening the file. You need to  download and extract the file (by opening it as previously described),  then you need to open the Terminal (ctrl-alt-T usually works), go to the CrashPlan folder in your  Downloads directory (usually "cd ~/Downloads/CrashPlan-install") and  then run the installer "./install.sh". Then it should guide you through  the install process (choose to run as root when it asks) and then you're good to go!  
[B]
CrashPlan vs. Dropbox
[/B]
CrashPlan is a backup app and  Dropbox is a file sync app. Backup and file sync are related but _very different_ animals. I love Dropbox and use it to sync my regularly  needed files (several gigbytes) across multiple devices. I love Crashplan too - which ironically I refer to as the Dropbox of backup! - and I use it to backup all of my devices to  a local server *and* the cloud, including all the files in my Dropbox. In the  event I ever lose or corrupt any of my files or directories I can recover them from my  CrashPlan backup as it stores multiple revisions of my files going back  as long as I want :).  Dropbox does offer a premium file revisioning facility call Pack Rat, so  you can replicate a small element of the backup functionality but my CrashPlan backup is  over a terrabyte and growing as it backs up everything (docs, media,  system files) and offers a (premium) unlimited storage plan  (CrashPlan Central, Dropbox is 100Gb max) and you can backup as much as you like (depending  how much local storage you have) to your local (or a friend's) computer for free! I  back up all my computers to a local Synology NAS (Network Attached Storage) and then backup the NAS to CrashPlan Central. My desktop/laptop  computers syncs my documents folder using Dropbox :). There are many other differences, but one other critical one for me is that CrashPlan offers a private key facility, which means my encrypted backups (locally and on CrashPlan Central) are only accessible by me and no one else. This includes CrashPlan employees - they can access the backup file but cannot read it (not easily anyway) as I am the only person with the key to decrypt it. Dropbox files are encrypted between your computer and the cloud and on Dropbox servers, _but_ Dropbox employees _can_ access your files as they hold the encryption keys (and you agree to this when you sign the T&C's).

---

### Post by ec1955 on 2012-04-06
I don't get it.
I have Crashplan on my desktop - I open it up and I see the install.sh
I click on it and nothing. So I get a message that I need some software to open that 'shell' - I download something - it opens up and I click again on the install.sh - but it says that I have something not configured?
I didn't find Crashplan in my downloads because it is on my desktop.
So, what could I have done wrong?
Thanks for your assistance.
Ernest

---

### Post by PhantomTurtle on 2012-04-06
> **ec1955 said:**
> I don't get it.
I have Crashplan on my desktop - I open it up and I see the install.sh
I click on it and nothing. So I get a message that I need some software to open that 'shell' - I download something - it opens up and I click again on the install.sh - but it says that I have something not configured?
I didn't find Crashplan in my downloads because it is on my desktop.
So, what could I have done wrong?
Thanks for your assistance.
Ernest

First you want to make it executable, so open terminal and type in(assuming that instsall.sh is still on your desktop),
```
cd ~/Desktop
```
then you want to make it executable,
```
chmod +x install.sh
```
Then run it,
```
./install.sh
```
If it doesn't install properly or finishes with many error and doesn't install at all, then you need to give it root privileges. So you need to type in the following in terminal,
```
sudo sh ./install.sh
```

---

### Post by ec1955 on 2012-04-14
It didn't work.
I don't know, maybe I am entering this stuff wrong - am I to copy all of these codes and string them together in the terminal and then enter to run it?
Thanks
Ernest

---

### Post by PhantomTurtle on 2012-04-14
You do them one by one. When you extracted CrashPlan to your desktop, did it make a folder called crashplan or the install.sh file? If it make a folder then you have to run
```
cd ~/Desktop/foldername
```

Additionally if you get any errors, post them the terminal output here(copy and paste)

---

### Post by ec1955 on 2012-04-24
Yeah, I don't get it - I know, you can call me 'stupid' because I am regarding this stuff.
I opebed a terminal and copied and pasted all the you said NADA!
So I opened the CRASHPLAN folder on my desktop and a 'terminal opened that eventually said that it was installed!
I do not understand what the heck is happening here.

I am finding this to be nearly impossible. to figure out how and what I should do to get this program installed and operating.

I know I should read up on this more but I have numerous other projects that need my attention.

I do not like WINDOWS but it is so much easier to install/run/uninstall programs etc.

Thanks for your help, 
I will eventually try again one day.
Ernest

---

### Post by PhantomTurtle on 2012-04-24
Sorry I could not help with my last reply and nobody on this forum will call you stupid for that. Can you please post the terminal output of the error you got when you tried to run "install.sh".

---

### Post by ec1955 on 2012-05-14
Sorry I haven't replied sooner but I am busy.
Thanks for your help.
So, I placed my CRASHPLAN folder on my destop.
It says CRASHPLAN-INSTALL.
Now, exactly what do I need to do?

I opened a terminal (ctrl/alt/T0
I typed in CRASHPLAN-INSTALL and it said , "COMMAND NOT FOUND"
How must I type this in to get it to open correctly?
Thanks again!
Ernest

---

### Post by PhantomTurtle on 2012-05-14
> **ec1955 said:**
> Sorry I haven't replied sooner but I am busy.
Thanks for your help.
So, I placed my CRASHPLAN folder on my destop.
It says CRASHPLAN-INSTALL.
Now, exactly what do I need to do?

I opened a terminal (ctrl/alt/T0
I typed in CRASHPLAN-INSTALL and it said , "COMMAND NOT FOUND"
How must I type this in to get it to open correctly?
Thanks again!
Ernest

You have to use the cd command to change directories into your desktop. Then you have to make sure it is executable by running,
```
chmod +x CRASHPLAN-INSTALL
```
in terminal.
Then you have to run it as,
```
./CRASHPLAN-INSTALL
```
in terminal. Then it should install.

---

### Post by ec1955 on 2012-05-15
Sorry for my ignorance, but is CD command? and how would I accomplish this?
Thanks, Ernest

---

### Post by PhantomTurtle on 2012-05-15
> **ec1955 said:**
> Sorry for my ignorance, but is CD command? and how would I accomplish this?
Thanks, Ernest

The cd command changes directories, so if your crash plan install file in a folder called crashplan in your desktop you open terminal and type in,
```
cd /home/yourusername/Desktop/crashplan
```
or if it was in documents,
```
cd /home/yourusername/Documents
```
This will only change you into a folder, don't direct it to the Crashplan installer.

---

### Post by Erik1984 on 2012-05-15
To build on PhantomTurtle's answer: A common shorthand in Linux for "/home/yourusername" you will find a lot on this forums is tilde (~) symbol. He used that in an earlier post in this thread.

So the command:
```
cd ~/Documents
```brings you to the exact same directory as:
```
cd /home/yourusername/Documents
```

---

### Post by PhantomTurtle on 2012-05-16
> **Euroman said:**
> To build on PhantomTurtle's answer: A common shorthand in Linux for "/home/yourusername" you will find a lot on this forums is tilde (~) symbol. He used that in an earlier post in this thread.

So the command:
```
cd ~/Documents
```brings you to the exact same directory as:
```
cd /home/yourusername/Documents
```

Oh yes, I didn't do that so that ec1955 wouldn't get confused. But yes I should have mentioned that as well.

---

### Post by abexman on 2012-06-01
Guys, thanks for these. I seem to be able to get the shell running but when it does it says 

> ./install. defaults MISSING!

but that install.defaults file does seem to be present in the same folder as the .sh file?

---

### Post by ec1955 on 2012-07-12
Hi, it's me again!!
Well, I still don't understand what you are telling me - but, what I did was, 
as I mentioned before, I have CRASHPLAN on my desktop -I opened this file and clicked on INSTALL folder - (I opened using GNU EMACS 23)- when this folder opened it said, "Welcome to CRASHPLAN for LINUX - to install run the installer in this directory -/install.sh
So, what exactly should I do now?
I see what you have written above - is that what I should use?
Thanks for your patience!
Ernest

---

### Post by PhantomTurtle on 2012-07-12
> **ec1955 said:**
> Hi, it's me again!!
Well, I still don't understand what you are telling me - but, what I did was, 
as I mentioned before, I have CRASHPLAN on my desktop -I opened this file and clicked on INSTALL folder - (I opened using GNU EMACS 23)- when this folder opened it said, "Welcome to CRASHPLAN for LINUX - to install run the installer in this directory -/install.sh
So, what exactly should I do now?
I see what you have written above - is that what I should use?
Thanks for your patience!
Ernest

Why don't we just start over. Download Crash Plan for Linux from here - [http://www.crashplan.com/consumer/download.html?os=Linux]("http://www.crashplan.com/consumer/download.html?os=Linux"). Now extract using the archive manager which will open when you double click the downloaded file. Extract it to the desktop. You need Java, to check if you do run,
```
java -version
```
If that tells you, that Java is not install type in the following in terminal to install it,
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
To check if java is installed run,
```
java -version
```

Next open terminal. Type in,
```
cd ~/Desktop/CrashPlan-install
```
(you might have it in a different folder and the name might be different, just make sure to change directories into the folder that has the README and install.sh files in it.)
```
chmod 777 install.sh
./install.sh
```
Once the install is finished run the command,
```
CrashPlanDesktop
```
This will open the crashplan GUI.
Hopefully that helps you get it working.

---

### Post by exup1000 on 2012-07-19
Many thanks, I was having difficulty too, it was the chmod 777 install.sh bit that I was tripping over.
Now its working nicely. I like the app as its cross platform and very simple to run, emails me when machines have not backed up recently. I did have a very complex RSYNC script running but was very high maintenance. This is set and forget almost.

---

### Post by ec1955 on 2012-07-31
Well, I downloaded to my DESKTOP as you said -
I open a terminal and typed in that which you said to do - it said 'directory not found'
I have JAVA on here as it is used elsewhere - I have a toolbar on the bottomm of my screen which indicates when it is 'on and 'off' 
Should I run both commands one after the other?
Thanks
Ernest

---

### Post by ec1955 on 2012-07-31
It did say I had JAVA running - but when I typed in other codes it says** ''file or directory not found'**!
I checked the folder and of course the install etc are in there.
I don't get it
Ernest

---

### Post by PhantomTurtle on 2012-07-31
> **ec1955 said:**
> It did say I had JAVA running - but when I typed in other codes it says** ''file or directory not found'**!
I checked the folder and of course the install etc are in there.
I don't get it
Ernest

Do you mind telling me exactly what you typed into the terminal that gave you the "file or directory not found". Also if it is still a tar.gz file make sure to extract it first by double clicking it and extracting after archive manager opens. Also if you can, show me a screenshot of File browser opened to the crash plan folder(screenshots can be taken and saved by pressing print screen on your keyboard).

---

