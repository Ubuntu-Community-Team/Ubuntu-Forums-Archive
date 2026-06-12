---
title: "gmail settings in evolution"
date: 2006-04-14
forum: General Help
---

### Post by PriceChild on 2006-04-14
Well it's past midnight and i'm allowed to be silly...

> [SIZE=-1]**Incoming Mail (POP3) Server - requires SSL:**[/SIZE]   [SIZE=-1]pop.gmail.com
  Use SSL: Yes
  Port: 995[/SIZE]
[SIZE=-1]**Outgoing Mail (SMTP) Server - requires TLS:**[/SIZE]   [SIZE=-1]smtp.gmail.com (use authentication)
        Use Authentication: Yes
        Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587[/SIZE]
[SIZE=-1]**Account Name: **[/SIZE]   [SIZE=-1]your Gmail username (including '@gmail.com')
[/SIZE][SIZE=-1]**Email Address: **[/SIZE]   [SIZE=-1]your full Gmail email address (username@gmail.com)
[/SIZE][SIZE=-1]**Password: **[/SIZE]   [SIZE=-1]your Gmail password[/SIZE] 
But i see nowhere in evolution to enter the ports.

I'm sure i had it set up before i reinstalled ubuntu too...

Please help, Pricey

---

### Post by gazj on 2006-04-14
I know this probably isn't the answer you want, but i have successfully set up gmail under thunderbird if thats any good to you :)

---

### Post by cstudent on 2006-04-14
[http://www.ubuntuforums.org/showpost.php?p=726120&postcount=5](http://www.ubuntuforums.org/showpost.php?p=726120&postcount=5)

---

### Post by Alexander Kirillov on 2006-04-15
[QUOTE=PriceChild]Well it's past midnight and i'm allowed to be silly...

 
But i see nowhere in evolution to enter the ports.

I'm sure i had it set up before i reinstalled ubuntu too...

Please help, Pricey[/QUOTE]
You can enter ports by entering in "server" box 
pop.gmail.com:995

(Disclaimer: I never used Evolution with gmail - but I used this method  to connect to an IMAP server which used non-standard ports

---

### Post by anselm on 2006-04-15
I didn't have to set up any ports when I did gmail in evolution, worked fine for e without doing this.

---

### Post by PriceChild on 2006-04-15
i tried the ":995" but it didn't seem to change anything.

Changed the authentication to "Always" as Alex suggested.

Doesn't seem to be doing anything, just stays on "Waiting" as before.

I also had it set up in thunderbird as well earlier, but i'd prefer to use evolution seen as its integrated into gnome.

---

### Post by cstudent on 2006-04-15
[QUOTE=PriceChild]i tried the ":995" but it didn't seem to change anything.

Changed the authentication to "Always" as Alex suggested.

Doesn't seem to be doing anything, just stays on "Waiting" as before.

I also had it set up in thunderbird as well earlier, but i'd prefer to use evolution seen as its integrated into gnome.[/QUOTE]

I think you must be overlooking something. If you have all these options set to these values it should work for you. Make sure you are using your full gmail email address as the user name.

> 

In the Evolution settings tab for Receiving Email:

Server type: POP
Server: pop.gmail.com
Username: [email]yourname@gmail.com[/email]
Use secure connection: ALWAYS
Authentication type: Password


Under Sending Mail tab:

Server type: SMTP
Server: smtp.gmail.com
Server requires authentication: checked
Use secure connection: ALWAYS
Authentication type: Plain
Username: [email]yourname@gmail.com[/email]



---

### Post by PriceChild on 2006-04-15
Hmm... it's suddenly just worked :S

Didn't change anything - i'm not complaining :D

---

