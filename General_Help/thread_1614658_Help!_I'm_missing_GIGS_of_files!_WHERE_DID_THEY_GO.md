---
title: "Help! I'm missing GIGS of files! WHERE DID THEY GO?"
date: 2010-11-05
forum: General Help
---

### Post by RE90 on 2010-11-05
So I don't really know how to go about this as a linux noob. I've been dual-booting with windows 7 for maybe almost a year, recently upgraded to 10.10, and had no problems -- albeit almost never using ubuntu. 

i have partitioned my drive and set up my laptop based off lifehacker's "perfect harmony" dual boot article. i.e. i have a windows partition, an ubuntu partition, and a "storage" partition where i keep all my files. the files i'm missing are things i've kept in there. 

the first time i realized i started missing files was when i downloaded a torrent from transmission and couldn't find it in windows. I went back to ubuntu and still couldnt find it -- brushed it off and figured tranmission did some funky delete thing and re-downloaded it.

now i'm missing several episodes of the office that i downloaded at once in the same folder only to find them gone. my typed lecture notes from xournal? the folder i saved them in (that i made in xournal i think) is now gone too. 

i shut down ubuntu and ran windows to double check -- windows gave me message before loading that there are disk sync problems or something and did a chksum? not sure if it accomplished anything.

can anyone help me figure out what might be going on so i dont keep losing files?

edit: looks like a lot of installed programs in windows from that drive have disappeared too -- e.g. starcraft, vuze

---

### Post by Tyson S on 2010-11-05
Are you loosing ubunutu files as well?

This could be a basic virus which comonly affects windows drives

---

### Post by RE90 on 2010-11-06
Not sure -- I keep all my downloads in my shared partition so I can't tell if anything is missing from ubuntu. 

Sometimes when I open up an app, the top window title bar is missing  after a certain amount of time using ubuntu or perhaps as soon as i boot so I have to close with alt+f4. 

Where can I look into this whole virus business? Would this be a windows virus?

---

### Post by oldos2er on 2010-11-06
What filesystem is the storage partition using?

---

### Post by wilee-nilee on 2010-11-06
Have you been using W7 as a admin primarily, not a limited account?

Never mind this thread seems strange. > Where can I look into this whole virus business? That rings quite hollow, I think this is a bogus scenario, for who knows what reasons. Could be wrong probably am hope you get the help you need.;)

---

### Post by Tyson S on 2010-11-06
Virus's in windows target the  registry which ubunut dosn't have so ubunutu should be safe unless windows can autmtically acces its partition.

Run a virus scan and ccleaner to check your machine and registry

---

### Post by kuvanito on 2010-11-06
believe me,there is no happy harmony dual boot
the only happy dual boot is two separtes drives
now you choose which drive boots first at boot time
other than that is crap coming your way sooner or later.....

---

### Post by Bitrate on 2010-11-06
Regardless of what filesystem your missing data is stored on, it would be a good idea to boot a system rescue cd and run Testdisk and let it try to recover any deleted or corrupted data.

---

### Post by RE90 on 2010-11-07
> **kuvanito said:**
> believe me,there is no happy harmony dual boot
the only happy dual boot is two separtes drives
now you choose which drive boots first at boot time
other than that is crap coming your way sooner or later.....

wish i knew this before i tried dual booting!

> Regardless of what filesystem your missing data is stored on, it would be a good idea to boot a system rescue cd and run Testdisk and let it try to recover any deleted or corrupted data.

not sure how to do this but i did run "[GetBackData]("http://www.runtime.org/data-recovery-software.htm")" and actually found some of my files! not sure exactly how to recover them -- the software isnt too noob friendly. 

> Have you been using W7 as a admin primarily, not a limited account?

pretty much, for the past year. ran a virus scan though for a few hours and nothing came up but a file in my java folder. one app was marked as a trojan but i'm pretty sure i got it from downloads.com so i doubt it's dangerous. and i assure you very much so that my files are missing -- not a troll haha.

i guess now it's a matter of recovering files which i consult other forums about unless you'd like to help me, but as far as the ubuntu community -- i'd still like to figure out how to prevent this in the future. just no more dual booting?

thanks for all your input so far...8)

---

### Post by czr114 on 2010-11-07
I also disagree with the malware theory. Most malware these days is designed to spread itself, harvest personal info, loot bank accounts, and spew loads of spam. The virus which goes to town on the filesystem, because its writer was a malicious idiot, is something mainly for the history books.

It sounds like something shredded the filesystem/MFT, unlinking a whole bunch of stuff.

Pull the drive now. It contains your data, but if you keep working on it, that data may be overwritten.

You need to boot either another system or a live CD and run GDB.

In GDB, after the scan completes, extract everything to another drive, then manually compare what was found with what can be accessed on the drive in question.

---

### Post by RE90 on 2010-11-08
is there any program i can run to just replace the lost files to their original location -- I tried testdisk -- seemed pretty confusing. 

but like i said -- i'm pretty sure my files are there -- i just have to recover them!

---

