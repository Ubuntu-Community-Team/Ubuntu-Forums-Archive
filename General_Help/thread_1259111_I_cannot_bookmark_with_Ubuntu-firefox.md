---
title: "I cannot bookmark with Ubuntu-firefox"
date: 2009-09-05
forum: General Help
---

### Post by sopadeajo on 2009-09-05
I cannot bookmark with Ubuntu-firefox

Just i lost all the bookmarks i had keeped from last session and furthermore i cannot bookmark new web pages using the mouse Bookmark this page feature

Ubuntu 9.04 Desktop Edition installed fron an original CD yesterday and Firefox-ubuntu version 3.0.8 Mozilla Firefox for Ubuntu canonical- 1.0

---

### Post by zipperback on 2009-09-05
Can you book mark a page using the menu options Bookmarks -> Bookmark this page?

What exactly happens when you try to bookmark something?


- zipperback

---

### Post by falconindy on 2009-09-05
Sounds like a permissions issue. Run `firefox` from a terminal and see if you get a permission denied error when you try to bookmark something. If you do, it should give you the name of the file/directory you'll need to chmod 744 on.

---

### Post by sopadeajo on 2009-09-05
> **zipperback said:**
> Can you book mark a page using the menu options Bookmarks -> Bookmark this page?

What exactly happens when you try to bookmark something?


- zipperback

No i cannot bookmark using the menu bookmarks and when i click on Bookmark This Page (mouse feature) i get nothing at all.

yesterday i could go to the menu bookmarks and find there my kept bookmarks but now there is nothing.it does not work.

---

### Post by lovinglinux on 2009-09-05
See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

It could also be a permission issue. In this case, see **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the same section.

---

### Post by sopadeajo on 2009-09-05
> **falconindy said:**
> Sounds like a permissions issue. Run `firefox` from a terminal and see if you get a permission denied error when you try to bookmark something. If you do, it should give you the name of the file/directory you'll need to chmod 744 on.

firefox starts perfectly from a terminal window but i am new to linux and do not understand the rest of your post

---

### Post by sandman3838 on 2009-09-05
You know I might be having the same issue?

Check this out?

