---
title: "No Command 'mycommand' Found?"
date: 2011-02-16
forum: General Help
---

### Post by Michael_Grumbach on 2011-02-16
I just installed Ubuntu using the Windows Installer.
I am trying to run an executable in a command window, and I get the message:
"No Command 'mycommand' found, did you mean: ..."

I typed $> mycommand <various flags, et al>

I ran an executable just before this, but proceeded by "./"
so I tried that, and received the following message:
"bash: ./: is a directory"

So I'm not sure why the 'mycommand' executable is not recognized.
I'm in the same directory as the .exe file.
I know it works, but it's not even recognized.

Any suggestions would be appreciated.

Thank you,
Mike

---

### Post by pl@yer on 2011-02-16
Linux does not include your current location in the file system (./) in the $PATH variable by default. So in order to run something from you current location you would include the relative path ./ or the full path to the file.

.exe usually means w32 executable. In other words an executable compiled to run under windows.

What are you trying to do?

---

### Post by gobbledigook on 2011-02-16
> **Michael_Grumbach said:**
> I am trying to run an executable in a command window, 

ubuntu doesn't run .exe files... directly, if it is a program that is only available in windows you may be able to run it under [WINE]("http://www.winehq.org/") this can be installed through a package manager (see below) and may or may not be able to load your program.... there is a compatibility list on their site :)

if you go to applications > add/remove it will open a package manager this lets you search through 1000's of free open source applications to install. more info on installing packages can be [found here]("https://help.ubuntu.com/community/InstallingSoftware")

---

### Post by Michael_Grumbach on 2011-02-16
Thanks.
I'm installing a reprise server.
The Unix/Linux Installation instructions direct me to type $> rlm -ws...
Maybe I need to go to the reprise website and find the correct executable?

---

### Post by Michael_Grumbach on 2011-02-16
And I was running this from the same dir where the command file is located.

---

### Post by Michael_Grumbach on 2011-02-16
This is supposed to be run on a unix/linux system

---

### Post by gobbledigook on 2011-02-16
> **Michael_Grumbach said:**
> This is supposed to be run on a unix/linux system

then i would be asking reprise for a .deb not a .exe

---

### Post by Michael_Grumbach on 2011-02-16
I just check the file extention.
It is not a .exe file.

---

### Post by Monotoko on 2011-02-16
then what is it? You may also need to modify the file so it has executable permissions with:

```
chmod -x ./file
```

---

### Post by Michael_Grumbach on 2011-02-16
I looked at in in a windows explorer window, and the extension wasn't visible.
I believe it's the right file.
I'm confident in the source.

I'll try the permissions suggestion.

---

### Post by stillnotelf on 2011-02-16
It is not clear to me that you tried "./mycommand".  The "./ is a directory" message indicates to me that you may have tried "./ mycommand" (notice the space).  Give "./mycommand" a shot...

In the long term, you'll want to add . (the current directory) to your $PATH variable if you don't like typing ./ all the time (I certainly don't...)

---

### Post by Monotoko on 2011-02-16
If that doesn't work, PM me and attach a zipped up version of what you are trying to install. I will take a look :)

---

### Post by smurphy_it on 2011-02-16
could try posting the directory contents so we can see what file it is, which would provide the file permissions and file type.

ls -l

Additionally, in windows, if you are looking at the file, and it doesn't display the "extension", then it is hiding extensions for known file types.  You would have to edit the Window Explorer preferences, and turn that check-box off.  Alternatively, to get the file extension, you can navigate to the folder in DOS / Command-line and do a dir.  That should give the full file name including the extension.

---

### Post by Michael_Grumbach on 2011-02-16
The issue was that the permissions were not set properly.
So I'm running now.

Thank you very much

---

