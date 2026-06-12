---
title: "removing username/pw from new notebook mini with ubunto"
date: 2009-08-22
forum: General Help
---

### Post by teeksk8 on 2009-08-22
I'm trying to help out a young girl I know who's mother got her an Ubunto notebook mini from ebay. It was supposed to be brand new but there is a user name and pw on the system that does not allow her to do anything without it. 
I've never even heard of this system before and naturally not an expert, so we are at loose ends.. Ebay have advised it is a 'new' product and cannot assist. She is leaving for the US today and was hoping to take it with her. 
Any assistance would be great.. 
 
I've tried using many of the posts on here to reset the password but the user name is 'hj' and the H key on the keypad is NOT WORKING either.. (we've been had obviously)
 
So that in itself presents an issue, b/c I'm unaware of course how to 'paste' the letter h into the terminal window or at any other level.. 
 
Thanks

---

### Post by dcstar on 2009-08-22
> **teeksk8 said:**
> I'm trying to help out a young girl I know who's mother got her an Ubunto notebook mini from ebay. It was supposed to be brand new but there is a user name and pw on the system that does not allow her to do anything without it. 
I've never even heard of this system before and naturally not an expert, so we are at loose ends.. Ebay have advised it is a 'new' product and cannot assist. She is leaving for the US today and was hoping to take it with her. 
Any assistance would be great.. 
 
I've tried using many of the posts on here to reset the password but the user name is 'hj' and the H key on the keypad is NOT WORKING either.. (we've been had obviously)
 
So that in itself presents an issue, b/c I'm unaware of course how to 'paste' the letter h into the terminal window or at any other level.. 
 
Thanks

System-Administration-User & Groups.

Unlock and then create a new user with "Administer the System" privileges.

Log out of the bad user, log into the system using the new user you just created and then use the same tool to delete the bad user account.

Otherwise just install a fresh copy of the Ubuntu Netbook Remix on the system.

---

### Post by teeksk8 on 2009-08-22
I've kind of tried to remove that user, but it keeps asking for the user password to do so saying it has amin .. and the mini doesnt appear to have a cdrom, so installing the software isnt an option unless it can be done online.. ?? sorry.. I'm really not a tech guy but thanks for the help, I'll see what I can do..
 
when i logout, it then asks for a user name (which i cannot create at this point without the other password it appears) and then it auto logs in as the other user.. ???

---

### Post by wojox on 2009-08-22
Here you go:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by akakingess on 2009-08-22
You could install it via a USB stick if you have one large enough and available. Just download the Ubuntu installer and put it on the USB stick and choose to boot off of the USB if that is an option within the bios. Try this and let us know if you get stuck or hit a hurdle.

---

### Post by michy99 on 2009-08-22
Not sure how much help this will be, but I can tell you how to get an 'h'. Hold down the Shift and Control keys at the same time. Type in u0068 and then release the Shift and Control keys. You will get a 'h' For a Big 'H' use u0048.

EDIT: Those are Zero's, not the letter O.

---

### Post by teeksk8 on 2009-08-22
> **wojox said:**
> Here you go:
 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
 
 
everytime I try this, once I get to the root shell prompt, rather than letting me type in 1s /home it asks for 'root password for maintenance'
 
so I guess I'm stuck there too.. 
 
sorry for all this

---

### Post by michy99 on 2009-08-22
> **teeksk8 said:**
> everytime I try this, once I get to the root shell prompt, rather than letting me type in 1s /home it asks for 'root password for maintenance'
 
so I guess I'm stuck there too.. 
 
sorry for all this

One tip: it is ```
ls /home
```The first letter is an l as in lion, not the number one.

---

### Post by teeksk8 on 2009-08-22
> **michy99 said:**
> One tip: it is ```
ls /home
```The first letter is an l as in lion, not the number one.
 
thanks for that, but it doesnt give me an option to enter anything at that level other than a password

---

### Post by michy99 on 2009-08-22
I really think she should return it to the seller and demand her money back. If she payed through PayPal, she can file a complaint and they will almost certainly give her the money back, but it may take a few weeks to go through the process.

---

