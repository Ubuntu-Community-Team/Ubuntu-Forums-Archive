---
title: "(XP) please help i got no way to go.."
date: 2010-04-14
forum: General Help
---

### Post by Marnix1 on 2010-04-14
There's something called "svchost.exe" My Virus scan detected it as a virus. but I dont now how to fix it :S can some one pelase help me? I read you need it to start serveral progams... Please help

Regards

---

### Post by howefield on 2010-04-14
Which anti virus application are you running ?

It is almost a certainty that they will have well populated and knowledgeable forums about what their software is picking up.

---

### Post by exodus_ on 2010-04-14
hey there.

Are you sure it's not detecting scvhost.exe??  It's a similar file that apparently exists.  I did a quick [google search]("http://www.google.ca/search?q=svchost.exe+virus&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") and I found [these instructions]("http://www.ehow.com/how_5132341_remove-svchostexe-virus.html") on how to remove it.

Why not try that and see if it helps?  If not I would suggest contacting the people who made your anti-virus application and see what they say.

Hope I can help.

---

### Post by QIII on 2010-04-14
svchost.exe is an important system file that Windows uses to allow the  system to hook .dlls (dynamic link library).  dlls can't be "run" in  their own right.  They can only be called from .exe (executable) files  which are running.  So svchost.exe provides that functionality.

svchost.exe is not itself a virus, but it can be used as a weak point  for viruses to do what they do.  What your scanner may have found is  suspicious use of svchost.exe.

To help, we would need to know the Virus scanner you are using (as asked above) and the exact text of the message you are getting from the scanner.

---

### Post by lisati on 2010-04-14
If memory serves correctly, there's a real file in some versions of Windows called svchost.exe **Don't blindly delete it without double checking!** Stand by with your Windows repair toolkit (recovery CD etc), just in case.

---

### Post by Marnix1 on 2010-04-14
Well i have the Anti virus called : Norman. It's in the quarantine now but when i replace it it detect it again and now well i dont know what to do

---

### Post by QIII on 2010-04-14
I think you are on the right track there, exodus_.  The exact text given by the scanner would make that obvious, I would hope...

---

### Post by elliotn on 2010-04-14
get avast and scan ur system and if its a virus it will clean it, but if it is a system file and has been deleted, just search it in a xp cd and paste it WINDOWS/SYSTEM32 or search good on were it should be

---

### Post by elliotn on 2010-04-14
btw avast or avira are the best I ever used

---

### Post by exodus_ on 2010-04-14
Can you paste the exact message you are getting from norman AV?  Does your AV function under windows safe mode?

Try running your AV under safe mode, and try those links I posted earlier ;)

If you are still having troubles after that let us all know with specific messages or errors that you are getting.

---

### Post by Peter Fjelstrup on 2010-04-16
Svchost is not the virus but it promotes it. When Norton has taken care of the infected file, you need to find the place in the register where the virus is triggered. Norton virus removal on the web tells you where according to ther name of ther virus. Usually it is in Hot Key Local mashine or Current user> Software>Microsoft>Windows>current user>run. There should be an indication af the name of the virus.

Run>regedit

---

### Post by goldshirt9 on 2010-04-16
also obtain 
**[SIZE=2]Malwarebytes Anti-Malware[/SIZE]**

run and follow instructions.one of the best around

you could run [http://free.antivirus.com/hijackthis/](http://free.antivirus.com/hijackthis/)
Hijack this and post the results on the relevant forum. not too bad prog.


this is a good site for av help etc etc
[http://pc-babble.blogspot.com/](http://pc-babble.blogspot.com/)

---

