---
title: "MSN on Empathy stopped working"
date: 2011-11-07
forum: General Help
---

### Post by Alwimo on 2011-11-07
Has MSN on Empathy stopped working for other people? It hasn't been working for me for the past few days.

It just keeps on trying to connect, and doesn't come up with a fail message.

---

### Post by Punksolid on 2011-11-07
Same problem here, some people say that on pidgin it is working. Just in pidgin, not EMESENE or another client.

Normally this is because Microsoft changes protocol often.

---

### Post by gamblor01 on 2011-11-07
It is working for me (connecting at least).  I'm not sure but maybe your server is different than the one I am connecting to in the US?

Most of us use MSN accounts at work to message each other.  I have had constant problems with it not properly sending/receiving messages to at least 3 different co-workers.  Since then I have been switching to Google chat where possible.  I don't know if this is a problem with the telepathy-butterfly framework (which Empathy uses to connect to the MSN service) or if it's an issue with the MSN service itself.

I'd say ditch the MSN account if you have the luxury...



**EDIT:** I found this morning that my account has stopped working as well.  Strange because it worked fine all day yesterday...

---

### Post by seth_reaver on 2011-11-07
It stopped working for me as well, US, Ubuntu 11.10 fully updated. It just keeps trying to connect. Pidgin didn't work either so i wonder if Microsoft changed their server.

---

### Post by oyvinst on 2011-11-08
Confirmed, it has stopped working here as well (a day ago or so). Empathy on Ubuntu 10.04 Lucid. The logon process seems to hang indefinitely. :-|

---

### Post by oyvinst on 2011-11-08
I made a bug report, please do tell if the problem affects you:
[https://bugs.launchpad.net/ubuntu/+source/telepathy-butterfly/+bug/887481](https://bugs.launchpad.net/ubuntu/+source/telepathy-butterfly/+bug/887481)

---

### Post by Alwimo on 2011-11-08
I clicked that it affects me too. I was going to create a bug for it but am a bit nervous about doing it incorrectly.

I'll be using Pidgin, which is connecting properly. 

Thanks for all the responses. :)

---

### Post by FallenUnia on 2011-11-08
Maybe related?

[http://ubuntuforums.org/showthread.php?t=1875101](http://ubuntuforums.org/showthread.php?t=1875101)

I filed a bug report on it on the kdenetwork page and it was confirmed. Meanwhile, as you can read in the post, I'm using Kmess with a patch and that works.

---

### Post by razor7 on 2011-11-08
Hi, same issue from yesterday!

Attaching butterfly (msn) lof file

---

### Post by razor7 on 2011-11-08
Solved!!! in file /usr/share/pyshared/papyon/service/description/AB/__init__.py (as root "sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py") change line 23 from this
```
url = "http://contacts.msn.com/abservice/abservice.asmx"
```
to this
```
url = "http://local-bay.contacts.msn.com/abservice/abservice.asmx"
```

Reboot and test it, it's working for me!

---

### Post by kneeki on 2011-11-08
> **razor7 said:**
> Solved!!! in file /usr/share/pyshared/papyon/service/description/AB/__init__.py (as root "sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py") change line 23 from this
```
url = "http://contacts.msn.com/abservice/abservice.asmx"
```
to this
```
url = "http://local-bay.contacts.msn.com/abservice/abservice.asmx"
```

Reboot and test it, it's working for me!I just tried this, did not work for me. :(

edit: Works now... Didn't make any changes, just took getting a new cup of coffee?

---

### Post by gamblor01 on 2011-11-08
> **kneeki said:**
> I just tried this, did not work for me. :(

Yeah this doesn't work for me either.

---

### Post by dtzortzis on 2011-11-08
> **razor7 said:**
> Solved!!! in file /usr/share/pyshared/papyon/service/description/AB/__init__.py (as root "sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py") change line 23 from this
```
url = "http://contacts.msn.com/abservice/abservice.asmx"
```
to this
```
url = "http://local-bay.contacts.msn.com/abservice/abservice.asmx"
```

Reboot and test it, it's working for me!
I can confirm this worked for me ;)
Thanks!

BTW, how did you find out the solution?

---

### Post by gamblor01 on 2011-11-08
> **dtzortzis said:**
> I can confirm this worked for me ;)
Thanks!

