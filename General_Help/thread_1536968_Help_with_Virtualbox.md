---
title: "Help with Virtualbox"
date: 2010-07-22
forum: General Help
---

### Post by jroa on 2010-07-22
I am new to Linux and I have a software problem that I hope I can get some help with.  I used Virtualbox to install Windows Server 2003 and everything went well.  I then had the bright idea to see how Vista would do on it.  During the installation of Vista, I ran out of disk space and the install paused.  I did not want to resize Vista from Linux, so I did a hard shutdown so I could boot into Vista to free up space, and when I got the partitiians straightened out and went back into Ubuntu, Virtualbox would not load.  I unistalled it and reinstalled several times.  I can get it to work from another account, but from mine, I get the following error box.  I can't seem to figure out how to fix this.  Any help would be greatly appreciated.

[IMG]http://i739.photobucket.com/albums/xx38/jorroa5990/Screenshot.png[/IMG]

---

### Post by DarthScape on 2010-07-22
Possibly try moving ~/.VirtualBox/VirtualBox.xml and VirtualBox.xml-prev to the trash. Make sure virtualbox is quit out. You will lose the settings for the virtual machine, but you can setup another one using the same Virtual hard drive you had before. If that doesn't work I would just restore the files.

or you could try editing the xml file, but that may be a bit of a pain

---

### Post by Ocxic on 2010-07-22
yep, do that --^

---

### Post by munkyeetr on 2010-07-22
It looks like there's a syntax error in ~/.VirtualBox/VirtualBox.xml. Did you try opening the file in a text editor and seeing if the opening tag (the culprit from the looks of the error message) is missing its '<' character. Look through all the tags xml if the first one is okay, to hunt down the offending tag.

That's what I'd try anyway.

---

### Post by jroa on 2010-07-22
Thanks for the help guys.  I am really used to Windows and DOS, so I am having a hard time even finding ~/.VirtualBox/VirtualBox.xml.  I have done a search for it and it came up with nothing and the few commands that I know brought up nothing either.  I would like to try to view it in a text editor, and possibly delete the files, but I just can't seem to find it.

You guys are great and thanks for the quick responses.  I hope I can learn enough to help someone out one day.

---

### Post by watupgroupie on 2010-07-22
The "~" sign represents your home folder. So go there, and then the period before the name of the folder makes it hidden by default. To view these folders hit ctrl+h. You should be able to find it then :)

---

### Post by DarthScape on 2010-07-22
Click on Places at the top of the screen, then click on your home folder. Next, click on Go at the top of that window. Then go down to Location. It will bring up a text field, type ~/.VirtualBox . In there should be the files we are looking for. Highlight, right-click, and move to trash VirtualBox.xml and VirtualBox.xml-prev

Otherwise, you can right-click the files, open with gedit, and try adding the "<" yourself.

---

### Post by jroa on 2010-07-23
munkyeetr, I tried opening the file in a text editor and it was blank.  I have no idea how I screwed the file up.

DarthScape, I deleted the file like you said and it looks like it did the trick.  I don't care that I lost anything.  I am experimenting more than anything.

watupgroupie, that is exactly what I needed to know.  I hope I remember this.

Thanks for everyones help.  I think I can take it from here until I screw it up again.;)

---

### Post by cybertriveni on 2010-07-23
unstall virtual box,reinstall it..........install os again again again.........



> **jroa said:**
> I am new to Linux and I have a software problem that I hope I can get some help with.  I used Virtualbox to install Windows Server 2003 and everything went well.  I then had the bright idea to see how Vista would do on it.  During the installation of Vista, I ran out of disk space and the install paused.  I did not want to resize Vista from Linux, so I did a hard shutdown so I could boot into Vista to free up space, and when I got the partitiians straightened out and went back into Ubuntu, Virtualbox would not load.  I unistalled it and reinstalled several times.  I can get it to work from another account, but from mine, I get the following error box.  I can't seem to figure out how to fix this.  Any help would be greatly appreciated.

[IMG]http://i739.photobucket.com/albums/xx38/jorroa5990/Screenshot.png[/IMG]

---

