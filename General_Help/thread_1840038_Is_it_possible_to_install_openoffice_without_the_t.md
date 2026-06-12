---
title: "Is it possible to install openoffice without the terminal"
date: 2011-09-06
forum: General Help
---

### Post by I-Like-Pie on 2011-09-06
I have downloaded this version here by clicking with my mouse

Linux      x86-64DEB
[CENTER] 

[/CENTER]
Swedish



[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

Is it possible by only clicking with the mouse to install it ?

And if not

How do i install it with the terminal what exactlly should i type?

---

### Post by haqking on 2011-09-06
> **I-Like-Pie said:**
> I have downloaded this version here by clicking with my mouse

Linux      x86-64DEB
[CENTER] 

[/CENTER]
Swedish



[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

Is it possible by only clicking with the mouse to install it ?

And if not

How do i install it with the terminal what exactlly should i type?


instructions are here [http://download.openoffice.org/common/instructions.html](http://download.openoffice.org/common/instructions.html)

---

### Post by I-Like-Pie on 2011-09-06
> **haqking said:**
> instructions are here [http://download.openoffice.org/common/instructions.html](http://download.openoffice.org/common/instructions.html)


that link requires using the terminal and I do not understand the instructions

I am asking if it is possible to install openoffice by only using the mouse and the version which i have linked above

---

### Post by haqking on 2011-09-06
> **I-Like-Pie said:**
> that link requires using the terminal and I do not understand the instructions

I am asking if it is possible to install openoffice by only using the mouse and the version which i have linked above


what part do you not understand.

and from what i remember when you unpackaged that there is a text file also with instructions.

---

### Post by I-Like-Pie on 2011-09-06
> **haqking said:**
> what part do you not understand.

and from what i remember when you unpackaged that there is a text file also with instructions.


Everything from point 3 and down is complete chinese to me

And the text files tell me nothing

I am asking is there anything I can click with my mouse to install open office the version i have downloaded

In windows all I had to do was click the downloaded file twice, is that possible in ubuntu 10.10 and if not what exactlly in the most exact sense should I type in the terminal to install this sepcific open office version

---

### Post by haqking on 2011-09-06
> **I-Like-Pie said:**
> Everything from point 3 and down is complete chinese to me

And the text files tell me nothing

I am asking is there anything I can click with my mouse to install open office the version i have downloaded

In windows all I had to do was click the downloaded file twice, is that possible in ubuntu 10.10 and if not what exactlly in the most exact sense should I type in the terminal to install this sepcific open office version


from what i remember, once extracted just double click anyone of the .deb files and it will open up with software centre

---

### Post by I-Like-Pie on 2011-09-06
> **haqking said:**
> from what i remember, once extracted just double click anyone of the .deb files and it will open up with software centre


That dosent work the only file which works was in the desktop intergration folder and that installed way to fast I think it was wrongly installed

could you perhaps write what I am supposed to write in the terminal to install open office from scratch all of it and so that it is swedish

---

### Post by e79 on 2011-09-06
Sorry for throwing in my donut **haqking** ;)

**@I-Like-Pie**

I hope you like cherry pies. If so,copy paste the commands below in your terminal :

Download the x86-64 Swedish version of OpenOffice:
```
wget http://download.services.openoffice.org/files/localized/sv/3.3.0/OOo_3.3.0_Linux_x86-64_install-deb_sv.tar.gz
```Unpack the download:
```
tar zxvf OOo_3.3.0_Linux_x86-64_install-deb_sv.tar.gz
```Change Directory:
```
cd OOO330_m20_native_packed-1_sv.9567/
```Install:
```
sudo dpkg -iR DEBS/
```Voila.

I like cherry pies.

---

### Post by haqking on 2011-09-06
> **I-Like-Pie said:**
> That dosent work the only file which works was in the desktop intergration folder and that installed way to fast I think it was wrongly installed

could you perhaps write what I am supposed to write in the terminal to install open office from scratch all of it and so that it is swedish


you want me to write terminal commands in swedish ?

in the debs folder anyone of the .debs just double click it

---

### Post by haqking on 2011-09-06
> **e79 said:**
> Sorry for throwing in my donut **haqking** ;)

**@I-Like-Pie**

I hope you like cherry pies. If so,copy paste the commands below in your terminal :

Download the x86-64 Swedish version of OpenOffice:
```
wget http://download.services.openoffice.org/files/localized/sv/3.3.0/OOo_3.3.0_Linux_x86-64_install-deb_sv.tar.gz
```Unpack the download:
```
tar zxvf OOo_3.3.0_Linux_x86-64_install-deb_sv.tar.gz
```Change Directory:
```
cd OOO330_m20_native_packed-1_sv.9567/
```Install:
```
sudo dpkg -iR DEBS/
```Voila.

I like cherry pies.


no problem, im getting confused where he asked me to write it so it is swedish...LOL

---

### Post by I-Like-Pie on 2011-09-06
> **haqking said:**
> you want me to write terminal commands in swedish ?

in the debs folder anyone of the .debs just double click it


No no

The terminal is in english

I want what perhaps the post above you wrote

But in those commands there are not sudo

I was thinking

Sudo get that specific file

Then Sudo install that specific file

---

### Post by haqking on 2011-09-06
> **I-Like-Pie said:**
> No no

The terminal is in english

I want what perhaps the post above you wrote

But in those commands there are not sudo

I was thinking

Sudo get that specific file

Then Sudo install that specific file


Just cut and paste the commands posted into your terminal.

dont get much easier than that

---

### Post by e79 on 2011-09-06
> **haqking said:**
> no problem, im getting confused where he asked me to write it so it is swedish...LOL

;)

---

### Post by e79 on 2011-09-06
> **I-Like-Pie said:**
> 
But in those commands there are not sudo

I was thinking

Sudo get that specific file

Then Sudo install that specific file

Sudo is only meant to perform administrative tasks that requires elevation (such as installing the software) and not for downloading or uncompressing some files for example.

Hope this helps

---

### Post by I-Like-Pie on 2011-09-06
> **e79 said:**
> Sorry for throwing in my donut **haqking** ;)