BTW, how did you find out the solution?

This still isn't working for me after several reboots.  I would also be interested to know how you came to this solution, both out of curiosity as well as information that may help me resolve the problem on my system.  Thanks!

---

### Post by solorzanomd on 2011-11-08
Thanks a lot for your help, I was looking for an answer. I have tried everything, but your solution was the only one that works. Thanks.

---

### Post by solorzanomd on 2011-11-08
I don't know how but to me works restarting the system. Try with this.

---

### Post by cnvandev on 2011-11-08
> **razor7 said:**
> Solved!!! in file /usr/share/pyshared/papyon/service/description/AB/__init__.py (as root "sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py") change line 23 from this
```
url = "http://contacts.msn.com/abservice/abservice.asmx"
```to this
```
url = "http://local-bay.contacts.msn.com/abservice/abservice.asmx"
```Reboot and test it, it's working for me!

This worked for me as well. You can also avoid rebooting by killling every empathy/telepathy-related process and then restarting Empathy to bring them all back up. I used ```
ps ax | grep pathy
``` to find 'em all, then killall <name of process> to kill them.

---

### Post by Erik1984 on 2011-11-08
[http://askubuntu.com/questions/76948/problems-connecting-msn-with-empathy](http://askubuntu.com/questions/76948/problems-connecting-msn-with-empathy)

I can confirm that the second idea, removing telepathy-butterfly, also works. However changing the server address is probably a nicer solution :P

---

### Post by Drowz0r on 2011-11-08
> **razor7 said:**
> Solved!!! in file /usr/share/pyshared/papyon/service/description/AB/__init__.py (as root "sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py") change line 23 from this
```
url = "http://contacts.msn.com/abservice/abservice.asmx"
```to this
```
url = "http://local-bay.contacts.msn.com/abservice/abservice.asmx"
```Reboot and test it, it's working for me!

Hello

Do you have a little more detail on this?

I've only been using ubuntu for around a week so I'm not sure on all the tricks yet.

Thanks

----

edit: Actually, got it now. Had to run it through the terminal before it would let me save it correctly.

---

### Post by seth_reaver on 2011-11-08
> **razor7 said:**
> Solved!!! in file /usr/share/pyshared/papyon/service/description/AB/__init__.py (as root "sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py") change line 23 from this
```
url = "http://contacts.msn.com/abservice/abservice.asmx"
```
to this
```
url = "http://local-bay.contacts.msn.com/abservice/abservice.asmx"
```

Reboot and test it, it's working for me!

Confirmed. Works now, took a few minutes, but after full restart it worked fine.

---

### Post by euroford on 2011-11-09
> **razor7 said:**
> Solved!!! in file /usr/share/pyshared/papyon/service/description/AB/__init__.py (as root "sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py") change line 23 from this
```
url = "http://contacts.msn.com/abservice/abservice.asmx"
```
to this
```
url = "http://local-bay.contacts.msn.com/abservice/abservice.asmx"
```

Reboot and test it, it's working for me!
local-bay.contacts.msn.com won't work, but local-sn.contacts.msn.com works for me.

---

### Post by LaptopU on 2011-11-09
Thanks, works for me, I set my status to offline on Empathy so it wasn't trying to connect, closed Empathy, edited the file, then clicked 'chat' again via the notification icon and it connected.

---

### Post by kuvanito on 2011-11-09
Thank You!
This worked for me also. :)

---

### Post by miguelpires on 2011-11-09
I can confirme that work form me!! Thank's for sharing

---

### Post by moemac57 on 2011-11-09
I am from Canada and I have tried everything in this post but MSN is still not working for me???? I have tried bay and sn still keeps trying to connect... I read all you guys and it is working for you. I hate Micro$oft but I have a lot of clients on MSN ARGH!!!!!!

Anyone? Can you help??
Thanks.

---

