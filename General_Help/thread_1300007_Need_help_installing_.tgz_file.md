---
title: "Need help installing .tgz file"
date: 2009-10-24
forum: General Help
---

### Post by lightningrod66 on 2009-10-24
Hello,
I have gnome desktop on Ubuntu 9.04 server until I get good at command-line things.  I just downloaded a file in ".tgz" format to the Desktop.  The instructions say to open terminal, cd to the download directory and type in tar xvfz "filename".  I did this, and now there is a folder on the Desktop named "filename" with a usr and etc folder within.  I assumed that when I untarred that the files/folders would go where they needed to go and not in the Desktop.  So I try to copy the contents of the usr and etc folders to the  usr and etc directories on my computer and I get "permission denied".  I assume this is because I am not ROOT.  How can I get this program installed if I am not ROOT?  I tried again using "sudo" before the tar xvfz "filename" and it didn't matter.

---

### Post by rockstarrem on 2009-10-24
An archive isn't an installer. Inside of it is probably a file called "configure". Go into the folder that contains this and type 

```

./configure

```

If it succeeds...
```

make
sudo make install

```

---

### Post by lightningrod66 on 2009-10-24
Let me try this another way:
Gnome Desktop on Ubuntu 9.04.  Downloaded a file in .tgz format.  Extracted and on Desktop now have a folder with etc and usr folders within.  Now what?  I need root privileges to copy the contents to my /etc and /usr directories.  Any help??

---

### Post by lightningrod66 on 2009-10-24
> **rockstarrem said:**
> An archive isn't an installer. Inside of it is probably a file called "configure". Go into the folder that contains this and type 

```

./configure

```

If it succeeds...
```

make
sudo make install

```

Sorry there is no configure file, only a "etc" folder and a "usr" folder

---

### Post by rockstarrem on 2009-10-24
What are you trying to install? Can you give a link?

---

### Post by lightningrod66 on 2009-10-24
> **rockstarrem said:**
> What are you trying to install? Can you give a link?

I don't have a link, but I can tell you the file.  I am trying to install nero for linux version 3.  it comes as a .tgz file, and when extracted, you get 2 folders: etc and usr.  There is no configure or install file.  I assume that the contents of the folders are supposed to be copied to the corresponding directories on your computer.  But for some reason I can't copy them because I don't have permissions.  I tried to login as root, but can't.  I tried to sudo then copy but still get not permissions.  This is my only peeve with linux is the whole permissions thing.  I wish I could have root permissions all the time, as I have been using computers for over 20 years and am not going to screw it up.  If I did, I could simply reinstall again - no big deal.

---

### Post by MelDJ on 2009-10-24
try: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html")

---

### Post by blwizard on 2009-10-24
> **lightningrod66 said:**
> I don't have a link, but I can tell you the file.  I am trying to install nero for linux version 3.  it comes as a .tgz file, and when extracted, you get 2 folders: etc and usr.  There is no configure or install file.  I assume that the contents of the folders are supposed to be copied to the corresponding directories on your computer.  But for some reason I can't copy them because I don't have permissions.  I tried to login as root, but can't.  I tried to sudo then copy but still get not permissions.  This is my only peeve with linux is the whole permissions thing.  I wish I could have root permissions all the time, as I have been using computers for over 20 years and am not going to screw it up.  If I did, I could simply reinstall again - no big deal.

Hey, you could use sudo when you copy the things, there is no reason it won't work, but I don't think it's the way to go. Because it's really weird for users to copy those files manually to /usr with root permission. Usually *.tgz contains source files and requires you to compile them and install them. Is the tgz file big? mind uploading it somewhere so we can have a look? Is there a Makefile in the folder?

---

### Post by slooow on 2009-10-25
> **lightningrod66 said:**
> Let me try this another way:
Gnome Desktop on Ubuntu 9.04.  Downloaded a file in .tgz format.  Extracted and on Desktop now have a folder with etc and usr folders within.  Now what?  I need root privileges to copy the contents to my /etc and /usr directories.  Any help??
You are on the right track. Do ' sudo cp -r DIRS TARGETDIR' to copy the directories to /usr and /etc directories.

---

### Post by lightningrod66 on 2009-10-25
> **blwizard said:**
> Hey, you could use sudo when you copy the things, there is no reason it won't work, but I don't think it's the way to go. Because it's really weird for users to copy those files manually to /usr with root permission. Usually *.tgz contains source files and requires you to compile them and install them. Is the tgz file big? mind uploading it somewhere so we can have a look? Is there a Makefile in the folder?

I don't know where i could upload it to, but there are no configure or make files included. I can extract and screen copy to show what files are there.

---

### Post by lightningrod66 on 2009-10-25
Oh another thing while we are on the subject.  I downloaded and installed Nero Linux 4 Trial.  I can't figure out how to uninstall it so that i can install a previous version I have that is a .deb file.  When I try to install the .deb file, it says a later version is already installed and won't let me install it.  There is no "uninstall" file for the nero linux 4 trial, and it doesn't show up in the add/remove listings.  Any ideas?

---

### Post by MelDJ on 2009-10-25
try finding for nero in synaptic and you will find the package. then mark it for complete removal

---

### Post by lightningrod66 on 2009-10-25
> **MelDJ said:**
> try finding for nero in synaptic and you will find the package. then mark it for complete removal

Thanks!  That did it, then i was able to install my previous version that is .deb file.

---

### Post by sleepitoff on 2009-10-25
Why do you want to use Nero in the first place on Ubuntu?

---

### Post by psycho5 on 2009-10-25
> **sleepitoff said:**
> Why do you want to use Nero in the first place on Ubuntu?

I was going to ask the exact same question. you should try Brasero takes care of all my burning needs, you could also try Gnome Baker.

---

### Post by MelDJ on 2009-10-25
> **psycho5 said:**
> I was going to ask the exact same question. you should try Brasero takes care of all my burning needs, you could also try Gnome Baker.

different people have different needs and likes :)

---

### Post by lightningrod66 on 2009-10-25
> **sleepitoff said:**
> Why do you want to use Nero in the first place on Ubuntu?

Cause i tried brasero and it don't work with my burner.  I installed nero cause I used it with windows and it works fine on ubuntu.

---

