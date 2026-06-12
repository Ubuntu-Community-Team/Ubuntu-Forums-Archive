---
title: "Blacklisting"
date: 2009-08-10
forum: General Help
---

### Post by mit10 on 2009-08-10
Hello Everyone!

Let me first just say I am very new to Ubuntu. (3 days old). So far I am loving this OS. However, I have a couple issues that I am wanting to iron out while I continue to try to learn. 

One of the issues I am trying to tackle right now is the annoying "motherboard" beep. Whenever I shut down Ubuntu it gives out an obnoxiously loud beep. I was browsing through the forums and I read that you can blacklist spkr? make any sense?

Firstly, what the heck is blacklisting what does it do (try to keep it in laymins terms or if you use fancy/abreviated words please give a short description of what they mean) 

Secondly, I know how to slowly navigate the Terminal but I dont know how to change a file. I would try to figure it out like I have been these last three to four days but I seriously making myself do 10x's more work then I have to and I am not really learning a whole lot because I have a million questions. (this Ubuntu thing is a lot to swallow!)

So if you could please help me blacklist the motherboard speaker (if thats what I need to do)? 

P.S I dont want to unplug my speaker (unless thats the only answer)... I want to learn about ubuntu not the anatomy of my computer! Thanks Guys!

---

### Post by XCan on 2009-08-10
pcspeaker:
To disable it you have to tell Ubuntu to unload/not load the modules needed to run it. This can simply be accomplished by running ```
 modprobe -r pcspkr 
```

However, the pcspkr gets loaded every time the machine boots, hence you need to blacklist it to stop it from being loaded. This is done by adding
```
 blacklist pcspkr 
```
into 
```
 /etc/modprobe.d/blacklist 
```

Alternatively, you could also remove the module altogether using 
```
 rmmod pcspkr 
```
but I think simply blacklisting it is more elegant.

Change file:

I'm not sure what you mean with changing a file, do you mean editing a text file? You can do that with nano if you want a terminal based text editor or gedit if you want a gui editor. Use
```
 nano /path/to/file
gedit /path/to/file 
```

Add sudo in front for nano, and gksudo in front of gedit, if you are changing system config. files like /etc/modprobe.d/blacklist.

---

### Post by Yellow Pasque on 2009-08-10
Xcan, rmmod does not delete the module; it just unloads it like modprobe -r. Also, I would recommend the user simply create his/her own blacklist file (named <something>.conf) in /etc/modprobe.d instead of modifying the system file (it will make future system upgrades less painful).

All files in /etc/modprobe.d/ should have a .conf extension

---

### Post by mit10 on 2009-08-10
Dude, XCan... you rock my face off!

It worked and I greatly appreciate you helping me out!!

Thanks again!

Temujin:

How do I create a new .conf file in terminal.

I want take out the "blacklist  spkr" in modprobe.d/blacklist.conf and make my own blacklist and edit it as you suggested.

---

### Post by Yellow Pasque on 2009-08-10
For example,
```
gksudo gedit /etc/modprobe.d/myblacklist.conf
```

---

### Post by mit10 on 2009-08-10
Amazing Thank You both so much!! Both posts were extremely informative and every bit helps for someone who is new to Linux! Thanks again for your time guys!

---

### Post by XCan on 2009-08-11
> **Temüjin said:**
> Xcan, rmmod does not delete the module; it just unloads it like modprobe -r. Also, I would recommend the user simply create his/her own blacklist file (named <something>.conf) in /etc/modprobe.d instead of modifying the system file (it will make future system upgrades less painful).

All files in /etc/modprobe.d/ should have a .conf extension

Ah, you're right indeed about rmmod.

---

### Post by Sprawn! on 2009-08-11
This advice and example helped me a great deal as well. Thank you.

---

### Post by mwparis on 2009-08-11
Helpful information, thanks.

---

