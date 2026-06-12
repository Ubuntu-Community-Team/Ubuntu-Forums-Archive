---
title: "is not marked as executable."
date: 2010-04-19
forum: General Help
---

### Post by trig on 2010-04-19
I have installed .exe on my computer before the Upgrade to 10.4. But since i have did so, i get The file '/home/captain/Downloads/TryWoW.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit. Wine  is installed.

---

### Post by nexes128 on 2010-04-19
Right click on the exe file and go properties, then select permissions and check "Allow executing file as program".

---

### Post by trig on 2010-04-19
Thanks for the tip guys.  it worked

---

### Post by nexes128 on 2010-04-19
Not a problem, you should mark the thread as solved now

---

### Post by comp3820 on 2010-05-03
I have the same problem, but unfortunately, this doesn't work for me.

I'm trying to run setup.exe for Office 2007 from the CD, and Ubuntu says it can't change the permissions because the filetype is read only.

I have done this before, so I don't know if this is a new thing. Is there any way to get around this for a CD?

---

### Post by bakelitedoorbell on 2010-05-07
This is what worked for me when installing a game from a CD:

Right click on the setup.exe file and choose "Open with Other Application"

Click the little plus sign next to "Use a custom command" and in the box that appears, type:  wine

Click "Open"

---

### Post by narendraD on 2010-05-08
> **comp3820 said:**
> I have the same problem, but unfortunately, this doesn't work for me.

I'm trying to run setup.exe for Office 2007 from the CD, and Ubuntu says it can't change the permissions because the filetype is read only.

I have done this before, so I don't know if this is a new thing. Is there any way to get around this for a CD?
You cant install Office 2007 in Ubuntu. Maybe (a Big One) thru Wine, but when you can have OpenOffice why Office2007.

---

### Post by comp3820 on 2010-05-08
My problem turned out to be a stupid mistake (using CD 2 of my office CDs instead of CD 1). 

I did end up installing Office 2007 in ubuntu, and it works fine (except for some slight menu issues that I need to figure out). 

IMHO, MS office is amazing, and openoffice can't even touch it. I think linux needs a good looking, easy to use word processor that can compete.

---

### Post by narendraD on 2010-05-10
> **comp3820 said:**
> My problem turned out to be a stupid mistake (using CD 2 of my office CDs instead of CD 1). 

I did end up installing Office 2007 in ubuntu, and it works fine (except for some slight menu issues that I need to figure out). 

IMHO, MS office is amazing, and openoffice can't even touch it. I think linux needs a good looking, easy to use word processor that can compete.


Congrats and Good Luck on using Office 2007 on Ubuntu. Pl post back on how good the combination of Ubuntu and MS Office work for you. There are quite a few good word processors for Linux. Other than OpenOffice, Abiword is very good. They are both way better than MS Word. May be the familiar Menu and GUI makes you feel more comfortable. Give OO or Abiword a try, u will not regret it.

---

### Post by comp3820 on 2010-05-10
In my opinion, Word is better than openoffice because of the ease of use. Openoffice is about the equivalent of Office 98 or 2000, where you need to find everything in a menu. In Office 2007, everything is arranged very well (and I used open office before the new ribbon ui).

Also, one of the biggest things that I appreciate about Office 2007 and 2010 (beta) is that you have almost instant formatting, with the one-click options that make your entire document look professional. It makes formating fun! I didn't even know these options existed in earlier versions of Word (or openoffice for that matter). Just another example of why placement is very important.

I'm also impressed with how Office looks. I know, I know - it doesn't matter. But open office is ugly, or at bare minimum just bearable. And in the end, that affects my decision as well. Now, themes for openoffice... you might have my interest again. :popcorn:

---

### Post by henkeldg on 2010-05-24
The problem with CDs is that there's no way to modify the permissions. Using "wine" as a custom command works perfectly. Thanks bakelitedoorbell.

---

### Post by stijnblommerde on 2010-08-12
similar problem for a different program.

properties > permissions > allow ... worked for me.

thanks a lot

---

### Post by lewis.muzy on 2010-09-06
Hey all, i'm new to this but i tried to change the access from read only and it said "could not change the permissions of "install.exe": Error setting permissions: Read-only file system" and the same happens when i try to "allow executing file as a program".

I tried to use the wine loader to no effect and sudo also appeared to do nothing.

Oh the thing i'm trying to install is "The Logical Journey of the Zoombinis"

Thankyou for any help.

---

### Post by xboxSlayer on 2010-10-02
Thanks,this worked for me as well.

---

### Post by Mugsy323 on 2010-10-25
> **nexes128 said:**
> Right click on the exe file and go properties, then select permissions and check "Allow executing file as program".
I know this is an old thread, but I'm not finding a fix.

When I try to "check" the "Allow execution..." box, it instantly unchecks.

Same thing when logged in as root, so I'm stumped.

Any ideas? Thx.

---

### Post by kip152 on 2010-10-26
I had Zet 8 through Wine on 9.04. After switching to 10.10, I can't get it to work. Someone said rightclick to set as executable, there's nothing like that available when I rightclick. How do I get the Zet 8 download to open with Wine in this new version?

---

### Post by bhaveshnande on 2010-10-28
Same problem...
When I go to properties and try to click on that check box, it **unchecks** instantly. What is the problem....
Any solution?

---

### Post by Mariusmssj on 2010-11-09
> **Mugsy323 said:**
> I know this is an old thread, but I'm not finding a fix.

When I try to "check" the "Allow execution..." box, it instantly unchecks.

Same thing when logged in as root, so I'm stumped.

Any ideas? Thx.

> **bhaveshnande said:**
> Same problem...
When I go to properties and try to click on that check box, it **unchecks** instantly. What is the problem....
Any solution?


same here whenever i tick the box, it just unchecks itself

---

### Post by gandaran on 2010-11-09
> **Mariusmssj said:**
> same here whenever i tick the box, it just unchecks itself
which directory is the file in when you try to do this?

---

### Post by Verbeck on 2010-11-09
right click on the file>open with other application>type in the custom command, **wine**

hope this helps

---

### Post by bhaveshnande on 2010-11-09
I got the solution. If you don't want your tick mark to disappear, just bring that particular file to the ubuntu part of your hard drive..
i.e bring that file to your ubuntu desktop and then try to add that tick mark. :D
it worked for me.

---

### Post by alab0 on 2011-02-25
> **bhaveshnande said:**
> I got the solution. If you don't want your tick mark to disappear, just bring that particular file to the ubuntu part of your hard drive..
i.e bring that file to your ubuntu desktop and then try to add that tick mark. :D
it worked for me.

Nice work\\:D/

---

### Post by Bcrowes11 on 2011-02-25
Insert the disk into cd drive. Open up the cd folder. Create a folder on you desktop. Copy the files from the cd folder into the desktop folder you created. Take the cd out. You should be able to set the exe files as executable now. This worked for me. Hope it works for you.:popcorn:

---

