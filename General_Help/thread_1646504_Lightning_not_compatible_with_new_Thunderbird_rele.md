---
title: "Lightning not compatible with new Thunderbird release???"
date: 2010-12-16
forum: General Help
---

### Post by Noah's Ark on 2010-12-16
Does anyone know a trick to make the new Thunderbird release function with the Mozilla Lightning (calendar) extension?  You will be my hero!

My history is this:
Each time Mozilla releases a new upgrade of Thunderbird (my main email client), I lose Lightning (my main calendar client) functionality.  [BTW, this is a real pain in the chops!]
In the past I have been able to simply manually install the 64bit version of Lightning, post hoc, and it has worked.  However, this is not working with the new T-Bird (v.3.1.7) release.  

Error message reads: 
""Lightning" could not be installed because it is not compatible with your Thunderbird build type (Linux_x86_64-gcc3). Please contact the author of this item about the problem."

Any suggestions?

---

### Post by DeMus on 2010-12-16
> **Noah's Ark said:**
> Does anyone know a trick to make the new Thunderbird release function with the Mozilla Lightning (calendar) extension?  You will be my hero!

My history is this:
Each time Mozilla releases a new upgrade of Thunderbird (my main email client), I lose Lightning (my main calendar client) functionality.  [BTW, this is a real pain in the chops!]
In the past I have been able to simply manually install the 64bit version of Lightning, post hoc, and it has worked.  However, this is not working with the new T-Bird (v.3.1.7) release.  

Error message reads: 
""Lightning" could not be installed because it is not compatible with your Thunderbird build type (Linux_x86_64-gcc3). Please contact the author of this item about the problem."

Any suggestions?

At the site where you found Lightning you can also find the person who made it. Write him about it and ask if there will be a newer version. Or ask Mozilla to not always change that program-part which deals with add-ons.
Which version do you have btw? I get daily updates of Thunderbird and my lightning keeps on working.
I have T'bird 3.1.8pre and Lightning 1.0b2. Great combination.

---

### Post by Noah's Ark on 2010-12-16
I have tbird v.3.1.7 and lightning 1.0b1

---

### Post by POWMS on 2010-12-16
Noah
after my Thunderbird update completed, I opened it and was informed Lightning was not compatible with the latest release of Thunderbird. A few seconds later I received a message that my add-ons were being updated. Lighting was one of those. 
Try and do a manual update by re-downloading the latest Lighting from Mozilla and re-insatalling in Thunderbird.
Regards
Craig

---

### Post by Noah's Ark on 2010-12-16
I did that several times actually, and no dice...
I tried also downloading older versions (0.9 etc.) from the apache server, and that did not work either...

---

### Post by POWMS on 2010-12-16
Sorry Noah.
I didn't read your original post completely.
I was referring to 32 bit.
I have not been able to get the 64 bit Thunderbird and Lightning to play nice.
Try emailing Lighting author?

---

### Post by timgood on 2010-12-16
Open the 1.0b2pre lighting.xpi by double clicking on it - it will open in Archive Manager. Double click on the file install.rdf which will open in gedit. Find the section:
> <em:targetApplication>
      <Description>
        <!-- thunderbird -->

Underneath you will find:

> <em:maxVersion>XXX</em:maxVersion>

Change the maxVersion to your version of Thunderbird (in my case 3.1.7). Save the file and Archive Manager will ask if you want to update the file in the archive. Do so. 

Now you will be able to install the .xpi without any problems. I have this working fine on my system.

Hope this helps.

---

### Post by timgood on 2010-12-16
I have made my modded version of the 1.0b2pre lighting.xpi available [here:]("http://www.eekageek.co.uk/uploads/lightning.xpi")

This should work with version 3.1.7 of 64bit Thunderbird.


I hope this helps.

---

### Post by Noah's Ark on 2010-12-16
Timgood, you have solved the issue-  HOORAH!

I had no idea that the coding was authored specifically for each version, without any reference given to the updated coding version.  So, every time T-bird updates, I will have to go in and change the version marker...

Thanks!

---

### Post by sepius on 2010-12-17
Helped me too, thanks so much timgood ... you are the man!!

---

### Post by hubie on 2010-12-23
timgood, I appreciate the solution as it worked for me.  I noticed that the version in the line I edited was 3.1.*  Do you know if that asterisk is supposed to function as a wildcard, and if so, is it a bug that it wasn't working like it should?

---

### Post by killabee44 on 2011-01-31
> **timgood said:**
> I have made my modded version of the 1.0b2pre lighting.xpi available [here:]("http://www.eekageek.co.uk/uploads/lightning.xpi")

This should work with version 3.1.7 of 64bit Thunderbird.


I hope this helps.

I know this thread is kind of old, but just wanted to thank you timgood. You fixed my issue as well. 
:)

---