### Post by gamblor01 on 2011-11-09
> **moemac57 said:**
> I am from Canada and I have tried everything in this post but MSN is still not working for me???? I have tried bay and sn still keeps trying to connect... I read all you guys and it is working for you. I hate Micro$oft but I have a lot of clients on MSN ARGH!!!!!!

Anyone? Can you help??
Thanks.

Yesterday I spent all day at work with hotmail.com open and I was logged into the messenger service through there.  This was a pain but it works.

Alternatively you can try using Pidgin instead of Empathy.  My co-worker had no problem connecting with Pidgin but my system (Empathy) wouldn't connect at all, even to the local-bay.contacts.msn.com URL.  I just now changed it to local-sn and it took a few minutes but finally connected.  I did exactly what LaptopU suggested:

- open Empathy and set status to offline
- use CTRL+Q to quit (or you can select it from the main menu)
- edited the file to use the local-sn address
- clicked on the chat icon from the top panel to start Empathy


When it first opened I saw the little progress indicator continually spinning and only my Google chat contacts showed up.  I closed the program and went back to opening hotmail.  A few minutes later I went to open my contact list in Empathy and suddenly all of my contacts were there.  Maybe try opening it and giving it a few minutes...it seemed to eventually connect now that I am using "http://local-sn.contacts.msn.com/abservice/abservice.asmx"


I'm in the USA -- hopefully it isn't some geographical restriction but considering this is an M$ service I wouldn't be surprised.

Good luck.

---

### Post by Andrea9 on 2011-11-09
> **euroford said:**
> local-bay.contacts.msn.com won't work, but local-sn.contacts.msn.com works for me.
Thank You!
This worked for me.

---

### Post by papatrexas on 2011-11-09
> **razor7 said:**
> Solved!!! in file /usr/share/pyshared/papyon/service/description/AB/__init__.py (as root "sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py") change line 23 from this
```
url = "http://contacts.msn.com/abservice/abservice.asmx"
```
to this
```
url = "http://local-bay.contacts.msn.com/abservice/abservice.asmx"
```
Reboot and test it, it's working for me!
Perfect! It's also working for me! Thanks a lot!

---

### Post by Alwimo on 2011-11-09
Thanks. It worked for me as well.

---

### Post by ElQanah on 2011-11-09
> **dtzortzis said:**
> I can confirm this worked for me ;)
Thanks!

BTW, how did you find out the solution?

I also confirm.  working with this as well.

---

### Post by Zvlwab on 2011-11-10
> **euroford said:**
> local-bay.contacts.msn.com won't work, but local-sn.contacts.msn.com works for me.

Thanks! this worked for me too

---

