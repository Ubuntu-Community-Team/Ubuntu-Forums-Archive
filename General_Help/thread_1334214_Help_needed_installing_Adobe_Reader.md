---
title: "Help needed installing Adobe Reader"
date: 2009-11-22
forum: General Help
---

### Post by achookang on 2009-11-22
I am new to linux & ubuntu so please forgive me. Can someone please guide me through installing a programme that I have downloaded as a .bin file.

I am using 9.10 (KK) and I want to install Adobe Acrobat Reader. It doesn't seem to be available via the Synaptic Package Manager system, but I downloaded the bin from Adobe's website

I have followed some instructions I found about chmod -x to make it an executable, then ./[name of file]

It then prompted me for a directory to install into and offered /opt as a default. (Where should one install new programmes, is /opt the default and usual place?)

Anyway I pressed enter hoping this would choose the default and I was told "Error: Cannot write to directory "/opt"

So now I am stuck. Would appreciate help

thanks
Alan

---

### Post by blazemore on 2009-11-22
The easiest thing to do is go to the Software Centre, in the Applications Menu.

Search there for Adobe Reader and it should be available for install.

You should always use the package management tools where possible, as security updates will be provided.

If you really must use the bin, do 
```
sudo ./name_of_file
```

---

### Post by phillw on 2009-11-22
> **achookang said:**
> I am new to linux & ubuntu so please forgive me. Can someone please guide me through installing a programme that I have downloaded as a .bin file.

I am using 9.10 (KK) and I want to install Adobe Acrobat Reader. It doesn't seem to be available via the Synaptic Package Manager system, but I downloaded the bin from Adobe's website

I have followed some instructions I found about chmod -x to make it an executable, then ./[name of file]

It then prompted me for a directory to install into and offered /opt as a default. (Where should one install new programmes, is /opt the default and usual place?)

Anyway I pressed enter hoping this would choose the default and I was told "Error: Cannot write to directory "/opt"

So now I am stuck. Would appreciate help

thanks
Alan

Hi,

9.10 can read adobe pdfs natively - you don't need anything extra. Document viewer handles them.

Regards,
Phill.

---

### Post by scouser73 on 2009-11-22
Delete the bin file and follow the instructions below.

**1** - Go to the [[COLOR="Red"]**Adobe Reader Website**[/COLOR]]("http://get.adobe.com/uk/reader/?promoid=BUIGO")
**2** - Click on **Different Language Or Operating System**
**3** - Click on the **Select An Operating System** drop down menu
**4** - Select **Linux - x86 (.deb)**
**5** - Click **Continue**
**6** - Select **Adobe Reader 9.1.2** & Click **Download Now**

That will start installing Adobe PDF Reader for you, once installed you can find it in Office.

---

### Post by phillw on 2009-11-22
> **scouser73 said:**
> Delete the bin file and follow the instructions below.

**1** - Go to the [[COLOR=Red]**Adobe Reader Website**[/COLOR]]("http://get.adobe.com/uk/reader/?promoid=BUIGO")
**2** - Click on **Different Language Or Operating System**
**3** - Click on the **Select An Operating System** drop down menu
**4** - Select **Linux - x86 (.deb)**
**5** - Click **Continue**
**6** - Select **Adobe Reader 9.1.2** & Click **Download Now**

That will start installing Adobe PDF Reader for you, once installed you can find it in Office.

Hi Scouser - just a bit puzzled - what is the advantage of reader over doc viewer ?  
Thanks,
Phill.

---

### Post by scouser73 on 2009-11-22
I don't think there is an advantage, I just like using Adobe PDF Reader, just down to preference really.

---

### Post by achookang on 2009-11-22
Hi,

Blazemore, on my system the Adobe Reader is not there in the Software Centre. Not sure why this is.
PhillW, I realised that the Document Viewer can already read PDFs, but I just wanted to use the Adobe reader that I was already familiar with. (Just a matter of personal preference) Also wanted to practice installing things, as I get familiar with Ubuntu! :)
Scouser73, thanks, I'm trying your method now. Will post back if I have any more problems


thanks all.
Alan

---

### Post by ra3 on 2009-12-07
scouser73, thanks so much!!  :KS

I've been working on getting Adobe Reader for hours!  Why Adobe because Document Viewer is not displaying Japanese text in PDFs and I can't figure out why.  I'm going to give Adobe a go.

Thanks!

Ra3

---

