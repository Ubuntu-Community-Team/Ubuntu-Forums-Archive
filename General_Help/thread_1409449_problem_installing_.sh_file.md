---
title: "problem installing .sh file"
date: 2010-02-17
forum: General Help
---

### Post by dochc on 2010-02-17
I'm trying to install a .sh file but I'm not really having any luck, probably because I (almost!) haven't got a clue what I'm doing. I've looked through the forums and found one similar thread but it didn't help me any.

I've very recently installed: Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) having finally lost all patience with Windows XP.

I think everything went to plan with the download, but clicking .sh file brings up the following message in gedit:

[I]Could not open the file /home/alexis/Downloads/install_personal_accountz_32.sh using the Unicode (UTF-8) character coding.
Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again.

the default character is: Current Locale (UTF-8)
[/I]
I've changed this to Western (iso 8859-15) as the only other option in the drop down list but this brings the same error message.

There must be something there as it's 31.4MB.

If you can please try to keep answers simple, I've only just put my first toe on the bottom rung of Linux/Ubuntu, I'd really appreciate it. Apologies if this is in the wrong place too.

---

### Post by jamesisin on 2010-02-17
Two things.

First of all a .sh file is a shell script and does not require installation.  You merely need to tell your system to allow execution of that particular file.  Then you can run the script by various methods.

Secondly, running an unknown script can be DEADLY to your system.

Where did you get this shell script?  What are its contents?  What are you trying to accomplish?

---

### Post by dochc on 2010-02-17
Hi thanks for the reply,

The script is a for a home accounts package. I bought this today and downloaded it. I am very sure I can trust the Company and the script I've downloaded from their site as I've been using their Windows products for years now. I know I could have used one of the many Linux varieties available but I've been using this one for so long that I am very familiar and comfortable using it.
So what do I have to tell Ubuntu to do with it to get it to install?

---

### Post by jamesisin on 2010-02-17
Save the file some place useful.  Right-click on the file and choose Properties.  On the Permissions tab of the Properties dialog check the "Allow executing file as program" box.

You can run it by double-clicking it and either choosing Run in Terminal or simply Run (I would probably choose Run in Terminal at least the first time).

---

### Post by dochc on 2010-02-17
Fantastic, that seems to have done the trick. Many thanks.
There are all these error messages showing in the terminal window, but I seem to have a working version of the software.

Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
Cannot run program "/home/alexis/PersonalAccountz/pds.command" (in directory "/home/alexis/PersonalAccountz/."): java.io.IOException: error=2, No such file or directory
Cannot run program "/home/alexis/PersonalAccountz/demoFolder.command" (in directory "/home/alexis/PersonalAccountz/."): java.io.IOException: error=2, No such file or directory
Cannot run program "/home/alexis/PersonalAccountz/Personal Accountz.exe" (in directory "/home/alexis/PersonalAccountz/."): java.io.IOException: error=2, No such file or directory

Should I be concerned about these?

I also now have a shortcut on the desktop but would prefer it if this resided in the applications menu - it's what I love about Ubuntu, a beautiful uncluttered desktop. I'm assuming this must be as easy getting this running!

---

### Post by nothingspecial on 2010-02-17
What is it, where is it, does it have a README file in it?

---

### Post by dochc on 2010-02-17
Errrm! This I think is where I really like your quote and is in fact the the rather large spanner in my machine at the moment. Sorry to be completely obtuse about this but how do I find the answers to these questions? There is is no obvious README file open

---

### Post by nothingspecial on 2010-02-17
Where exactly, in your file system is the .sh file.

Is it on your desktop?

Is it in your home folder?

What exactly is it called?

What is the thing that you downloaded called exactly, and where is it, and what is in it?

---

### Post by dochc on 2010-02-17
it's in my home folder under downloads. It's called install_personal_accountz_32.sh. (this is the file I downloaded and I don't know what's in it other than I've learned it's a shell script). Following the advice above and running this in a terminal this created a folder called install_personal-accountz_32.sh.3116.dir, which contains a bunch of files and a jre folder.

---

### Post by nothingspecial on 2010-02-17
This is going to be one of those pain in the ***, things that happen on (world wide) forums, where I have to go now.

Please, link the site you got this from and any other info you can think of.

If no one else has had a look, I`ll have a look tommorow.

Sorry, and don`t worry, we`ll get this working, as you said, it`s a linux app.

---

### Post by dochc on 2010-02-17
Thanks for looking. Here's the URL: [http://www.accountz.com/accountz/personal-accountz](http://www.accountz.com/accountz/personal-accountz). There's not alot of useful information on this site well not at least related to this.

---

### Post by jamesisin on 2010-02-17
dochc - JRE is Java (the Java Runtime Environment).  If the application is functioning as expected, perhaps there is little to be concerned with as regards the errors?

You can create a launcher (like the one on your desktop) pretty easily.  Right-click a panel and choose Add to Panel (and then Custom Application Launcher).  Look at the properties for the launcher on your desktop for the information you'll need to build the new one.  (Dragging and dropping may also work.)

Personally I use Gnome-Do instead of application launchers/icons:

[http://www.soundunreason.com/InkWell/?p=1367](http://www.soundunreason.com/InkWell/?p=1367)


nothingspecial - Is there a repository for Guayadeque Music Player?  I'd like to check it out (and prefer repos).

---

