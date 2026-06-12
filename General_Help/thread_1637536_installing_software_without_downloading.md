---
title: "installing software without downloading"
date: 2010-12-04
forum: General Help
---

### Post by cracker89 on 2010-12-04
Say Ive installed a fresh copy of ubuntu on a new machine. I have an existing install on one machine. 

Due to restrictions on internet usage and access, I am unable to download all the softwares and packages from the internet onto the newly setup machine. 

Say I want to take some packages already installed on my pre-existing machine and install them on the new machine. 

Can it be done? [-o< [-o< [-o<

---

### Post by dFlyer on 2010-12-04
You can always burn the programs in /var/cache/apt/archive to DVD/CD and use dpkg -i to install them on your other computer provided they are both the same version of ubuntu. But than again it would be easier to clone your first computer and move it all in one easy sweep to the other computer using clonezilla.

---

### Post by cracker89 on 2010-12-04
Thanks Gary. 

Ill look up clonezilla! sounds interesting..

---

### Post by madjr on 2010-12-04
AptOnCD

---

### Post by cracker89 on 2010-12-13
> **madjr said:**
> AptOnCD
Elaborate?

---

### Post by piquat on 2010-12-13
You coud run APTonCD on the other machine and it will basically save install packages from the /var/apt... cache on the CD to be installed on the other PC.
 
I'd just go with the second suggestion.  They're all .deb packages in there.  Pull the ones you want out onto a CD and walk them over to the other machine.  Double clicking the .deb packages on the other machine should bring up the gdebi installer (I think that's installed by default) and install them.  I believe gdebi will take care of the dependencies also.

---

### Post by Frogs Hair on 2010-12-13
These links might be worth investigation. 

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

---

### Post by cracker89 on 2010-12-13
Thank u people. Busy with exams, so will try it out soon. Looks good..

---

### Post by cracker89 on 2010-12-14
A couple of doubts...

@piquat: " it will basically save install packages from the /var/apt... cache on the CD to be installed on the other PC."
I cant find "/apt" under the "/var" directory. 

I want to not use 3rd party software for this. 

And do the two installations of Ubuntu need to be exactly the same? 

Cheers...

---

### Post by piquat on 2010-12-14
> **cracker89 said:**
> A couple of doubts...

@piquat: " it will basically save install packages from the /var/apt... cache on the CD to be installed on the other PC."
I cant find "/apt" under the "/var" directory. 

I want to not use 3rd party software for this. 

And do the two installations of Ubuntu need to be exactly the same? 

Cheers...

I'm sorry, I really wanted you to refer to the second suggestion.  He's got it right, I was trying to spit it out from memory.  They should be in /var/cache/apt/archives.  Those .deb packages are really what you're downloading with synaptic.  And as he mentioned, it should come from a machine running the same version of Ubuntu.

---