[http://ubuntuforums.org/showthread.php?t=1252984](http://ubuntuforums.org/showthread.php?t=1252984)

---

### Post by falconindy on 2009-09-05
> **sopadeajo said:**
> firefox starts perfectly from a terminal window but i am new to linux and do not understand the rest of your post
Sorry. Let me elaborate: When you run a program from a terminal, the program will often output things to the terminal where the program was started from. The output varies widely -- it might be notes that a developer left behind, or it could be an error that the program encountered. In this case, when you go to bookmark an item, you might see something like:
```
Permission denied: /home/user/.mozilla/profiles/q7r23fu9/bookmarks.html
```
If that's the case, it means that at some point, somehow, the permissions were changed in your profile directory. The `chmod` command is used to alter permissions on files and directories, allowing (or disallowing) the owner, and other users read/write access to said files.

---

### Post by sopadeajo on 2009-09-06
> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003").

It could also be a permission issue. In this case, see **Solution** [*[COLOR=Red]**FOT001**[/COLOR]*] from the same section.

I cannot find your fot003 nor fot001.
The problem with firefox seems to be serious since the back and forward arrows are not working, that is i cannot see my historial at all. What should i do?

---

### Post by DeMus on 2009-09-06
> **sopadeajo said:**
> I cannot find your fot003 nor fot001.
The problem with firefox seems to be serious since the back and forward arrows are not working, that is i cannot see my historial at all. What should i do?

You opened the page lovinglinux showed you? Just click on the link in his answer.
Then on that page type ctrl + f (press ctrl key and keep it pressed while typing the letter f) At the bottom of the screen you get a search frame. type fot and click on Next, and again and again .... until you see fot 001 and / or fot 003

---

### Post by sopadeajo on 2009-09-06
OK, i go to the profile folder , look for places.solite file and delete it.But i am new to Linux and do not know where is the profile folder neither how to find it
Any help?

---

### Post by lovinglinux on 2009-09-06
> **sopadeajo said:**
> OK, i go to the profile folder , look for places.solite file and delete it.But i am new to Linux and do not know where is the profile folder neither how to find it
Any help?

Read the beginning of the tutorial. It has a Profile section and everything else you need.

---

### Post by sopadeajo on 2009-09-06
I might be very unlucky or else the Murphy law is torturing me.
I did twhat i read behind but i still do not find the  profile folder even though i press the ctrl+h.And neither the other way:
~$ firefox-P
launches firefox but no way to see the profile folder.I am really unlucky or what is happening????????????



"Profiles are stored in your home directory, under the hidden folder .mozilla/firefox/. To see it, you need to hit CTRL+H when browsing home. The default profile folder name has a series of random letters and number, followed by *.default* (example: *ydtehagr8ja.default*).

You can create any number of profiles you want. They won't affect each other. To create a new profile, close Firefox the open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:"

---

### Post by lovinglinux on 2009-09-06
> **sopadeajo said:**
> I might be very unlucky or else the Murphy law is torturing me.
I did twhat i read behind but i still do not find the  profile folder even though i press the ctrl+h.

Go to your home folder and press CTRL+H. You should see a bunch of folders starting with a dot. Look for the .mozilla and open it. Open the folder inside it, named firefox. You should see a file named profile.ini and a folder with a bunch of letters. Open the folder, not the file. That's your profile directory.

> **sopadeajo said:**
> ~$ firefox-P

There is a space between **firefox** and **-P**. This command will launch your profile manager, from where you can create, delete, rename and start profiles, but you cannot browse them from there. If Firefox is already opened, it won't start the profile manager. You need to close Firefox or start the profile manager with the -no-remote option, like this:

```
firefox -P -no-remote
```

---

### Post by sopadeajo on 2009-09-06
I believe that Ubuntu and Firefox software developers should be careful of correcting these kind of problems with firefox or with any other application, because that happened on my very first day after installing the official Ubuntu 9.04 (in a CD) and i have had no time to learn Ubuntu, besides it should be considered that operations with a OS must be easy to do, not hard to do because an OS is there to facilitate things between machine and us, not to the contrary and that a OS navigator cannot fail the very first day you use it.
Because people will get back to window$ which i do not like at all, and is a bad OS, but at least Firefox works well with it. Do not forget that most people do not have enough time to be spent in reparing things the first day they use it.

---

### Post by sopadeajo on 2009-09-06
> **lovinglinux said:**
> Go to your home folder and press CTRL+H. You should see a bunch of folders starting with a dot. Look for the .mozilla and open it. Open the folder inside it, named firefox. You should see a file named profile.ini and a folder with a bunch of letters. Open the folder, not the file. That's your profile directory.



There is a space between **firefox** and **-P**. This command will launch your profile manager, from where you can create, delete, rename and start profiles, but you cannot browse them from there. If Firefox is already opened, it won't start the profile manager. You need to close Firefox or start the profile manager with the -no-remote option, like this:

```
firefox -P -no-remote
```

I have found the place.sqlite files (there are more than one) in home\myname\.mozilla\firefox\9lz7d22i.default
but doing CTRL+H is useless for me and no access to these files which are grey colored and really well protected.Are you certain that the action to be taken to fix the problem is really to delete the places.sqlite files?
Anyway i have no access to them.

---

### Post by lovinglinux on 2009-09-06
> **sopadeajo said:**
> I believe that Ubuntu and Firefox software developers should be careful of correcting these kind of problems with firefox or with any other application, because that happened on my very first day after installing the official Ubuntu 9.04 (in a CD) and i have had no time to learn Ubuntu, besides it should be considered that operations with a OS must be easy to do, not hard to do because an OS is there to facilitate things between machine and us, not to the contrary and that a OS navigator cannot fail the very first day you use it.
Because people will get back to window$ which i do not like at all, and is a bad OS, but at least Firefox works well with it. Do not forget that most people do not have enough time to be spent in reparing things the first day they use it.

Is not an issue with Firefox+Ubuntu. These kind of problems are due to sqlite database corruption and it it happens on Windows too. Mozilla, which develops Firefox, probably don't care if you use Windows or Ubuntu. 

> **sopadeajo said:**
> I have found the place.sqlite files (there are more than one) in home\myname\.mozilla\firefox\9lz7d22i.default
but doing CTRL+H is useless for me and no access to these files which are grey colored and really well protected.

As far as I know, there is no such thing as being grey coloured. You should have total access to those files, unless you did something wrong like starting Firefox with sudo.

Copy and paste the following code in the terminal just to make sure you have the correct permission on the mozilla folder:

```
sudo chown -R $USER:$USER ~/.mozilla
```

Do not replace anything on the code above, just copy and paste it on a terminal and click "Enter". After doing that, check if you can add bookmarks. If yes, then you don't need to do anything else. Otherwise, follow the instructions below:

You can also delete the file places.sqlite from terminal. Keep in mind that it will delete all your bookmarks and browsing history. You can restore them from backups if available. See the Backup section of my tutorial for instructions:

```
sudo rm -f ~/.mozilla/firefox/9lz7d22i.default/places.sqlite
```

> **sopadeajo said:**
> Are you certain that the action to be taken to fix the problem is really to delete the places.sqlite files?

Yes, I'm pretty sure that's causing the problem with bookmarks or the other thing already explained. 

If nothing works and if you don't care about loosing firefox settings and bookmarks, then simply run this command:

```
rm -fr ~/.mozilla/firefox
```

This will delete your profile and a new one will be created when you start Firefox again. Please keep in mind that Firfefox needs to be closed to perform these operations.

---

