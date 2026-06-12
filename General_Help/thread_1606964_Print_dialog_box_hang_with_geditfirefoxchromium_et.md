---
title: "Print dialog box hang with gedit/firefox/chromium etc"
date: 2010-10-27
forum: General Help
---

### Post by rainbow99984 on 2010-10-27
Hi, My System spec is::Ubuntu 10.04/Kernel 2.6.32-25-generic #45-Ubuntu   i686 GNU/Linux
gnome::2.30.2. Laptop - Dell E6400. 
today I updated it, the problem I'm facing occurs even before update so update is not the cause.till yesterday night every thing worked fine.
Problem::
>>When ever i try to print from firefox/Chromium/Gedit the print dialog appears shows just print to file and hang up !
>>I checked in System->Administration->Printing and it shows list of network printers(I'm in Lan). Even i can successfully print from gvim/writer.
>> once i left that dialog box left open, may be around 10 min latter i saw the list of printer but when i tried again same thing- Hang !!
I even checked with cupsd it is running normally.
Any guess where to check for the problem part/solution?

===========================================================================
Admin team just solved the problem it was due to the shared printer option enabled in System->Administration-Printing.
Hope the shared printer call was delaying too much to cause hang. As of now things are working fine
Thanks.
Rahul

---

### Post by arapaho on 2010-11-18
I have the same problem. When I want to print to a file from Opera system frequently hangs. Actually not the whole system, because I can move mouse, but I can't do anything with applications.
Any solution, please?
Sorry, I didn't noticed it is marked as solved. I don't have any shared printers and problem still exist.
Edit:
I have just discovered that there is an option "shared" in System->Administration-Printing -> print-to-pdf -> politics -> option 'State' - shared. I unmarked it. I will see if it works and let you know. 
Actually, I'm going to start a new topic.

---

