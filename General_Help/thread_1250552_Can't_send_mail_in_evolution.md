---
title: "Can't send mail in evolution"
date: 2009-08-26
forum: General Help
---

### Post by scrambledarthur on 2009-08-26
Greetings all,

Is anyone having trouble sending mail in evolution?

I'm using a gmail account with an smtp server. I checked where my mail's going to, and it says smtp.gmail.com. 

My account receives mail just fine, beautifully filtering out messages and placing them in my specific folders, but I'm having a bit of trouble figuring out how to send a message via evolution.

Thanks!

P.S. Does anyone know a way to fix the volume bug, where anything <60% maximum volume is inaudible, but anything after that goes up by leaps and bounds?

---

### Post by SuaSwe on 2009-08-26
Check that all your sound settings are maxed out in Alsa Mixer (Terminal, type alsamixer), so that you don't get any funny amplification issues. Other than that, I don't know about the sound. :)

Are you getting any sort of errors when sending? It's not unusual to require your internet provider's SMTP server and settings to send e-mails using POP clients.

---

### Post by jonobr on 2009-08-26
What port number and protocol are you using for the gmail smtp server?

---

### Post by scrambledarthur on 2009-08-27
How do I find out?

---

### Post by jonobr on 2009-08-27
Hello


When you set up Evolution, there was a bunch of settnigs you put in for connecting to Gmail, probably host and port number as well as protocols,
Do you remember what you put in? there should also be an option to look at the settings

---

### Post by DugDra on 2009-09-08
Hi
I had the same problem. Check your settings under <Edit> <Preferences> select your gmail account click edit, select Sending email tab, You need the following for gmail:
Server: smtp.gmail.com
Check Server requires authentication
Use secure connection TLS Encription
Authenttication
Type: Plain (I Think)
User Name: [email]yourusername@gmail.com[/email]  (you need the @gmail.com)

Hope this helps
Doug

---

### Post by feyon on 2009-09-08
**For the sending a mail in evolution you just follow the following link:**

[www.wonderhowto.com/how-to/video/how-to-send-email-with-evolution-in-ubuntu-linux-253672/](www.wonderhowto.com/how-to/video/how-to-send-email-with-evolution-in-ubuntu-linux-253672/)  -

---

### Post by ShutterAce on 2009-09-08
Was it working at one point?

Who is your ISP?

Have they changed anything on their mail servers?

I just had to chase down a similar problem a few weeks ago. My ISP had offloaded it's mail to Google and I use various doamains for different emails. I had to include a port number in my prefs to get the outbound mail routed properly. It sounds like you have the same problem.

---

### Post by Sgt-Slyde on 2009-09-08
I just set up Evolution yesterday evening myself and also had to play with it to make it work.  The Google website had some generic help files that were useful once I actually read what they said, not what I expected to see.  As DugDra wrote earlier make sure to include the "@gmail.com", don't mispell it "gmial" as I did, and the "Type:  Plain" setting worked for me.  I checked the box for "remember password" and it's now working fine.

---

### Post by Helloworld1 on 2009-09-11
I am currently experiencing similar problems.

I am using the following settings for sending email(I use IMAP on the same(default) account  for recieving).

Servertype SMTP
Server smtp.gmail.com
Server requires authentication
TLS encrytion
Type PLAIN
Username [email]myemail@gmail.com[/email]
Remember password

In the beginning it worked(although I can't remember what my settings were at that time). Suddenly, my email weren't being sent anymore. When I hit send/receive, my hotmail(POP) and gmail(IMAP) run just fine, but the progressbar of the Gmail smtp doesn't move.
I have tried different settings regarding the server ie smtp.gmail.com:587

Does anyone know what is wrong, or where I can find more information about what is wrong?

---

### Post by OfNoNation on 2009-12-11
I use Gmail and Evolution and the following works for me.

Server Type= SMTP
Server Address= smtp.gmail.com:465  (remember to add the port number)
server requires Authentication (ticked/checked)
Use Secure Connection= SSL (never tried TLS)
Authentication Type= Plain
Username= user.name01   (definitely no '@gmail.com')
Remember Password (checked/ticked).

I hope this helps somebody.

What brought me here was a search for a simple SMTP server for Ubuntu 9.10, like I had in my Windows days, that will send my mail directly to the recipient's POP server and take smtp.gmail.com out of the process completely.

---

### Post by OfNoNation on 2009-12-11
That said, you must remember to go to Gmail's site and activate POP in your account settings. Though I'm not sure that's necessary in order to send mail via their smtp server.

---

