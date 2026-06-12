---
title: "printing over a network"
date: 2010-09-09
forum: General Help
---

### Post by drdob on 2010-09-09
Dear all could you please help me ?
I am running Ubuntu 10.4 LTS . I wish to share files and a printer over my network, it is on my main computer running XP . my ubuntu can see the printer but it will not print at all, it has the drivers Etc but it will not print. the personal file share said that i do not have the right package installed, but not which one! can anybody give a old codger a hint..... or just get me out of this hole. thank you  Dr Dob

---

### Post by stevebu56 on 2010-09-09
When you say "the personal file share said that i do not have the right package installed" what do you mean?  Can you explain where you're seeing this error?

---

### Post by drdob on 2010-09-09
hi stevebu56 thank you for replying 
i found it in System > preferences >personal file shearing.
dr Dob

i should have added : in the box :
SHARE FILES OVER THE NETWORK
 below is this;
this feature cannot be enabled because the required packages are not installed on your system. 
 But what packages???
DrDob

---

### Post by stevebu56 on 2010-09-09
Have you added the printer via System->Administration->Printing->Add? 

To add the printer do the following from the Printing dialog. 
```
Click Add
Click Network Printer 
Click Windows Printer via SAMBA 
Click Browse & find printer 
Click Forward
Select the printer from the printer database. 
Make a name for the printer & click Apply. 
```

Now you should be able to use that printer when printing.

The personal file sharing option is to share files from your Ubuntu box to others on the local network.  I don't think that's what you want in this situation.

---

### Post by sgosnell on 2010-09-09
You also need to have samba installed, of course.

---

### Post by drdob on 2010-09-10
hi stevebu56  ):P

i have done that more than once when it test it with verify i get                             
           "Print Share Inaccessible   Invalid argument"
that is the annoying bit Ubuntu can see my xp computer and the printer but not print from it....
                      yours Dr Dob

---

### Post by drdob on 2010-09-13
thank to all that replied but still no printing. i am stumped . the printer works ok if i pug in direct. but not over the network it gets to 1% and stops.oh well back to head scratching

---

