---
title: "Biggest bandwidth killer... my brother ..."
date: 2006-06-17
forum: General Help
---

### Post by kthakore on 2006-06-17
My brother and I are sharing our internet connection through a WRT54GS linksys router, and whenever he is downloading anything I completly lose my internet connection, btw he has a winxp home. What can I do? Also he keeps closing the ports to my apache server on the router config, is there any way pass this? plz help as I am ding here. And ... no .. I can't beat him up:sad:

---

### Post by 23meg on 2006-06-17
Tell him to limit his connection speed with bandwidth control software for Windows.

---

### Post by kthakore on 2006-06-17
I don't think he would do that as he is an ...

---

### Post by nephesh on 2006-06-17
uninstall TCP/IP from his computer?

---

### Post by kthakore on 2006-06-17
how would I do that?

---

### Post by caldevil on 2006-06-17
Put some virus on his compuer :D

---

### Post by kthakore on 2006-06-17
srry I am a n00b but how would I do that (Ps to the admins of the forum I bought the computer he is using so it is not hacking rite?) ? I just want to put a little fear of god in him, because I work for a company doing SAP stuff, and I need to be connected to their servers 24/7, but because my brother is an a@#@$@# he will completly kill the bandwidth, because he wants to watch a movie. Also if anyone knows how I can prevent him from changing the port forwarding on the router, I would be so happy.

---

### Post by scxtt on 2006-06-17
if you have access to the router, log in and change the admin password -- of course if he can beat it out of you - it's not gonna be of much good ...

---

### Post by kthakore on 2006-06-17
I have access to it and even if i did change it my bro with hard restart it and change the admin again when I am not at home.

---

### Post by treris on 2006-06-17
basically anything you do then depends on his willingness to cooperate because he can of course undo almost anything you might do to his computer
I understand from your post that reasoning with him does not really seem to work, maybe you can come to an agreement about downloading times, assuming you normally aren't working 24/7 from your house you should be able to make a deal with him only downloading full throttle when you're away from home

that would probably be the easiest solution

PS you could also send him a letter appearing to come from your local copyrights agency claiming they have been monitoring your ip address and are considering legal steps and what not, that might (temporarily) put a stop to his downloading  movies and stuff

---

### Post by Patrick-Ruff on 2006-06-17
hehe, I've read some stuff about some spoofing methods to literally nock people off the internet, there are many steps you can take towards this really. think like a hacker :). I'm not going into details however, because it is, very much illigal in real life and on these forums to discuss actual hacking methods, all I can tell you is that most of the tools you need are already built into Linux, remember, linux has a well earned reputation for hacking...take atvantage of that repuation. he can't hack you back, hes on windows ;).


your as secure as your root password.

---

### Post by unf on 2006-06-17
[QUOTE=caldevil]Put some virus on his compuer :D[/QUOTE]
Great :D This is LOCK UP the interwep virus for bro :razz:

---

### Post by disturbed1 on 2006-06-17
Hold down the windows key and press r    in the run dialog type regedit, press enter

Delete the winsock and winsock2 entries in 
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\


windows key -> r / in the run dialog type cmd.

This get's you to the command line type this in
netdiag /test:winsock

It should fail. 

Or -

windows key -> r / in the run dialog type Msinfo32

Expand Components, expand Network, and then click Protocol


You can play with WindowsXP firewall using these commands
netsh firewall set

Actually, you can do what you want to the Windows TCP/IP stack inside of netsh. 

To repair the damage you've done it's as simple as 
netsh winsock reset catalog    
and/or
netsh winsock reset
and/or
netsh int ip reset


You can also change the ACL's (access control lists) in regedit by going to 
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Ole\MachineAccessRestriction= ACL
and
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Ole\MachineLaunchRestriction= ACL


Be warned, playing with the winsock can make a system's TCP/IP stack completely unstable, and may prompt for a reinstall.

---

### Post by blkish on 2006-06-17
[QUOTE=kthakore]My brother and I are sharing our internet connection through a WRT54GS linksys router, and whenever he is downloading anything I completly lose my internet connection, btw he has a winxp home. What can I do? Also he keeps closing the ports to my apache server on the router config, is there any way pass this? plz help as I am ding here. And ... no .. I can't beat him up:sad:[/QUOTE]

other than the obvious solution of taking a hammer to his network card, which may not be the most diplomatic approach, the only reliable way i've found to manage congested connections is to implement some form of traffic shapping or Quality of Service (QoS).

if you happen to have an old computer lying around (even 486-dx/100 would suffice) you can do this using open source software.
i would recommend looking into m0n0wall - [http://www.m0n0.ch/wall/](http://www.m0n0.ch/wall/)
and pfSense (a port of monowall, solves different problems) - [www.pfsense.com](www.pfsense.com)

they are both excellent router/firewall platforms

monowall can run easily off a bootable CD and keep its configuration on a floppy drive. pfSense is also capable of this, but the installation is a little more involved.

the section of most interest to you under the m0n0wall admin interface would be 'traffic shaper' + 'magic shaper wizard' and 'NAT'.

good luck

blkish

ps: you could probably mumble something about it being more complicated and so it would be best you didn't give your brother the password ;)

---

### Post by llamakc on 2006-06-17
Put his computer up for auction on Ebay; or better yet, auction him off.

---

### Post by kthakore on 2006-06-17
Thanks for the replys, but if I did want to hack him from linux, where should I look (I am not asking to tell me here just point me to a place). And as for the windows method, he won't let me use my own compy (the one he is using). I would want to hack him because I want him to think he screwed something up.

---

### Post by FLeiXiuS on 2006-07-01
The only other shaping method out there is to stop him at the router.  At times of the day when he becomes a bit bandwidth hungry, log onto your router and block his IP address.  That'll shut off his connections to the internet and free up the bandwidth.  When he asks why the internet is down reply, "I think it's because your downloading so much you might want to limit that."  Or something simular.  Yeah that sounds corny, I know.  But it's simple yet effective.

Social Engineering, mhaha!

---

### Post by clarke.rainey on 2006-07-01
Well you said you bought the computer for him... that means you can take it back... tell him that if he does not allow you to implement some sort of bandwidth limiting... that you will take the computer back... and this your Job should have priority over his illegal activities...

---

### Post by jeremy on 2006-07-02
It is actually quite simple; install DD-WRT on your router (get it from [www.dd-wrt.com)](www.dd-wrt.com)), and then you will be able to set (limit) his bandwidth from within the router settings

---

### Post by kthakore on 2006-07-08
I came up with a simple way I just arpspoof him and don't forward any of his bandwidth effectively slowing it down and more for me. heh heh he

---

### Post by kthakore on 2006-07-08
of ocurse I don't do arp posioning as that is just wrong no matter how evil he is.

---

### Post by T700 on 2006-07-08
Some problems just cry for a social solution, versus a technical fix.  You say you have a job; move out and get your own place.  There are advantages to being a grownup.

Paul

---

### Post by vem0m on 2006-07-09
lock him out of the router with a new pasword i use the same router u cna set a priority to give urself a higher one then his which basically means u would be higher on the chain to get speed to do that 
type [http://192.168.1.1/](http://192.168.1.1/) in your browser enter the password to get into the settings then Applications & Gaming  > QoS then in what ever ur computer is plugged into port wise in the Ethernet Port Priority list set it to High priority should take effect imediatly and give u higher speed if needed even if hes d/ling

---

### Post by kthakore on 2006-07-12
I agree to what you are saying paul but there is only so much S&*( I can take u know?

---

