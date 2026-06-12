---
title: "empathy not connecting"
date: 2009-12-30
forum: General Help
---

### Post by charonred on 2009-12-30
I've just installed karmic 9.10, and have been busy migrating items from Hardy.

Though this Empathy messenger client seems very buggy. I can connect to my instant messenger/hotmail, but there's no way it will connect to either my gmail/googletalk, or to my yahoo messenger.

I have deleted the accounts a few times and created new ones, but both  suffer 'network error'

---

### Post by zine92 on 2009-12-30
Maybe try renewing/changing your pass to a shorter one. For me, i had the same problem but only with my hotmail, at first i didn't know what to do, even pidign works for me, after that, i try changing my old pass to a shorter one and i can log in. Hope that helps.

---

### Post by charonred on 2009-12-30
same accounts (username & password) worked fine in Pidgin, and still do if I boot into Hardy.

But Empathy doesn't want to work with either Yahoo or gtalk/gmail accounts, so it seems the problem is with Empathy.

---

### Post by omkardanke on 2010-01-30
I seem to be having the same problem, I too have gmail and yahoo accounts and i cannot connect to them using empathy. This is the first time i am using empathy though i have used pidgin and kopete before I could connect from those two.

Empathy shows no sign that it is trying to connect to the servers. Also it only shows the connect button when the account is being made. This button too does not seem to do anything other than just save the settings.

Sigh.... pidgin was better....

---

### Post by Troll_the_Great on 2010-01-30
Same problem here. If somebody finds an answer I will be grateful.

---

### Post by blueshiftoverwatch on 2010-01-30
I sometimes have problems with Pidgin where I can't connect to some (or all) of my IM accounts. I think it has something to do with my ISP randomly dropping ports. I always just fixed this by hitting the reset button on my Comcast router*.

On Windows I think theirs a command you can use to get around having to do anything physically. It's something like *dumpdns*. I don't know about Linux.

*In case you were wondering. The black box Comcast gives you to connect to the Internet aren't isn't actually a modem, it's a router. A modem connects one computer to the Internet. A router connects one network (your home LAN) to the Internet (essentially, a very large WAN). They just call them modems so that the non-tech savvy won't get them confused with their LAN router.

---

### Post by charonred on 2010-01-30
I don't think resetting the modem/router will help; I'm using Karmic full-time now and believe the problem lies with the messenger client because Pidgin is working fine, but Empathy just won't connect with the same messenger accounts.

Maybe when Lucid Lynx is released it might work, but for the moment I'll stick with tried and tested Pidgin (it might not have the 'features' of Empathy, but at least it works).

---

### Post by soctu on 2010-01-31
I have the same problem with empathy... None of my accounts connect. The only thing i think of is that empathy is configured with old address data to connect with the IM servers (yahoo, gmail etc..).

---

### Post by nucleuskore on 2010-02-04
I had trouble accessing Yahoo and GTalk servers from my institution. After poking around the internet and fiddling with the settings I managed to work out the settings as follows:

GTalk
[[IMG]http://img509.imageshack.us/img509/9382/gtalk.th.png[/IMG]](http://img509.imageshack.us/i/gtalk.png/)

Yahoo!
[[IMG]http://img509.imageshack.us/img509/8190/yahooe.th.png[/IMG]](http://img509.imageshack.us/i/yahooe.png/)

---

### Post by Troll_the_Great on 2010-02-04
> **nucleuskore said:**
> I had trouble accessing Yahoo and GTalk servers from my institution. After poking around the internet and fiddling with the settings I managed to work out the settings as follows:

GTalk
[[IMG]http://img509.imageshack.us/img509/9382/gtalk.th.png[/IMG]](http://img509.imageshack.us/i/gtalk.png/)

Yahoo!
[[IMG]http://img509.imageshack.us/img509/8190/yahooe.th.png[/IMG]](http://img509.imageshack.us/i/yahooe.png/)

For the yahoo account, you just changed the default port (5050) to 80? Because for me it doesn't work... :(
What version of empathy do you use?

---

### Post by nucleuskore on 2010-02-04
Empathy 2.28.1.1

For Yahoo! Messenger refer this port guide
[http://www.helpbytes.co.uk/yconnect.php](http://www.helpbytes.co.uk/yconnect.php)

---

### Post by omkardanke on 2010-02-09
@nucleoskore   Your gmail solution doesn't seem to be working with me. Yahoo was and is working nicely. The only thing is gmail.

---

### Post by nucleuskore on 2010-02-09
There is no one size fits all solution. I had this problem, I tried to wrok around it, and then thought I'll share what I managed to get working here, so I searched and found this thread, and made my post. You'll have to play around with the settings and try. Here are my references:

For GTalk
[http://www.google.com/support/talk/bin/answer.py?hl=en&answer=27930](http://www.google.com/support/talk/bin/answer.py?hl=en&answer=27930)
[http://www.ubuntugeek.com/howto-setup-voice-chat-with-google-talk-user-using-empathy.html](http://www.ubuntugeek.com/howto-setup-voice-chat-with-google-talk-user-using-empathy.html)
[http://helpforlinux.blogspot.com/2009/06/there-is-no-official-google-talk.html](http://helpforlinux.blogspot.com/2009/06/there-is-no-official-google-talk.html)

and for Yahoo! messenger
[http://www.helpbytes.co.uk/yconnect.php](http://www.helpbytes.co.uk/yconnect.php)

For MSN I use amsn, works fine for me.

---

### Post by tlikarish on 2010-02-10
I had trouble getting empathy working out of the box as well but was able to get things working by 

1) edit -> accounts
2) click advanced toggle
3) filling in talk.google.com 

All the other defaults worked, that was the only thing I had to change.

good luck!

---

### Post by charonred on 2010-02-11
did as suggested earlier, and accounts seem to be working (at least MSN/hotmail); only problem is using Empathy is I have to start it & unlock the keyring for it before it will run, .. how do I get Empathy to start automatically/unlock keyring when I start my PC

---

### Post by srirammanoj on 2010-02-13
Thank you . The yahoo messenger settings worked for me.

---

### Post by smared on 2010-03-29
got the same problem before and invest many time searching 
for help but didn't find a result.
i got it running now in a very simple way.
just go to synaptic package manager search for
empathy and if the result appear use the right mouse
to reinstall.

that's it.
good luck!

---

### Post by nicow on 2010-05-30
Hey, check on the advanced button and double check the** Server** field. 

My problem was actually there, my server field had:** scsa**.msg.yahoo.com and the correct one should be **scs.**msg.yahoo.com

After I removed the a at the end of scsa it started working fine.

---

### Post by nanang on 2010-06-24
> **nicow said:**
> Hey, check on the advanced button and double check the** Server** field. 

My problem was actually there, my server field had:** scsa**.msg.yahoo.com and the correct one should be **scs.**msg.yahoo.com

After I removed the a at the end of scsa it started working fine.

Thank u very much Nicow. Its work for me. Like your sugestion, i just delete the 'a' letter at 'scsa' in my server field.

---

