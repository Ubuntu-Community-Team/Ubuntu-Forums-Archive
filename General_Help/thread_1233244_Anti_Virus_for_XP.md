---
title: "Anti Virus for XP?"
date: 2009-08-06
forum: General Help
---

### Post by razorboy5 on 2009-08-06
Hi
 
finally i'm done dual booting my Laptop
i gave 240GB to my Ubuntu and 10GB to my Windows XP
 
i dont use XP except for gaming (suddenattack if u've heard of it and thinkin of getting Diablo 2 on a *cough cough* server)
 
would u recommend getting an antivirus for XP if i'm using just for those purposes?
 
and i dont know alot about viruses but heard they "infect" hard drive. Does that mean they'll leak through to the Ubuntu side or will it generally stay to the Windows side?
 
didn't really bother with Antivirus on Ubuntu cuz wasn't too worried

---

### Post by snakeman21 on 2009-08-06
My wife does the same thing, uses windows only for games.  As long as you go to your device manager and disable all your network devices, you should not need an antivirus.... unless you intend to share files between ubuntu and windows.


ps:  Even if viruses "leaked" to your ubuntu partition, ubuntu wouldn't be effected.

---

### Post by credobyte on 2009-08-06
If you use it only for gaming, get an on-demand scanner/antivirus like BitDefender ( free ).

---

### Post by razorboy5 on 2009-08-06
well it's only for gaming but they're online games, dunno if that makes alot of difference
 
good to hear that my ubuntu wont be affected thou :D

---

### Post by aysiu on 2009-08-06
I'd recommend using a limited user account in XP.

---

### Post by BloGTK on 2009-08-06
I use AVG Free on my Windows VMs. It's good enough protection, and it's free. You have to jump through a bunch of hoops to download it, but just keep clicking on the links for a free version.

If you mainly play Diablo 2, I'm almost positive that you should be able to play that under Linux with Wine -- it's a rather old game.

---

### Post by razorboy5 on 2009-08-06
chances of getting viruses in limited user and admin, are they the same?
 
did a very brief research before posting and it only mentions that if u get hit with virus on admin it can be more severe than with limited
 
EDIT: thx for the AVG Free recommendation, will check that out when i get on my laptop. also yea Diablo 2 runs in Linux but duno how to get on a *cough cough* server in Ubuntu. All the tuts are in windows

---

### Post by aysiu on 2009-08-06
> **razorboy5 said:**
> chances of getting viruses in limited user and admin, are they the same? Not really.

First of all, almost all viruses are designed to get into system files so as to be difficult to remove.

Secondly, if it's just a gaming computer, there's not much in the user account for the virus to damage. If it really got infected (which it won't), you could just delete the user account and create a new one.

From what I've seen, the chances of getting viruses with antivirus are the same as getting viruses without antivirus. In fact, sometimes it's worse with antivirus (complacency, placebo effect, susceptibility to rogue viruses, paranoia about false positives and tracking cookies).

---

### Post by razorboy5 on 2009-08-06
ah that's a great idea to just keep deleting the accounts :D
 
thx alot for the tip :P

---

### Post by bronkeydain on 2009-08-06
Just get AVG and you'd be alright. 

There is also a product called deepfreeze that will return your computer back to the exact state it was in each reboot. This also means you would lose any files you save on your system, but also all viruses. You can have it exclude folders so you can save your files in there...

---

### Post by lildigiman on 2009-08-06
What you can easily do is install ClamTK/ClamAV Virus Scanner in Ubuntu. Search for "Virus Scanner" in Add/Remove Programs, and it will be the only one that shows up. You can scan your windows partition right inside ubuntu using it.

Or if you choose to have the software on your windows partition, you can install ClamWIN from [http://www.clamwin.com/](http://www.clamwin.com/).

Either works great and finds everything you could throw at it.

---

### Post by y-lee on 2009-08-06
> **lildigiman said:**
> What you can easily do is install ClamTK/ClamAV Virus Scanner in Ubuntu. 
...

Either works great and finds everything you could throw at it.

Simply not true no anti virus i know of can detect "everything you could throw at it". In fact AVG (already mentioned) and Avast (which has a free version) both do much better than ClamAV.

From [Wikipedia]("http://en.wikipedia.org/wiki/ClamWin#Effectiveness") (and yeah I know the reference is a bit old but I seriously doubt much has changed)

> In the 1 - 21 June 2008 test performed by Virus.gr, ClamWin version 0.93 detected 54.68% of all threats and ranked 37th out of 49 products tested 

And btw AVG has [a linux version]("https://help.ubuntu.com/community/Antivirus/Avg") :)

These days tho even when using windows I am starting [to doubt the effectiveness of using anti-virus programs]("http://www.codinghorror.com/blog/archives/000803.html") esp since they hurt system performance enough for me to notice.

---

### Post by Revolutionary101 on 2009-08-06
Viruses that are designed for Windows will not run on Ubuntu (Just like you can't run a .exe file on Ubuntu without Wine). I would suggest getting an anti-virus because as long as this computer is connect to the Internet and is using Windows there is always a possibility of getting a virus. I suggest getting Avast anti-virus.

---

### Post by razorboy5 on 2009-08-06
well although it's not a very good anti virus as mentioned by y-lee, it seems very convenient. If i were to run anti-virus on windows i would have to leave on windows for maybe up to hours without doing much. Will have to check it out

and i've tried to run .exe alot of times in Ubuntu lol... :-\"
and love ur siggy Revolutionary

---

### Post by martinbaselier on 2009-08-07
If you know what you're doing, you don't need antivirus. I've done so myself from windows 98 till xp and never had a problem. It's save though to have a scanner available to scan new files you downloaded, and do a global system scan every now and then. 

This is a good guide to understand the services (good clear explanations) and learn which ones you can turn off safely. He also created profiles for different situations. The information is for windows 2000 - windows 7 (and for each service pack)
[http://www.blackviper.com/](http://www.blackviper.com/)

Turning off a few of those phone-home services will start to make your system safer. Viruses like to use options already available, like telnet, outlook, msn, internet explorer. So avoid those as much as possible. There are alternatives for all of them. 

If you just make sure you scan every new program you download, you should be safe enough. And watch out where you click.

---

### Post by mike555 on 2009-08-07
You might want to check out a free lock down program, like "system protect " ...
[http://www.system-protect.com/](http://www.system-protect.com/)

---

### Post by automaton26 on 2009-08-07
I use AVG Free on my Vista x64 partition. It seems OK - I scan everything I download.

But I've never seen any viruses in the past decade, because I only get things from reliable sources. Or perhaps the AV products just never detect the worst viruses...!

---

