---
title: "Installing Adobe pdf reader."
date: 2010-01-11
forum: General Help
---

### Post by Lakeside on 2010-01-11
I am running Ubuntu Intrepid server and hosting a Joomla website with a pdf embed extension so I can put .pdf's in my articles. But I have to have Adobe pdf reader on here too (I use Firefox) Would someone be able to help me do this step by step? I would really appreciate that, thanks.

---

### Post by garvinrick4 on 2010-01-12
I know nothing about servers but it is called acroread.

---

### Post by plucky on 2010-01-12
**acroread** is in the partner repository.```
sudo nano /etc/apt/sources.list
``` and remove the # from this line ```
deb http://archive.canonical.com/ubuntu karmic partner
``` then run ```
sudo apt-get update
sudo apt-get install acroread
``` assuming you are using Ubuntu 9.10 Karmic Koala.


Good Luck

---

### Post by scouser73 on 2010-01-12
> **Lakeside said:**
> I am running Ubuntu Intrepid server and hosting a Joomla website with a pdf embed extension so I can put .pdf's in my articles. But I have to have Adobe pdf reader on here too (I use Firefox) Would someone be able to help me do this step by step? I would really appreciate that, thanks.

B]1[/B] - Go to the [[COLOR="Red"]**Adobe Reader Website**[/COLOR]]("http://get.adobe.com/uk/reader/?promoid=BUIGO")
**2** - Click on **Different Language Or Operating System**
**3** - Click on the **Select An Operating System** drop down menu
**4** - Select **Linux - x86 (.deb)**
**5** - Click **Continue**
**6** - Select **Adobe Reader 9.2** & Click **Download Now**
**7** - Open With **GDebi Package Installer**

---

### Post by Lakeside on 2010-01-12
Thanks for the suggestion.  I am actually using Hardy Heron 8.4(I think) I did run that command but of course did not find that line (deb.....Karmac partner).

---

### Post by Lakeside on 2010-01-12
Thanks for mentioning Acroread guys,  silly me I didn't realize it was in the supository, I I went there and just selected and installed it that way, I hope that is okay.

---

