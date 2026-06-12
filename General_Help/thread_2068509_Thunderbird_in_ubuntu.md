---
title: "Thunderbird in ubuntu"
date: 2012-10-09
forum: General Help
---

### Post by Gordonisnz on 2012-10-09
Hi. 

I'm running Thunderbird 15.0.1.

Today, I found I could not search for some emails though I KNOW they are there. 
(I have 1 login but 15 or so email accounts)


I googled & found that some people say to delete the *.MSF files, & your messages will re-index. (we're using IMAP)

QUESTION :- I'm old-school with Windows. & if I searched for *.mdf in windows, I'll get a list of all the files along with the directory info.

If I use Nautilus, & search *.msf, I get a blank screen - Nothing happens.

Q1:- How do I search all *.msf files in Nautilus ?

Q2. Is there an internal process within Thunderbird that I can tell it to re-index / rebuild the index for 1email account ?   Or do i need to go to nautilus & find the msf file & delete it ?


(I'll delete / rebuild 1 a day)

PS - is deleting *.msf files the best thing ?   - How do we suggest it as an in-built function (1 click, & it re-builds the index)

---

### Post by Dave_L on 2012-10-09
The Nautilus search feature apparently doesn't support wild card characters such as '*'. You could search for ".msf".

Or within Thunderbird: 

right-click on folder >> Properties... >> General Information >> Repair Folder

---

### Post by nothingspecial on 2012-10-09
Changed lubuntu prefix to ubuntu.

---

### Post by Gordonisnz on 2012-10-10
> **Dave_L said:**
> The Nautilus search feature apparently doesn't support wild card characters such as '*'. You could search for ".msf".

Or within Thunderbird: 

right-click on folder >> Properties... >> General Information >> Repair Folder


What if an email account has 20-30-50 folders ? 

do I have to repair each / every folder ? Or an entire account ?

---

### Post by Dave_L on 2012-10-10
I couldn't find a way of repairing multiple folders within Thunderbird, so in that case I would backup and then delete the .msf files in /home/---/.thunderbird using Nautilus or the command shell.  Exit from Thunderbird while doing this.

This is assuming that the search issue is caused by faulty .msf files.

---

