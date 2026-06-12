---
title: "how to create a path statement"
date: 2011-08-07
forum: General Help
---

### Post by BushyIII on 2011-08-07
I have multiple drives and software that defaults to my primary drive.  I want to change preferences to use my second drive.  Obviously I'm a noob.

This is the current path "/home/guy/dvdrip-data"
my second drive is named "2Internal"

How do I properly format the path statement to use the second drive?

---

### Post by bodhi.zazen on 2011-08-07
You can use any path you wish

```
mkdir /path/you/want
sudo mount /dev/your_driver /your/path
```

If you mount it outside your home you will need to use sudo.

See also : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by BushyIII on 2011-08-07
> **bodhi.zazen said:**
> You can use any path you wish

```
mkdir /path/you/want
sudo mount /dev/your_driver /your/path
```If you mount it outside your home you will need to use sudo.

See also : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

My second drive had been mounted and still is, I can readily open it and  view its files and directories.  The problem is adding the path to a  particular piece of software.  I want to change the software current  path of "/home/guy/dvdrip-data" to a new path on my second drive named  "2Internal".  I have tried all the following without any success.  "/2Internal/dvdrip-data",  "/2Internal/Movies/dvdrip-data",   "/home/guy/2Internal/dvdrip-data".  
 
 I know the paths I have tried failed because the software immediately  highlights the path in RED and states "Can't create directory:  /2Internal/Movies/dvdrip-data
 
 Am I doing it wrong or is the software hardwired to only use  "/home/guy/dvdrip-data" ?

---

### Post by AlphaLexman on 2011-08-07
> **BushyIII said:**
> Am I doing it wrong or is the software hardwired to only use  "/home/guy/dvdrip-data" ?
No, we can fix it!

You should have a hidden file named '**/home/guy/.dvdriprc**'

Using your favorite text editor, it might be about 400 lines down, look for the following...
```
  'config' => {
    'base_project_dir' => {
      'value' => '[COLOR="Red"]/home/guy/dvdrip-data[/COLOR]',
      'type' => 'dir',
      'label' => 'Default data base directory'
    },
```
And change the path to your liking. Save and restart dvd-rip.

---

### Post by BushyIII on 2011-08-07
Sounds good I'll give it a try.  What do I need to do to expose hidden files?

---

### Post by AlphaLexman on 2011-08-07
> **BushyIII said:**
> What do I need to do to expose hidden files?
<Ctrl-h> Will show hidden files in Nautilus, and it will show hidden files in the 'gedit -> file -> open' dialog box.

---

### Post by BushyIII on 2011-08-07
Thanks for your help!

---

### Post by BushyIII on 2011-08-07
The file doesn't exist.  I did the CTRL-H to display hidden and searched everywhere including the entire file system.  It isn't there.

---

