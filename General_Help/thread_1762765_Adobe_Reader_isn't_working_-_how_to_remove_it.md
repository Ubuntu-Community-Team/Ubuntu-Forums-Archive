---
title: "Adobe Reader isn't working - how to remove it?"
date: 2011-05-19
forum: General Help
---

### Post by lilaliv on 2011-05-19
Hey folks,

I'm pretty new to Ubuntu and I really need your help cause I simply don't  know how to get rid off the Adobe Acrobat Reader.

Since I couldn't find it with the synaptic package manager, I  downloaded the file "AdbeRdr9.4.2-1_i486linux_deu.bin" and installed it  manually in the terminal. Well, it doesn't work. At all. I can open it,  but that's it. It won't show me any menu (it's all gray), and whenever I  try to print something, I get an error code. So I'd really like to  remove it.

The thing is that I don't know how. I've tried so many different  commands by now, it's tiring. I'm pretty sure that when I installed it,  it was called "acroread", when I ask the terminal where it is, it tells  me "usr/bin/acroread", but when I try to remove it, it can't find it.

"sudo apt-get remove acroread" didn't work. I've read that the package name might be incorrect and instead be "adobereader-enu" - that failed, too. Then I've read there was an uninstall file in the adobe folder - but I don't know how to find/open that. "cd <name_of_install_directory/Adobe/Reader9/bin && sudo ./UNINSTALL" didn't work, either - or maybe I just don't use this command correctly, I don't know. Last thing I read was to just delete the folders - which I'm a little afraid of. Never was a good idea with Windows, either.

What do I do?
Thanks in advance.

---

### Post by ianc1 on 2011-05-19
I don't use it myself but as far as I can tell if you go to Ubuntu Software Centre under Get Software>Canonical Partners there is an option for Adobe Reader 9 called "Use This Source".  If you installed it I imagine there will be an option there to remove it.

---

### Post by ivanovnegro on 2011-05-19
Welcome to the forums.
Could you say how you downloaded the program exactly and from which site. Did you install it for sure?
Adobe is normally installable from the repositories, no need to go to the web and it works like in Windows but the preinstalled document viewer is really faster, Evince.

---

### Post by r-senior on 2011-05-19
If it was installed from a .bin file it's a matter of finding that UNINSTALL file. Best guess to start with would be under /usr/local somewhere. Failing that, search the whole of /usr.

You can search with Nautilus (file manager), or if you are OK with the terminal:

```

cd /usr/local
find -name UNINSTALL

```

If that doesn't find it:

```

cd /usr
find -name UNINSTALL

```

---

### Post by lilaliv on 2011-05-19
ianc1: Thanks, but it didn't (really) work. When I had installed it the way you suggested, it's been there twice, but both didn't work ;) and now that I've removed it, one of them is still there, it's just not working at all now (i.e. if I double-click on a pdf file, there's absolutely nothing happening anymore)... this is driving me crazy.

---

ivanovnegro: uh... guess it's been the Adobe website? But I'm not sure. And yes, it (now was?) installed, I could open it, it showed the documents, it just didn't work properly. I didn't know of the software-center-partners-thing, that might have been a better idea...

---

rsenior: I can't find it. I've opened my user file, then ".adobe/Acrobat/9.0", there's nothing in there that looks like an unsinstall file. I have 

/Cache
/Cert
/Collab
/Forms
/JavaScripts
/Preferences
/Synchronizer

and the following files:

AdobeCMapFnt09.lst
SharedDataEvents
UserCache.bin

Or am I in the wrong directory?

---

### Post by lilaliv on 2011-05-19
OK, I've found the directory and I found the UNINSTALL file - except it doesn't do anything. Nothing happens if I double-click on it, whether I choose to just run it or to run it in the terminal...*

I've re-installed and removed everything I can, it won't help. I can't even just delete the Adobe file in /opt, let alone all the shortcuts... is there any way to just get rid off what's left? I'm somewhat getting annoyed...

