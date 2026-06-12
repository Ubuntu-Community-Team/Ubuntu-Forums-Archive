---
title: "xauthorization cannot copy (cant update)"
date: 2006-04-27
forum: General Help
---

### Post by cjmartinez on 2006-04-27
i had posted to this same topic in absolute beginner section but i am assuming that more experienced users dont usually go into that forum so i'm posting the same issue again.  I went to try and run update manager/synaptic and it is giving me an error message saying cannot run usr/bin/synaptic due to not being able to copy /Xauthorization file, i received a reply on it saying that i should just delete it. I will try and do this but it seems as though there has to be a way to fix this problem without deleting it.  any thoughts?  also if i do delete it, is there any possibility of side effects or future issues relatd to this prob. 

another question, is there any recommended reading so that i may learn about things that i can do now that i have linux on my "used to be windows" pc?  i would eventually like to join and help the documentation team in future publications and would like to educate myself as much as possible, i have read through the ubuntu startguide and a couple of other docs but they pretty much stick to basics (refering to the ex-windows user) in regards to most comparable to windows

---

### Post by Ramses de Norre on 2006-04-27
Do you mean ~/.Xauthority? If so try ```
sudo chown username ~/.Xauthority && chmod 775 ~/.Xauthority
``` to make yourself owner of the file and make it readable, writeable and executable.
If it does not work try ```
rm ~/.Xauthority
``` it wont harm your system, a new and hopefully correct ~/.Xauthority file will be created.

---

### Post by cjmartinez on 2006-04-27
awesome man, i havent gotten to try it yet cause im at work but it givesme some hope at least. just out of curriosity, and since i am still technically a noobie, what does this "chmod 775 ~/.Xauthority" do as far as the "775" you refered to.  and while i am writing back to this, and if you know, what is the purpouse of the ~/Xauthority file do, i notice there are many people that say that they dont even have it.   also, i think the reason for this error may be because i obviously didnt read enough documentation before experimenting with the fun stuff.  is there any docs that go over fun stuff to do with this newly installed ubuntu, as far as eyecandy, games...

---

### Post by Ramses de Norre on 2006-04-27
chmod: change permissions, three digits: first owner permissions, second group permissions (owners primary group), third world permissions (everyone else)
r=read=4
w=write=2
x=execute=1
Add the values for the permissions for each user and that gives you a single digit.

For the doc's: browse the forums, I've learned most of the things I know here by reading problems and their solutions. And read the man pages on commands to learn them better (man command_name).

---

### Post by cjmartinez on 2006-04-27
bro, thanks for the info, i was assuming that the read write commands were just like in dos ie: -r -w -x,

---

### Post by mrfuzzemz on 2006-10-14
Thanks Ramses! That did the trick!

---

### Post by Doppelbock on 2006-12-10
I was getting the same error posted to start this thread and when I checked my home directory .XAuthority was set to -rw------- so I followed your advice on the chmod and I'm good to go now with permissions showing as -rwxrwxr-x which seems like it's too permissive. I would have thought that rwx for owner would be enough so I did a chmod to 700 and it still appears to be working fine.

---

### Post by mlb on 2008-02-14
Actually often error reason is the file does not exists. I would suggest to use following:

```
sudo touch ~/.Xauthority && chown $LOGNAME  ~/.Xauthority && chmod 775 ~/.Xauthority
```

:guitar:

---

### Post by LeDechaine on 2008-02-28
Yeahoo, thanks a lot, Ramses de Norre, you saved me. :D

---

