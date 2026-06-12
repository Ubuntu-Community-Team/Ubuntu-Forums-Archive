---
title: "problems with download"
date: 2010-05-27
forum: General Help
---

### Post by riverwhy on 2010-05-27
i'm trying to download software (linux citrix client) from this link so i can connect remotely to the server at my work place.
[FONT=Calibri][SIZE=2][/SIZE][/FONT][FONT=Calibri][SIZE=2][http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755)[/SIZE][/FONT]

when i go to the link there is a choice of 5 downloads, but i'm assuming they are all the same thing (?) On each one it says x86 client requires either OpenMotif v.2.3.1 or OpenMotif v 2.2.3.  I'm not sure what that is, nor where i get it. 
But..  Ignoring that for the moment when i click on download i get the usual choice to open or save the file. However the only program in the options list for opening the file is archive manager..  If i click on "other"i just get a list of files and folders on the laptop. If i do try to open with archive manager (the default & only suggestion in the drop down list) it says it can't do it because the associated helper file (?) does not exist. I suspect that's irrelevant though because i'm sure i don't want to open it with AM anyway (?).

how do i download this file?

running ubuntu 10.4 LTS

sorry for all the questions.. windows was never like this!!

---

### Post by jerrrys on 2010-05-27
Ubuntu uses **.deb**, use one of those two choices

---

### Post by riverwhy on 2010-05-27
brilliant! thanks - download successful.. only thing is.. now i can't find where to run it! It has put a "citrix receiver" icon in favorites, but when i open it it says "opening citrix receiver" but actually does nothing at all..  ??

sorry again.. linux newbie!

---

### Post by jerrrys on 2010-05-27
don't know, this may help

[http://www.google.com/search?client=ubuntu&channel=fs&q=openmotif+v.2.3.1&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=openmotif+v.2.3.1&ie=utf-8&oe=utf-8)

---

### Post by jerrrys on 2010-05-27
and this

[http://www.google.com/search?hl=en&q=openmotif+2.3+1+ubuntu&revid=1540802376&ei=3kz-S631IoO4NfyD0Ts&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=4&ved=0CFIQ1QIoAw](http://www.google.com/search?hl=en&q=openmotif+2.3+1+ubuntu&revid=1540802376&ei=3kz-S631IoO4NfyD0Ts&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=4&ved=0CFIQ1QIoAw)

---

### Post by riverwhy on 2010-05-27
further to the above. i thought i would reinstall the package to see if it told me where it had put it..  it didn't..  i then went into "internet" (the citrix icon was here, not as previously stated, in favorites) and clicked  on the icon. The icon then disappeared???

come back Bill Gates???

---

### Post by Jakiejake on 2010-05-27
> **riverwhy said:**
> further to the above. i thought i would reinstall the package to see if it told me where it had put it..  it didn't..  i then went into "internet" (the citrix icon was here, not as previously stated, in favorites) and clicked  on the icon. The icon then disappeared???

come back Bill Gates???

First Bill Gate _**WAS**_ The CEO Of Microsoft, He is now retired and Steve Balmer has taken his place
Second of all Mark Shuttleworth is the CEO of Canonical AKA The company that creates/makes/manages Ubuntu
Yes I know Mark Shuttleworth is not the CEO at the moment that woman is because he is working on a side project but in terms he still is the CEO and will hopefully be back soon

---

### Post by riverwhy on 2010-05-27
Jerrrys - thanks for the links.. first i went to motifzone but there are loads of downloads there for openmotif.2.3.1 & i have no idea which one i need.
So i looked at the other link and found this on the forum

[B]<<<The problem is that you have installed the lastest Citrix ICA Client for Linux Version 11 aka Citrix
Receiver. The Citrix Linux Client since  Version 11 needs open motif 2.3.1. Ubuntu  includes only the prior Version 2.2.3-2. At the moment there are no  Debian or Ubuntu packages for open motif 2.3.1 available.

But the following trick *might* help. The solution is unsupported, use  at your own risk. 

Install the open-motif package 2.2.3-2. Its included in the libmotif3  package (sudo apt-get install libmotif3) Change to the directory where  the library libXM.so.3 is installed (cd /usr/lib). Make a symbolic link  from libXM.so.3 to libXm.so.4 (sudo ln -s libXm.so.3 libXm.so.4)
The Citrix Receiver should now open - and  hopefully work without further problems.>>>[/B]    

so i installed libmotif3 as above but am not sure exactly what to type in to change the directory (see above).
I tried cd/usr/lib  & then cd/usr/libXM.so.3 - both times i got "no such file or directory"  ??

---

### Post by jerrrys on 2010-05-27
look in

filesysystem>user>share

is my best guess, since i do not run this software, can't really say

also check hidden files in home folder

[ATTACH]158419[/ATTACH]

---

### Post by Jakiejake on 2010-05-28
Bump! :p

---

### Post by xipec on 2010-09-24
libX**m**.so.3 is found at File System > usr > lib
 Pay attention to the right notation of the file:
 libXm.so.3.  (It is not libX***M***.so3).
I got the following:
[B]~$ sudo ln -s libXm.so.3 libXm.so.4
ln: creating symbolic link `libXm.so.4': File exists[/B]

---

