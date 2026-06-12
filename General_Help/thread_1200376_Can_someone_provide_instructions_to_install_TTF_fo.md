---
title: "Can someone provide instructions to install TTF fonts into ubuntu 9.04 ?"
date: 2009-06-29
forum: General Help
---

### Post by JeZ-l-Lee on 2009-06-29
Hi,

I am switching from Vista to ubuntu 9.04
I am currently looking for a job and am viewing my resume made in Office 2003 in OpenOffice 3.
Problem is that my resume uses a TTF font that is not available in ubuntu.
_How can I properly install a TTF Windows font into ubuntu 9.04 ?_

I am a total beginner, so I need step by step instructions.
Thanks in advance!

------------------------------------------------------
**JeZ+Lee**

---

### Post by merlinus on 2009-06-29
[http://tombuntu.com/index.php/2008/04/17/how-to-install-fonts-in-ubuntu-804/](http://tombuntu.com/index.php/2008/04/17/how-to-install-fonts-in-ubuntu-804/)

Next time try a google search...

---

### Post by JeZ-l-Lee on 2009-06-30
Hi, I did Google for about two hours and found nothing.
I followed the instructions in the URL page you posted but it still is not working.
Trying to add Arial Narrow TTF font into ubuntu 9.04
Please look at this screenshot for more info:
[Image link]("http://silentheroproductions.com/images/TTF_Fonts_ubuntu01.png")

---

### Post by merlinus on 2009-06-30
FWIW, it did not work for me either.  

But this worked:

                                 To integrate additional fonts in the OpenOffice.org software, proceed as follows:
 
[LIST=1]
[*]Go to the {install_path}/program directory.  For me, it was /usr/lib/openoffice/program, and double-click spadmin
[*]Click **Fonts**.
[*]The dialog lists all fonts added for the     OpenOffice.org software. You can select and remove fonts using the     **Remove** button or add new fonts with the **Add** button.
[*]Click **Add**. The **Add Fonts**     dialog appears.
[*]Enter the directory from which you want to     add the fonts. Press the **...** button and select the directory     from the path selection dialog or enter the directory directly.
[*]A list of the fonts from this directory     appears. Select the fonts you want to add. To add all the fonts,     click **Select All**.
[/LIST]

---

### Post by JeZ-l-Lee on 2009-06-30
Hi, thanks for the reply, I did successfully followed your instructions - but it did not add the Arial Narrow font - perhaps my font from Vista is bad or something...

---

### Post by merlinus on 2009-06-30
THis is clearly a flawed method.  For example, I could not load any of my Adobe Type I fonts.  They are installed into /home/.fonts, and I can see them in Character Map, but only the ttf ones would install into Open Office.

---

### Post by angryhomer17 on 2009-06-30
I tried installing arialn.ttf from XP into openoffice 3 about five different ways, but it would have none of it. I guess it doesn't like letters being so close to one another. They need bigger bubbles.

Anyway, I did find a few ways to work around this.

1. Don't use arial narrow. Simple, easy, and effective. Change your resume to a different font. Try Liberation Sans or FreeSans; they are exact matches for arial and they are open, of course. This might also force you to look over your resume and see if you really need that extra sentence or two.

2. My resume is quite fine, thank you very much. I don't want to change it, I just want to view and edit it in Ubuntu. Well since openoffice doesn't want to play nice we can try something else. Like abiword. You can install this word processor by copying this:

```
sudo apt-get install abiword
```

Abiword is a decent replacement for word/openoffice, not the greatest, but it works. Plus you can use arial narrow in it. 

Oh, so you have to install the arial narrow fonts first, which it looks like you already did. Just copy them into /usr/share/fonts/truetype/msttcorefonts, if you haven't.

Open your resume in abiword and view/edit away. Note: While abiword will display arial narrow fonts and will let you edit your document in arial narrow, you can't open a new document and choose arial narrow. :( You can either copy and paste some arial narrow text and toss it in a new doc, or just edit an existing doc with arial narrow and save it under something new.

Note 2: Don't freak out if some of the text disappears. This is a bug with abiword. Just scroll up and down to refresh the screen. Your text will magically reappear.

3. Bah, I hate Ubuntu, why won't it just work like it says it will? Screw this I'm going back to windows. If you've gotten to this point, there is still another option. You can have your ubuntu and eat it too. (I wonder how ubuntu tastes). Anyway, you can run windows inside of ubuntu (not a dual boot) and work with all that proprietary stuff in there. Just install virtualbox and install vista or xp or whatever other os you want to run with virtualbox. 

This third choice works out well for me, because openoffice, while nice, is no replacement for MS office. For all the stupid and idiotic and crazy stuff ms does, they make a decent office suite. Although word sucks. I just use nano or gedit. But I still have yet to find a good replacement for excel. 

Oh, one last thing. Don't save or send your documents in .doc format. It's old and incompatible with any other word processor, even itself. Try .odt, .rtf, or .pdf. Check out this link. [http://en.nothingisreal.com/wiki/Please_don%27t_send_me_Microsoft_Word_documents](http://en.nothingisreal.com/wiki/Please_don%27t_send_me_Microsoft_Word_documents)

---

### Post by merlinus on 2009-06-30
I believe the problem with certain fonts not being able to be used by OpenOffice has to do with copyrights.

M$ released a number of their fonts into the public domain via msttcorefonts and webfonts, but the rest of theirs and Adobe's were not.

Fortunately there is still a very good selection to choose from.

---

### Post by chavezgvg on 2009-08-04
Finally I succeeded installing the Arial Narrow ttf.  Nothing special just the ttf file I used.  Here is the URL to download it:

[http://www.free-fonts-ttf.org/true-type-fonts/lexicon-17-high-quality-collections.htm?page=32](http://www.free-fonts-ttf.org/true-type-fonts/lexicon-17-high-quality-collections.htm?page=32)

I put them into my .fonts directory, executed sudo fc-cache -vf, and thats it.  Now I can read .doc or .docx that comes from other people who uses this font.

I hope this will be helpfull.

---

### Post by specialcowboy on 2009-10-28
Alt+F2
Type gksudo nautilus
navigate to /usr/share/fonts
paste the fonts into the truetype folder

Select all of the fonts just added
Right-click and select properties
go to the permissions tab
Under Others - select Access: Read only

Open a terminal window
type sudo fc-cache -fv

You may need to logout and log back on. Not sure.

This worked for me to add Armenian TT fonts to my Ubuntu 9.04

---

### Post by oktapod on 2009-11-14
There is a Microsoft Core Fonts pakage in the Ubuntu Software Center. Ubuntu 9.10

---

### Post by Rod J on 2010-01-13
> **chavezgvg said:**
> Finally I succeeded installing the Arial Narrow ttf.  Nothing special just the ttf file I used.  Here is the URL to download it:

[http://www.free-fonts-ttf.org/true-type-fonts/lexicon-17-high-quality-collections.htm?page=32](http://www.free-fonts-ttf.org/true-type-fonts/lexicon-17-high-quality-collections.htm?page=32)

I put them into my .fonts directory, executed sudo fc-cache -vf, and thats it.  Now I can read .doc or .docx that comes from other people who uses this font.

I hope this will be helpfull.

I have been having the same problem adding the standard Arial Narrow fonts to my system. I have a theory why Arial Narrow is difficult to add to a Linux system: If you double click on the Arial Narrow family of font files (ARIALN.TTF, ARIALNB.TTF, ARIALNBI.TTF ARIALNI.TTF) in the font viewer and compare the information you will see that they are all the same-- Name: Arial, Style: Narrow. The basic info doesn't seem to differentiate between the Bold, Bold Italic, Italic styles even though the individual style information is embedded in the font file and the file names are different. So, I think this confuses the font manager and it simply ignores the Arial Narrow family. Maybe this is overly simplistic and may not be correct but I suspect this is the problem. Someone with more knowledge might be able to correct me on this. 

If you compare the individual font file info of the Arial Narrow family files downloaded from [www.free-fonts-ttf.org](www.free-fonts-ttf.org) you will see that the information as viewed in the font viewer is distinctive for each member of the family and that's why they can be installed successfully.

---

