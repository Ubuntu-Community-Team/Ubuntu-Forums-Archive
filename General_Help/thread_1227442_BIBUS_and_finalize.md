---
title: "BIBUS and finalize"
date: 2009-07-30
forum: General Help
---

### Post by paloalto71 on 2009-07-30
I use Bibus 1.4 and openoffice 3. In ubuntu or kubuntu 9.04- doesn't change
everything works fine, but when I try to finalize, bibus freezes

I tried to start it from terminal, and during the finalize step I got:

File "/usr/share/bibus/BibFrame.py", line 1499, in onMenuOOoFinalize
self.doc.finalize()
File "/usr/share/bibus/OOo.py", line 96, in finalize
bibOOoPlus.finalize(self,msg.Update)
File "/usr/share/bibus/bibOOo/bibOOoPlus.py", line 103, in finalize
cit_fuse,cit_separator,cit_order,cit_asc = self.bibStyle['citation']['ad']
ValueError: too many values to unpack

any ideas?

Thanks

---

### Post by siminm on 2009-11-10
I'm using Ubuntu 9.10. I installed Bibus via apt-get and everything works great except the Finalize step. 

Instead of freezing Bibus complains
[IMG]http://i34.tinypic.com/33xhbgp.png[/IMG]
Even if the file is already saved, or if you click yes, this box pops up and won't go away till you click No.
Running it from the shell does not spit out any errors. Running as root doesn't resolve this issue either.

---

### Post by siminm on 2009-11-11
I've reinstalled Bibus from their own source (1.5.0), instead of ubuntu's apt-get, and the error changed to freezing instead of an infinate loop.
Changing the following solved this issue for me:


/usr/share/bibus/bibOOo/bibOOoBase.py line [s]749[/s] 748 (pointed out by space_agent)

replace **"private:stream"** with **self.model.getLocation()**
Note: "private:stream" is a string in quotation marks, self.model.getLocation() is a function NOT in quotation marks

Someone please confirm this.

---

### Post by reuterr on 2009-11-14
Hello Siminm,
Thank you very much for your help. I have installed 
[http://sourceforge.net/projects/bibus-biblio/files/debian/bibus-1.5.0/bibus_1.5.0-1_all.deb/download](http://sourceforge.net/projects/bibus-biblio/files/debian/bibus-1.5.0/bibus_1.5.0-1_all.deb/download)
on Ubuntu 0910 and had also that finalize problem.
With your patch it works now :D
Best regards, Rudolf
p.s.
How did you figure that out?
I also searched in this area with winpdb, but no success.

---

### Post by siminm on 2009-11-14
The error stated that the URL was not in a correct format, but most instructions said to use "private:stream" or "file:///..."
Since the location of the file is up to the user, I had to resort to the location function

---

### Post by space_agent on 2009-12-01
Great simnm, you're a genius. Worked for me too. the only thing is that it is on line 748 (ok not too far away from 749:) and it is important to get rid of the commas, which although pointed out already by you I missed in the first place. Thanks again!

---

### Post by pveurshout on 2010-01-06
Thanks for your solution! Haven't tried the fix yet, but this thread is bookmarked :) I had just finished working after a long, long, long day, so you can imagine how frustrated I was when Bibus refused to cooperate and I had to "finalize by hand"..

---

### Post by 80aless on 2010-07-15
EDIT: Thanks, without quotes it works! 
```

(self.model.getLocation(), "_default",0,pvDescriptor)
```

---

### Post by jgratero on 2010-11-22
Didn't work for me. I have a Lucid install on a Compaq CQ2009F, and even with this workaround, no luck at all.

The funny thing is that I have Bibus also on my laptop (Dell Inspiron 6400, Lucid install also) and it works! No workaround (or anything required)

I've even tried (as suggested by a web forum) that the problem might be on the python uno (possibly broken). No luck with the reinstall anyway.

---

### Post by jgratero on 2010-11-26
What actually worked for me was (as suggested on the Bibus Help Forums) to remove the OpenOffice and Bibus configuration folders from my home directory, an start from scratch. 

It did work this time...

---

### Post by profant on 2011-03-16
Unfortunately this fix somtime works and sometimes it does not. It seems to me as if it depended on the style I saved and always pasted into the newly created .bibus folder in my home folder. If someone has another advice, I would be very greatful. Or maybe if someone could recommend a different non-freezing open source program, which does the same job.

Thank you.

Tomas

---

