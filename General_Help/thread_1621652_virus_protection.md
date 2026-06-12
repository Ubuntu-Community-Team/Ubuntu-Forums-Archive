---
title: "virus protection?"
date: 2010-11-14
forum: General Help
---

### Post by dante19992 on 2010-11-14
being used to the pc i have always used resource draining virus protection programs. now that i have switched to ubuntu 10.10 i wanna kno is there rly any need for virus protection on my linux?

---

### Post by marin123 on 2010-11-14
[http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed](http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed)

---

### Post by Frogs Hair on 2010-11-14
Unless you are worried about sending a Windows virus to someone I would not worry about. If you feel the need Avast makes a free Linux edition.

I used to have Clam AV , but it only scans for Windows Viruses that can't run on Ubuntu anyway.

---

### Post by dante19992 on 2010-11-14
well what about with Wine? isnt it a layer that translates windows files to a language ubuntu understands? would installing this make it necessary?

---

### Post by hakermania on 2010-11-14
yep, but it will destroy the wine's folders not yours.... (inside your home folder there is a .wine folder and there wine placed Program Files etc...)

---

### Post by matt_symes on 2010-11-14
Hi,

> well what about with Wine? isnt it a layer that translates windows files  to a language ubuntu understands? would installing this make it  necessary?

Thats true, but even wine is contained by the security polices of Linux. It could only trash your home directory.

Kind regards.

---

### Post by dante19992 on 2010-11-14
ok so basically if sumtin happens i just uninstall wine and delete the folder then reinstall it?

---

### Post by matt_symes on 2010-11-14
Hi,

Run it as a low privilege user and limit wine to the c_drive folder in the configuration window and it should be contained just there.

It does  not have root privileges it could not do any major damage to the entire  system. 
   
Only root has superuser privileges and only sudoers referenced in the  sodoers file can gain access to root privileges.
All the programs you install in wine live in your home directory in the hidden .wine folder.

So yes, you could just delete that folder, uninstall wine and start again.

Linux makes it hard to get viruses. 

Kind regards

---

### Post by ivarn on 2010-11-14
The only way you can get viruses in wine is if you use internet explorer 
You will probably use wine for games and apps you can't get for linux, right?
So the chances are very minimal, and to get a virus inside your wine folder you must place it there on your own. Also, most viruses attack the registry, not the file system.

---

### Post by matt_symes on 2010-11-14
Hi

May i ask why you want to use wine? There are open source alternatives to almost all windows applications.

[http://www.osalt.com/](http://www.osalt.com/) will recommend open source alternatives for windows programs.

Running windows programs under wine in Ubuntu kind of defeats the purpose of using Ubuntu. Not all windows programs work under wine anyway.

Of course your other options are to install windows in a virtual machine under Ubuntu or to dual boot.

Kind regards.

---

### Post by 3Miro on 2010-11-14
Wine is mostly for games. Legitimate CDs with games don't contain viruses, so unless you download and install "funny programs" you don't have to worry about viruses in wine. Most viruses don't work under wine anyway.

If you get a virus in your home folder, you should just delete the folder, you don't even have to reinstall all of wine.

---

### Post by matt_symes on 2010-11-14
Hi

> Wine is mostly for games

Not being a gamer myself, i'm sure that is a valid point.

Kind regards

---

### Post by dante19992 on 2010-11-14
well i am a huge gamer i mainly use wine for perfect world and other online games that dont have a linux version. and i cant use an alternative because all of the linux mmorpg's SUCK. i was mainly worried cuz i also intended to run lunascape 6 throught wine cuz firefox and opera also arent that great

---

### Post by matt_symes on 2010-11-14
Hi

Well good luck with the gaming :) My advice is try to use wine only when necessary though.

If your questions have been answer mark this thread as solved.

Kind regards

---

### Post by SeijiSensei on 2010-11-14
If you install Wine and other Windows programs, after you've gotten everything the way you like, make a backup snapshot of the installation like this:

```

# go to your home directory
cd ~
# create a compressed "tarball" of the .wine directory
tar cjpf wine.tar.bz2 .wine 

```

If something goes wrong you can revert to this saved image by running 

```

cd ~
# save the corrupted installation in case you need something there
mv -f .wine .wine.bad
# recreate Wine
tar xjf wine.tar.bz2

```

Then you'll be back where you started.  If you need a file in the old installation it will be in ~/.wine.bad/.  (You don't need to type in the lines that begin with "#"; they're just comments to explain what the commands below them do.)

wine.tar.bz2 could be fairly large so you should make sure you have enough disk space.  Because the image is compressed, it won't be as large as .wine itself, but it may only compress to 50-70% of the .wine directory's size because that largely contains compact binary files.  You can measure the size of the entire Wine installation by running:

```

cd ~
du -s .wine

```

which will report the size of the installation in megabytes.  Make sure you have enough free space to accommodate at least 80% of the uncompressed size of .wine.

---

### Post by Bitrate on 2010-11-14
> **3Miro said:**
> Wine is mostly for games

It sure as hell is not.

I use Wine/Crossover Pro to run the following Windows Applications:

Forte Agent
VideoRedo
Microsoft Office 2003 Professional
WinAVI
Internet Explorer 7.0

Yes, there are FOSS alternatives for these programs but they are inferior (except for Firefox beating IE). Wine/Crossover runs all these apps very well.

---

