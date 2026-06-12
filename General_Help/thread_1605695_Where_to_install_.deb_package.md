---
title: "Where to install .deb package"
date: 2010-10-25
forum: General Help
---

### Post by ianc1 on 2010-10-25
Hi all

A real beginners question here.  Whilst I can manage the software centre and synaptic fine and add repositories etc I am at a loss as to what to do with a deb.  I have downloaded Komodo Edit 5 software I am familiar with from work and like.

Its default on installation is to make a Komodo folder in my Home folder which I don' like.  Am I correct in thinking that usr/local is the recommended location in the file system in which I should install downloaded packages such as this?  During use I will want to change preferences in files etc from within the program, would this location restrict me from doing this without sudo.

Is there a better place to install this?

Any suggestions would be great

Ian

---

### Post by lindsay7 on 2010-10-25
Download GDebi from synaptic. Once it is installed all you have to do is click on the deb package to install it.

---

### Post by themusicalduck on 2010-10-25
If you have a .deb file that you want to install, you should only have to double click it. It'll then either open with Software Centre or Gdebi depending on which version of Ubuntu you are on.

Then just click install and it will hopefully do everything else.

---

### Post by AlphaLexman on 2010-10-25
Did you use:
```
dpkg -i package-name.deb
```
to install the program?

Else: 
```
/usr/bin/
```
or:
```
/usr/local/bin/
```

---

### Post by GlazedWicker on 2010-10-25
I'm sure the Komodo folder in your home directory is just for project files and such things. The actual program executables will most likely be installed in /usr/bin or /usr/local/bin.

---

### Post by btindie on 2010-10-25
If it's a binary deb package then it will install to where ever it's been configured to. You can view the contents of the deb file with
```
dpkg-dep -c <filename.deb>
```then to install it use
```
sudo dpkg -i <filename.deb>
```

---

### Post by ianc1 on 2010-10-25
Wow, lightening fast responses.  Thanks everyone, I'll try the Gdebi route and reinstall it again tomorrow.  I had assumed the Komodo directory in the Home folder was in fact the program directory but as pointed out this could have been for my use.  Rather dimly I did not look at contents but uninstalled assuming I'd done something wrong.

---

### Post by ianc1 on 2010-10-25
My error its a tar.gz and I've looked at the install info again I believe I did it correctly and the package was installed to Home/Komodo.

If I put this in usr/local/bin will I be able to edit the program preferences due to sudo access restriction?

Thanks

---

### Post by AlphaLexman on 2010-10-25
Is it a source code program? 
```
ls ~/Komodo
```
Post the result.

---

### Post by ianc1 on 2010-10-25
Thanks AphaLexman, that's what I thought was usual for tar.gz installs but I've just looked at the files contents and it appears to be a directory structure consisting of bin, lib and share and I think the bin actually contains the program files.
[FONT=Verdana]
It has an install.sh script, which contains [/FONT]```
# To install Komodo, run:
[FONT=Verdana]#   ./install.sh
# To see additional install options, run:
#   ./install.sh -h

dname=`dirname $0`
LD_LIBRARY_PATH="$dname/INSTALLDIR/lib/mozilla:"$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
$dname/INSTALLDIR/lib/python/bin/python -E $dname/support/_install.py "$@"[/FONT]
```[FONT=Verdana]
[/FONT]I can't reply with a directory list of Komodo as I've deleted it from my HOME folder as I was unhappy with the location.

Cheers

---

### Post by Rasa1111 on 2010-10-25
in Ubuntu 10.10, 
if you dont have Gdebi, 
You can right click the .deb file, and choose to "open in software center". 
That will install it where it needs to go. 

 I do like to have Gdebi to though.

---

### Post by AlphaLexman on 2010-10-25
If a download IS source code, you will have to 'compile' the source to 'binary'. If the bin directory has executables, try:
```
xdg-open komodo
```...in the bin dir (of course)
Or whatever the filename may be.

---

### Post by ianc1 on 2010-10-27
Thanks everyone, all installed and in working order in /usr/bin/local.  Obviously had to run the install script with sudo but it seems relatively benign.  I love this editor, whilst a little bulky for many jobs its great for programming better than anything I've found in the repository.  I wish it would appear in the Ubuntu repository.

Cheers

Ian

---