**@I-Like-Pie**

I hope you like cherry pies. If so,copy paste the commands below in your terminal :

Download the x86-64 Swedish version of OpenOffice:
```
wget http://download.services.openoffice.org/files/localized/sv/3.3.0/OOo_3.3.0_Linux_x86-64_install-deb_sv.tar.gz
```Unpack the download:
```
tar zxvf OOo_3.3.0_Linux_x86-64_install-deb_sv.tar.gz
```Change Directory:
```
cd OOO330_m20_native_packed-1_sv.9567/
```Install:
```
sudo dpkg -iR DEBS/
```Voila.

I like cherry pies.


The installation didnt work

If I now click applications office I do not see anything there, also BEFORE I wrote those lines from above I completely unistalled openoffice as another link on an internet page said I should do, perhaps that did something

Anyway I wrote what you said the terminal installed but when I now move my mouse over applications office there is no open office there

---

### Post by e79 on 2011-09-06
Hold on, verifying something, I'll get back to you. In the meantime, to use OpenOffice, open a terminal and type :

Starting Menu:
```
openoffice.org
```Writer only:
```
openoffice.org -write
```Calc only:
```
openoffice.org -calc
```Math only:
```
openoffice.org -math
```Draw only:
```
openoffice.org -draw
```Impress only:
```
openoffice.org -impress
```

---

### Post by e79 on 2011-09-06
:-\"  Dusting off a Ubuntu 10.04 virtual machine... :-\"

Ok, it looks like you will have to recreate your menu icons. This is not too difficult, I'll help you and you should learn a little while doing so. 

Please refer yourself to the attached screenshots 

**1.** Right-Click your Applications menu and select '**Edit Menus**'  (see _edit-menus.jpg_)

**2.** In the left pane of the menu window, select '**Office**' and then click on '**New Item**' in the rightmost pane  (see _add-item.jpg_)

**3.** Fill out the information as shown on '_writer.jpg_' screenshot.

**4.** Once done, click on the **Icon** on the left side (see _change-icon.jpg_) and change it with the appropriate icon as shown on '_icons.jpg_'. Once done, click Close.

**5.** Repeat steps 2-4 looking at '_spreadsheet.jpg_', '_impress.jpg_' and '_draw.jpg_' to create the other icons.

I think you should be good with that; post back if there's anything.

Cheers

e79

EDIT* I can only upload 5 pictures so I will try to add the missings in another reply.

---

### Post by e79 on 2011-09-06
missing screenshots.

---

### Post by I-Like-Pie on 2011-09-06
Thanks for all your very hard work but I went back to windows :)

---

### Post by Jay Car on 2011-09-07
> **I-Like-Pie said:**
> Thanks for all your very hard work but I went back to windows :)

Somehow that doesn't surprise me. :)

e79, you are awesome.

---

### Post by e79 on 2011-09-07
> **I-Like-Pie said:**
> Thanks for all your very hard work but I went back to windows :)

The pleasure is all mine,

Best luck to you :p

---

### Post by e79 on 2011-09-07
> **Jay Car said:**
> Somehow that doesn't surprise me. :)

e79, you are awesome.

Thanks Jay Car, it is surely appreciated !

Cheers

---

