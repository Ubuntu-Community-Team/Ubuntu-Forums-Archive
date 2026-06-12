---
title: "How can i set up Thunderbird??(for hotmail)"
date: 2009-07-22
forum: General Help
---

### Post by bnvdarklord on 2009-07-22
I have Mozilla Thunderbird, and i cannot make it to receive my emails at all with my hotmail account.
I have installed WebMail and Hotmail extentions, I have used ports higher than 1200 so they run correctly, i use pop3.live.com and smtp.live.com as incoming and outgoing servers, but i cannot get it to work correctly.

---

### Post by mike555 on 2009-07-22
pop=  pop3.live.com  port995
  smtp=  smtp.live.com  port 25 or 995
 uncheck "secure password auth. (spa)"
  requires  "secure connection (ssl)"


  if that doesn't work use ; smtp.live.com port 587    tls

---

### Post by bnvdarklord on 2009-07-22
these ports, and all ports under 1200 i think don't work, i used 9950 and 2500 respectively.

edit : with the setting i have made, thunderbird is loading pop3.live.com, for a minute, and then i get a timeout error.

---

### Post by Benzaa on 2009-07-22
What is your status on the preferences for webmail??
Are they all green??

In case they are and you are still having timed out problems, try to increase your connection timed to 120 secs. Search for the option in preferences.

This helped me when I was having the same problem

---

### Post by bnvdarklord on 2009-07-22
Both POP and SMTP are green.

---

### Post by Benzaa on 2009-07-23
> **bnvdarklord said:**
> Both POP and SMTP are green.


Did you change the connection time???

---

### Post by bnvdarklord on 2009-07-23
Just did, and i got the same time out error.

---

### Post by wojox on 2009-07-23
This is what mine are set to:

Incoming server: pop3.live.com:995
Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password


Outgoing server: smtp.live.com:587
Server requires authentication: yes
Security: TLS
Authentication type: plain

Works fine.

---

### Post by bnvdarklord on 2009-07-23
> **wojox said:**
> This is what mine are set to:

Incoming server: pop3.live.com:995
Username: your_username @hotmail.com
Use secure connection: SSL
**[COLOR="Red"]Authentication type: password[/COLOR]**


Outgoing server: smtp.live.com:587
**[COLOR="#ff0000"]Server requires authentication: yes[/COLOR]**
Security: TLS
**[COLOR="#ff0000"]Authentication type: plain[/COLOR]**

Works fine.

Where are the settings i highlighted?

---

### Post by Benzaa on 2009-07-23
Here are my settings, check the image.

Remember that is important that the port number is the same that you are using for POP in webmail

---

### Post by wojox on 2009-07-23
Sorry I forgot I switched back to evolution??  :o

---

### Post by bnvdarklord on 2009-07-23
YAY i fixed it!! I used ports 2000 and 2001 like Benzaa in Webmail, but left 995 and 587 in settings... Thank you all for your help!

I got one Question though : I have 3 folders : Inbox, Unsent and Trash. Where are the Sent and Junk folders?

---

### Post by Benzaa on 2009-07-23
I think you can create the folder. 

Im not sure how does the junk separator works but if you find out, post it.

---

### Post by bnvdarklord on 2009-07-23
> **Benzaa said:**
> I think you can create the folder. 

Im not sure how does the junk separator works but if you find out, post it.

I found it with a little google search. You need the folderFlag add-on
```
https://addons.mozilla.org/en-US/thunderbird/addon/1898
```
and then create a folder, right click on it, click flags, and select Junk.:KS

---

