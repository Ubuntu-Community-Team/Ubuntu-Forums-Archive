---
title: "help me im fed up wih this issue"
date: 2010-03-28
forum: General Help
---

### Post by Nisal on 2010-03-28
hey guys i need a solution for this im using USB dongal for connect to internet..every time i have to connect and disconnect 10-15 times to get page loaded,i mean it shows as connected but still i can load the pages ,what can be the problem ?


[IMG]http://i39.tinypic.com/2dkzsic.png[/IMG]

---

### Post by linden940 on 2010-03-28
give me the FULL name/model of the wireless card you are using...

is it a usb or one thats inside the computer?

i think i may know what the problem is but i need to know the wireless card make/model

---

### Post by Nisal on 2010-03-29
its huawei E156G

---

### Post by linden940 on 2010-03-29
ok well its supported....so thats not the case...or it was in 9.04 so i dont see why it wont be in 9.10

anyway i did alittle poking around and this seems like something u may want to try...its a forum that has a link..i think you should click on the link but showing you where i had found this info out

[http://forum.huawei.com/jive4/thread.jspa?threadID=327858&tstart=0&orderStr=null](http://forum.huawei.com/jive4/thread.jspa?threadID=327858&tstart=0&orderStr=null)

---

### Post by linden940 on 2010-03-29
hmm fast ? i like to ask...can you ping Google?

---

### Post by jimv on 2010-03-29
If you can't get to any websites, you should check to see if you have an IP address.  You can check that by typing ifconfig into a command line.

---

### Post by crlang13 on 2010-03-29
Where are you located?  My girlfriend has a huwai usb dongle for internet access and when using Windows or Ubuntu we very often are able to "connect" but then experience little or no connectivity when trying to surf the web (just like you).  She lives right on the edge of a blackspot that even the ISP recognizes is there.

Have you tried using your computer somewhere that's not your house?

---

### Post by Nisal on 2010-03-29
ok when i try several time i can connect but for that i have to disconnect and reconnect gain and again

---

### Post by Nisal on 2010-03-29
> **linden940 said:**
> hmm fast ? i like to ask...can you ping Google?

i can when it shows like that in fact u can see i was trying to load google and got that msg

---

### Post by 3rdalbum on 2010-03-29
Upgrade to Lucid (Ubuntu 10.04), it fixes the problems with mobile broadband that were present on 9.10.

---

### Post by Nisal on 2010-03-29
> **3rdalbum said:**
> Upgrade to Lucid (Ubuntu 10.04), it fixes the problems with mobile broadband that were present on 9.10.

hmm il try it

---

### Post by 3rdalbum on 2010-03-29
> **Nisal said:**
> hmm il try it

Oh by the way: When I say "upgrade", I mean do a fresh install of Ubuntu 10.04 Beta 1 or a daily image.

---

### Post by Nisal on 2010-03-29
> **3rdalbum said:**
> Oh by the way: When I say "upgrade", I mean do a fresh install of Ubuntu 10.04 Beta 1 or a daily image.

fresh ? huh that mean il lost all the softz i had installed ?

---

### Post by Nisal on 2010-04-01
bump i still didn't get solution for this any more help ?

---

### Post by scouser73 on 2010-04-01
It might be your DNS settings, meaning that every time you try to connect to a web site it's not fully resolving.

I use Google Public DNS, go to: [[COLOR="Red"]**Google Public DNS**[/COLOR]]("http://code.google.com/speed/public-dns/docs/using.html") and follow the instructions to see whether it fixes the problem you're having.

---

### Post by Jeffster999 on 2010-04-01
I had a similar problem with my broadband rtr as well...I eventually got frustrated and reset it to factory specs(holding the reset key for 15 secs)

Once that was done I was able to log on to the web with NO security (only a temporary fix)

Once I was able to connect, I went through the settings (in the rtr) and tried to connect.

You get the idea, I know it is tedious but ultimately it worked

---

### Post by Grenage on 2010-04-01
I'm with **scouser73**, every mobile web dongle I've used, that had problems, was fixed by manually specifying DNS addresses in the Network Manager applet.

I used Google's DNS servers, you could use any.

---

### Post by Nisal on 2010-04-04
okay i configured Google DNS.. and i verify it as it says , i think this is mean it ok right ?

[IMG]http://i42.tinypic.com/2cerls7.png[/IMG]

edit it solved the problem :)

---

