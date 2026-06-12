---
title: "Xfire-\wine problem and Compiz effect problem"
date: 2010-05-18
forum: General Help
---

### Post by nitrus on 2010-05-18
Hello there i have just recently started using linux Ubuntu 10.04 and i know enough about computers to figure out linux and learn it.  First problem is i installed wine which is installed flawlessly to use some windows apps.  Once i installed wine i tested it out by installing Xfire and when i ran it i got this erorr message..
________________________________________________________________________
<?xml version="1.0" encoding="utf-8" ?>

<ExceptionReport Version="4">
	<Application Build="42654" Command="&quot;C:\Program Files\Xfire\Xfire.exe&quot;"/>
	<OperatingSystem Type="2"><Version Major="6" Minor="1" Build="7600"/></OperatingSystem>
	<Exception Code="C0000005" Address="7A6A8A4E"></Exception>
	<Registers EAX="00000001" EBX="00000000" ECX="00000000" EDX="00000000" ESI="00000009" EDI="7CBC2310" CS="0023" EIP="7A6A8A4E" SS="002B" ESP="0032F0E4" EBP="00000000" DS="002B" ES="002B" FS="0063" GS="006B" Flags="00010246"/>
	<BackTrace>
	</BackTrace>
</ExceptionReport>
_________________________________________________________________________

My other problem is Compiz configure settings wont enable any effects.  When i go into Compiz config and enable the Burn effect nothing happens.  This problem happens with all of the effects i try.  I have installed the Animation Addon that i read on google that adds the other cool effects such as the burn effect i wanted  to setup.

I can post a screen shot of the "Xfire Exception" problem if someone lets me know how to do that via ubuntu because i am use to windows.

---

### Post by ubunterooster on 2010-05-18
Regarding screenshots go to applications>accessories>screenshot. I prefer to tell it to take the picture after 3 seconds so I can place mouse were I want it. I save the screenshots to my desktop. See following screenshots for uploading.

---

### Post by nitrus on 2010-05-18
Here is exact code on Xfire Exception 

> <?xml version="1.0" encoding="utf-8" ?>

<ExceptionReport Version="4">
	<Application Build="42654" Command="&quot;C:\Program Files\Xfire\Xfire.exe&quot;"/>
	<OperatingSystem Type="2"><Version Major="6" Minor="1" Build="7600"/></OperatingSystem>
	<Exception Code="C0000005" Address="7A6A8A4E"></Exception>
	<Registers EAX="00000001" EBX="00000000" ECX="00000000" EDX="00000000" ESI="00000009" EDI="7CBC2310" CS="0023" EIP="7A6A8A4E" SS="002B" ESP="0032F0E4" EBP="00000000" DS="002B" ES="002B" FS="0063" GS="006B" Flags="00010246"/>
	<BackTrace>
	</BackTrace>
</ExceptionReport>


In the Compiz Screenshot im showing the Animation and Animation addon are both check and still no effects.  Thank you for replying fast.  Hope this helps.

---

### Post by ubunterooster on 2010-05-18
Actually I am not sure what is going on but wanted to get the screenshot up so someone else could.

Right-click on the background and click "Change desktop background" go to the "visual effects" tab and set to "none". Then go back to compiz and see if after changing settings there it works now. Again, I am not sure of the the problem.

---

### Post by nitrus on 2010-05-18
> **ubunterooster said:**
> Actually I am not sure what is going on but wanted to get the screenshot up so someone else could.

Right-click on the background and click "Change desktop background" go to the "visual effects" tab and set to "none". Then go back to compiz and see if after changing settings there it works now. Again, I am not sure of the the problem.

Doesn't look like that fixed the issue in Compiz i also can't remove Xfire from Wine Remove?  i get a "Unable to elevate, Error 1" when i try to remove it

---

### Post by nitrus on 2010-05-19
Any ideas how to remove it?

---

### Post by ubunterooster on 2010-05-19
I'd go to the wine folder and delete the folders for the program.

---

### Post by nitrus on 2010-05-20
thanks let you know if that worked

---

