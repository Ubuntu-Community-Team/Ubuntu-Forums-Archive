---
title: "Getting &quot;Hotmail/Live&quot; to work in 9.04 with Evolution"
date: 2009-09-02
forum: General Help
---

### Post by kenji_03 on 2009-09-02
We use to have to trick Hotmail to get it to send to a pop3 account, but recently M****soft decided to make pop3 available FOC from Hotmail.  This means no more of the "hotway hotsmtp" stuff[FONT=monospace].

[/FONT]For most of us, setting your account up like this is all you have to do
> **Paresh said:**
> 
Receiving email
Server Type = POP
Server = pop3.live.com
Secure Connection = SSL encryption

Sending email
Server Type = SMTP
Server = smtp.live.com
Secure Connection = TLS encryption

More info [here]("http://windowslivehelp.com/solutions/settings/archive/2009/01/06/send-and-receive-windows-live-hotmail-emails-from-a-mail-client.aspx")
For one reason or another your ports may be blocked, if that happens you need to set it up like this
> **pavlovscat said:**
> Incoming server: pop3.live.com:995
 Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password
 

Outgoing server: smtp.live.com:587
Server requires authentication: yes
Security: TLS
Authentication type: plain
 

Do **NOT **do this method (It will cause your hotmail to not sync even if the settings are right):
[Link (1) Here]("http://www.ubuntugeek.com/how-to-configure-evolution-to-use-hotmail-in-ubuntu-810-intrepid-ibex.html")
[Link (2) Here]("http://ubuntuforums.org/showthread.php?t=200408&highlight=evolution+hotmail")

If Evolution is still not working, make sure you didn't install **xinetd** (as the methods above tell you to) as that will cause problems with Evolution reading Hotmail now that it's :popcorn: free

Source Info:
[URL="http://ubuntuforums.org/showthread.php?t=1124293&highlight=hotmail+send+evolution+Jaunty"]Link Here
[/URL]

---

### Post by Speef on 2009-09-22
Thank you so much, setup was super easy. But I was having a bit of trouble and decided to just go to my hotmail and all of the emails that were in my inbox and now totally gone!(when I login just through firefox) is there a way that my evolution can import the emails without removing them from my online hotmail. jic my hd fails or something
\\:D/

---

### Post by tobep17 on 2009-09-28
Hi,

This procedure works fine with my inbox in hotmail but my personal folders, like archive etc are not visible. Is there a way of fixing that too? 

Before setting up using this method I had already tried one of the supplied links to manually install and configure hotway but that didn't work as hotway was not found. 
I cannot find Xinetd installed but maybe I am not looking at the right spot?

---

