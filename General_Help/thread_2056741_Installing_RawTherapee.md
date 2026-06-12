---
title: "Installing RawTherapee"
date: 2012-09-12
forum: General Help
---

### Post by rbscairns on 2012-09-12
I want to install RawTherapee in Ubuntu 12.04. Ubuntu SoftwareCenter only has version 3.0.0 so I downloaded version 4.0.9.1 from the RawTherapee site.

After downloading the zip file, I extracted the files into my Downloads folder. I now have eight folders; dcpprofiles, iccprofiles, images, languages, profiles, share, sounds, and themes. I also have six files; AboutThisBuild.txt, AUTHORS.txt, LICENSE.txt, options, rawtherapee, and RELEASE_NOTES.txt.

From this point, how do I go about installing RawTherapee 4.0.9.1 on my Ubuntu 12.04 system (preferably using the GUI)?

---

### Post by mcduck on 2012-09-12
Based on the contents, there is nothing you need to do to install it. It's already ready to run, just make sure the "rawtherapee" file has execute permission and then run it.

---

### Post by rbscairns on 2012-09-12
Thank you McDuck, but still no joy.

The rawtherpee file is set to "Allow exectuting file as program" in Propeties>Permissions. When I click (or double click) on the rawtherapee file icon I get nothing.

What am I missing?

---

### Post by jerrrys on 2012-09-12
Have you tried to open it in terminal?

---

### Post by rbscairns on 2012-09-13
> **jerrrys said:**
> Have you tried to open it in terminal?
No I have not. I do not know how to open a programin terminal.

---

### Post by jerrrys on 2012-09-13
> **rbscairns said:**
> No I have not. I do not know how to open a programin terminal.

Just open a terminal

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

and enter

rawtherapee

That should do it or atleast give you an error message

---

### Post by rbscairns on 2012-09-13
I go into terminal and enter rawtherapee. the following result is displayed:

> The program 'rawtherapee' is currently not installed.  You can install it by typing:
sudo apt-get install rawtherapee

If I then type "sudo apt-get install rawtherapee". rawtherapee version 3.0.0 is installed, not the version 4.0.9.1 that I downloaded and want to use. I then removed the installed version 3.0.0.

The attachment shows where I have saved rawtherapee version 4.0.9.1.

---

### Post by mcduck on 2012-09-14
You need to move in the directory where you extracted the program, and then run "./rawtherapee" there.

```
cd ~/Downloads/rawtherapee
./rawtherapee
```

If that works you can then create a launcher for it to make it appear in the Dash (or any other menu you might be using top launch your programs). The easiest way to do that is to use the Alacarte Menu Editor. If you are happy with hand-editing configuration files you can of course also just copy any of the existi ng .desktop files in /usr/share/applications and then rename it and edit the contents to point to your program.

Also, if you create a symbolic link for the executable file in ~/bin you'll be able to run the program without having to move to it's directory first, just like if it was installed from Ubuntu's repositories. You might want to uninstall the repository version of the program first, though.

---

### Post by rbscairns on 2012-09-17
Thank you McDuck for putting up with my troubles. Sorry for the slow replies as I do not have 24/7 internet access.

The results so far:

> richard@NSDCeb2:~$ cd ~/Downloads/rawtherapee
richard@NSDCeb2:~/Downloads/rawtherapee$ ./rawtherapee
./rawtherapee: error while loading shared libraries: libiptcdata.so.0: cannot open shared object file: No such file or directory
richard@NSDCeb2:~/Downloads/rawtherapee$ 

I then went to Accessories>Files and did a search for libiptcdata.so.0. Nothing can be found. How do I find this file?

BTW, I remember from my DOS days that cd = change directory, but what does the "~" mean?

---

### Post by Rodney9 on 2012-09-17
You could use the ppa nightly builds -

[https://launchpad.net/~rawtherapee/+archive/nightly](https://launchpad.net/~rawtherapee/+archive/nightly)


Rodney

---

### Post by rbscairns on 2012-09-25
It took some learning for me (good) and I was able to install Rawtherapee ver. 4.0.9 from the ppa nightly builds.

---

### Post by ianp5a on 2013-04-06
Thanks for the PPA tip. That is the solution.  That zip file download is useless.
The RawTherapee site gives no help on installing. They put a lot of effort into the latest version of RawTherapee yet make it almost impossible to install.
Note the nightly build is 4.0.9 and the zip download is 4.0.10.

---

### Post by ianp5a on 2013-04-07
This PPA:   [http://ppa.launchpad.net/dhor/myway/ubuntu](http://ppa.launchpad.net/dhor/myway/ubuntu)   gets the latest Rawtherapee 4.0.10.
Remove the other PPA and uninstall Rawtherapee first. Add the new PPA. Update software then re install Rawtherapee from the Software manager.

I discovered it when I wanted to add **Macrofusion**.

---

### Post by clrpaolo on 2013-11-28
Hi there, i have exactly the same problem to download Rawtherapee 4. I have Ubuntu 12.04 64 bit. I downloaded the file from the Rawtherapee website but doesn't work. I have already uninstalled the previous version of Rawtherapee. I have clicked on the link to the PPA on your last post, but don't know how to proceed after that. How do i install the PPA and then Rawtherapee 4? Probably my question is so stupid, I'm very new to ubuntu and linux, sorry.

---