### Post by euroford on 2011-11-10
Today I turned to [https://local-sn.contacts.msn.com](https://local-sn.contacts.msn.com), it's faster than [http://local-sn.contacts.msn.com](http://local-sn.contacts.msn.com) :P

---

### Post by Zvlwab on 2011-11-10
About an hour ago ```
url = "http://local-sn.contacts.msn.com/abservice/abservice.asmx"
``` worked for me, but suddenly it doesn't work anymore

---

### Post by Naue on 2011-11-10
> **Zvlwab said:**
> About an hour ago ```
url = "http://local-sn.contacts.msn.com/abservice/abservice.asmx"
``` worked for me, but suddenly it doesn't work anymore


Thats URL (https://local-sn.contacts.msn.com/abservice/abservice.asmx) worked for me now. Thanks.

---

### Post by Zvlwab on 2011-11-10
It suddenly works again somehow. Also I've been trying to write a script to login to msn myself (not very successfully though), but I do know that it accepts both HTTP and HTTPS connections for the SOAP request it uses this url for.

---

### Post by InsektO on 2011-11-10
Thanks, i was really looking for a solution to this. Didn't need to reboot.

---

### Post by d3v1150m471c on 2011-11-10
try pidgin

---

### Post by ubuntu27 on 2011-11-11
I am also experiencing the same thing.


Here is the LP Bug Report: 

[https://bugs.launchpad.net/ubuntu/+source/papyon/+bug/887349](https://bugs.launchpad.net/ubuntu/+source/papyon/+bug/887349)

---

### Post by Astronaut356 on 2011-11-11
> **razor7 said:**
> Solved!!! in file /usr/share/pyshared/papyon/service/description/AB/__init__.py (as root "sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py") change line 23 from this
```
url = "http://contacts.msn.com/abservice/abservice.asmx"
```
to this
```
url = "http://local-bay.contacts.msn.com/abservice/abservice.asmx"
```

Reboot and test it, it's working for me!

Tried your fix but all I see is an empty file . If I navigate through the file system via the GUI I can find the file but I can't change anything because I don't have the right permissions. Why can't I open the file with the terminal?

---

### Post by dtzortzis on 2011-11-11
> **Astronaut356 said:**
> Tried your fix but all I see is an empty file . If I navigate through the file system via the GUI I can find the file but I can't change anything because I don't have the right permissions. Why can't I open the file with the terminal?

Go to Applications -> Accessories -> Terminal 
Then type:
```
sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py
```

That's the file you have to edit. You will find the mentioned line very easily. Good luck!

---

### Post by Astronaut356 on 2011-11-11
> **dtzortzis said:**
> Go to Applications -> Accessories -> Terminal 
Then type:
```
sudo gedit /usr/share/pyshared/papyon/service/description/AB/__init__.py
```

That's the file you have to edit. You will find the mentioned line very easily. Good luck!

Tried it again and what I get is in the attached screen shot. I don't understand the error message in the terminal.

---

### Post by robarm38 on 2011-11-11
> **Naue said:**
> Thats URL ([https://local-sn.contacts.msn.com/abservice/abservice.asmx](https://local-sn.contacts.msn.com/abservice/abservice.asmx)) worked for me now. Thanks.
Neither one works for me.  I'm connecting from Japan. Would that make a difference?

---

### Post by huwjenjinn on 2011-11-12
Terrific stuff.

[http://local-bay.contacts.msn.com/abservice/abservice.asmx](http://local-bay.contacts.msn.com/abservice/abservice.asmx)

worked for me on:

lucid 10.04
Empathy 2.30.3

in the UK

---

### Post by brain270 on 2011-11-12
thank you razor7!!!! 
it worked for me too.

---

### Post by hkxyz on 2011-11-14
The above recommendations didn't work however updating python-papyon to 0.5.5-1 worked for me.

---

### Post by moemac57 on 2011-11-15
> **hkxyz said:**
> The above recommendations didn't work however updating python-papyon to 0.5.5-1 worked for me.

Would you be kind enough to describe the steps on how you did this? I would like to try it.

Thanks!

---

### Post by ubuntu27 on 2011-11-15
For temporal solution, I am using [emesene Instant Messenger]("http://blog.emesene.org/") which has already fixed the issue.
They have a Official PPA.


[http://blog.emesene.org/](http://blog.emesene.org/)

---

### Post by Devilman13 on 2011-11-16
> **moemac57 said:**
> Would you be kind enough to describe the steps on how you did this? I would like to try it.

Thanks!

Not much need. It's an older version now.

**None** of these solutions work for me. Haven't tried emesene yet.

---

### Post by davfigue on 2011-11-17
For those that still have problems, verify that you dont have the package **telepathy-butterfly** installed

for uninstalling:
```
sudo apt-get --purge remove telepathy-butterfly
```

Regards,

---

### Post by Devilman13 on 2011-11-18
Last update fixed this for me automatically.

---

### Post by Alwimo on 2011-11-19
Yes, it's working again without doing any fiddling for me too. :)

---

### Post by papibe on 2011-11-19
I received the python-papyon update on both of my systems, but that did not solve the problem by itself.

In 11.04 I had to do this after to got it working:
```
sudo dpkg-reconfigure python-papyon
```

But in 10.04 the problem still persists.

Regards.

---

### Post by eejit on 2012-02-07
> **davfigue said:**
> For those that still have problems, verify that you dont have the package **telepathy-butterfly** installed

for uninstalling:
```
sudo apt-get --purge remove telepathy-butterfly
```Regards,


this seemed to work for me! thanks

---