Please help! :(

* well, the terminal opens for about half a second, then it closes again. I can't even see what it says.

---

### Post by r-senior on 2011-05-19
Try launching a terminal separately (with Ctrl-Alt-T), then go to the directory where the UNINSTALL file is and run it, e.g.

```

cd /opt/something
./UNINSTALL

```

If it fails, post the output.

---

### Post by lilaliv on 2011-05-19
This is what I did:

```
cd /opt/Adobe/Reader9/bin
./UNINSTALL
```This is the error code:

```
cd: 336: can't cd to /opt/Adobe/Reader9/Reader/intellinux/bin

```I don't know why it changes the directory... it doesn't even exist.

---

### Post by r-senior on 2011-05-19
OK, the installer doesn't work! ;)

I'm just downloading the .bin file and see if I can make any sense of it. Bear with me.

---

### Post by crashed111 on 2011-05-19
Looks like it never installed correctly. Did you install it originally as super user (sudo)? If you did not then the install may have failed if the script tried to do it without checking if you were root first leaving you with a half complete install. 

Linux unlike Windows makes removal of most programs easy to do by hand (No registry) the only time you get problems if with programs like VMWare which like to play with the Kernel.

If the script is failing you can open it with a text editor run it line by line using copy and paste as root and not worry about the command that fail. If you are not familiar with the shell if the script is not too long you could post it here and we could take a look. 

This should not be affecting your system as a whole however so do not worry and you should still be able to view pdfs using the standard Linux tool.

---

### Post by lilaliv on 2011-05-19
I'm pretty sure I installed it as sudo. But it wasn't working from the  very beginning. The menu was kind of 'blank', i.e. it was there but I  couldn't read anything, it was just gray. And printing didn't work,  either. I've always liked Adobe's functions for the printing, that's why  I wanted to install it in the first place.

I've opened that file in a text editor, this is what it says (since all  that stuff in that file is in my mother tongue (that you're probably not  speaking) I'll just loosely translate it to you):

```
set_lang_DEU_utf()
{
    ST_ER_AR02="Error: Current installation directory cannot be found."
    ST_ER_SAME_FILE_NAME_AS_DIR="%s is existing, but not a directory. Specify another directory."
    ST_UNINSTALL_SUCCESS="Adobe Reader has been removed from your system."
}

        
set_lang_DEU()
{
    ST_ER_AR02="Error: Current installation directory cannot be found."
    ST_ER_SAME_FILE_NAME_AS_DIR="%s is existing, but not a directory. Specify another directory."
    ST_UNINSTALL_SUCCESS="Adobe Reader has been removed from your system."
}
```

... which is a big, fat lie :-s

---

### Post by r-senior on 2011-05-20
I've not had that much time to look at this today but I did load up a virtual machine running 11.04 and tried to run the .bin file downloaded from the Adobe website. I didn't even get as far as you did. Nothing at all. Just failed silently.

Given that /opt is not a standard directory in an Ubuntu installation, you should be safe to just delete the /opt/Adobe directory if it exists because it must have been created by that failed install:

If you aren't sure, post a directory listing. Otherwise, in a terminal,:

```

cd /opt
sudo rm -rf Adobe

```

As far as local configuration files are concerned, there may well not be any. Or there may be, but they'll be small. You could just pretend there aren't but if you are curious, try things like:

```

cd
find -name '*[Aa]dobe*'

```

This finds anything under your home directory called 'adobe' or 'Adobe'.

Personally I'd just leave them. If I run the above, even though I've never installed Adobe reader, I do have hidden directories under my home folder for the browser flash plugin.

If you are having problems with opening .pdf files, post back.

Hopefully no damage done, but a lesson to all to stick with software from the repositories or PPAs.

---

### Post by linuxinstalledfromhdd on 2011-05-20
I'm an old timer with Ubuntu, and I still use a do-to list when I do a fresh install of Ubuntu. 

And yes, it will install Acrobat Reader successfully too.

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by lilaliv on 2011-05-23
r-senior:
Thanks for all your help! The folder is gone now even though all the shortcuts are still there, but I will just try and ignore them, so I don't mess things up again. True - I will probably never try that again... lesson learned ;)


linuxinstalledfromhdd:
Thank you, too. I don't have the time to read through this now, but I've set up a bookmark and will have a look at it later.


If I ever find a 'real' solution to the problem or all the shortcuts suddenly disappear on their own, I'll tell.

---

### Post by a280931 on 2011-11-11
This worked for me.
sudo apt-get purge adobereader-enu



> **lilaliv said:**
> Hey folks,

I'm pretty new to Ubuntu and I really need your help cause I simply don't  know how to get rid off the Adobe Acrobat Reader.

Since I couldn't find it with the synaptic package manager, I  downloaded the file "AdbeRdr9.4.2-1_i486linux_deu.bin" and installed it  manually in the terminal. Well, it doesn't work. At all. I can open it,  but that's it. It won't show me any menu (it's all gray), and whenever I  try to print something, I get an error code. So I'd really like to  remove it.

The thing is that I don't know how. I've tried so many different  commands by now, it's tiring. I'm pretty sure that when I installed it,  it was called "acroread", when I ask the terminal where it is, it tells  me "usr/bin/acroread", but when I try to remove it, it can't find it.

"sudo apt-get remove acroread" didn't work. I've read that the package name might be incorrect and instead be "adobereader-enu" - that failed, too. Then I've read there was an uninstall file in the adobe folder - but I don't know how to find/open that. "cd <name_of_install_directory/Adobe/Reader9/bin && sudo ./UNINSTALL" didn't work, either - or maybe I just don't use this command correctly, I don't know. Last thing I read was to just delete the folders - which I'm a little afraid of. Never was a good idea with Windows, either.

What do I do?
Thanks in advance.

---

### Post by macsathish on 2012-06-07
i downloaded .deb pkg but i had the same problem but now i uninstalled successfully  it worked for me too thanks!!!!!!!!!!!! a280931

---

### Post by adriancarrara on 2012-10-09
For Ubuntu 12.04 I found this directions useful to install Adobe Reader:

[http://www.techheadz.co.uk/222.html](http://www.techheadz.co.uk/222.html)

---

### Post by annbo812 on 2013-06-07
hi people, i am struggling with the similar problem.

apt-get purge has failed to find the package:

admini:~$ sudo apt-get -s purge acroread
[sudo] password for ademi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not installed, so not removed



This is what i tried:

@admini:~$ sudo apt-get -s purge adobereader-enu

and 

@admini:~$ sudo apt-get -s purge adobereader-bin


And this is what Ive got:

E: Unable to locate package adobereader-bin



And this is how I installed it:

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner" 
sudo apt-get update
sudo apt-get install acroread

What do I do next?  :confused:

[INDENT] [/INDENT]

---

### Post by localhost8080 on 2013-06-07
> **annbo812 said:**
> 

And this is how I installed it:

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner" 
sudo apt-get update
sudo apt-get install acroread

What do I do next?  :confused:

[INDENT] [/INDENT]


sudo dpkg --get-selections | grep acro

or

sudo dpkg --get-selections | grep adobe

should list the acrobat and adobe packages you have.
once you get a list you can
sudo apt-get --purge remove whatever
to get rid of it :)

---

### Post by annbo812 on 2013-06-12
Thank you for your suggestion. Unfortunately, the problem remains unresolved. 

As before with dpkg i can find only one package - cmap-adobe-japan2, which seems to have nothing to do with the pdf-viewer. So I still do not know the name of the adobe package, that I have installed and so am not able to remove it.

Please, help me to find this beast.

---

### Post by ealbin on 2013-09-03
Hi,
Acroread 9 worked perfectly even with animations in pdf under 12.04 but was no more working after an upgrade to ubuntu 13.04...
I could not uninstall it completely from the "Ubuntu Software Center". I mean that Adobe Acrobat could still be started after removing the package "acroread". Thanks to localhost8080 and his great command "sudo dpkg --get-selections | grep acro", I noticed that I had also a package called "acroread-bin" to uninstall in the Ubuntu Software Center.
Now, I could reinstall it under 13.04 and it works perfectly again :-)

---

