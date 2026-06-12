---
title: "wanna make a start with wammu"
date: 2011-08-27
forum: General Help
---

### Post by raja.genupula on 2011-08-27
i have a nokia mobile . model 2690, i just wanna set this for wammu through a usb cable. i had googled it and got nothing . tried   links from gammu site but didnt work . ]

could any one help me to figure it out

---

### Post by raja.genupula on 2011-08-30
c'mon , some one could have to look at this . its been two days . please guys .

---

### Post by coldraven on 2011-08-30
I have never had any luck with Wammu, try using gammu instead.
Gammu is a command line utility only.
I needed to get my contacts from my old Nokia 5140 using a CA-42 (USB to serial) cable.
Run ```
gammu-config
```It should produce a file called .gammurc in your home folder
Mine looks like this, you can edit the file if you did not know the correct settings when you ran the above command.

#######################
 [gammu]
 
 port = /dev/ttyUSB0
 model = 5140
 connection = fbusdlr3
 synchronizetime = yes
 logfile = 
 logformat = nothing
 use_locking = 
 gammuloc = 


Then I created a backup file (.lmb) using 
     ```
gammu --backup my_contacts.lmb 
```Then restore your contacts   
     ```
gammu --restore my_contacts.lmb 
```This will erase any existing contacts so if you have already made some use --addnew instead.    
     ```
gammu --addnew my_contacts.lmb
```

---

### Post by raja.genupula on 2011-08-30
i wanna use it for sending sms and receiving too. 

thanks for pick up my thread , after a long time i got reply . please help me with this .

---

### Post by coldraven on 2011-08-31
Hi again, sorry that I made a mistake in my first post. I have corrected it.
So fist create a config file with ```
gammu-config
```then check that you can communicate with your phone with ```
gammu --identify
```then send an SMS like this
```
echo "Hello John" | gammu --sendsms TEXT +44xxxxxxxx
```Where +44xxxxxxx is John's phone number

For some reason I have never been able to make Wammu work so I just use Gammu.
Maybe if you get your phone to work with gammu first then wammu might work for you.
Good Luck :p

---

### Post by raja.genupula on 2011-09-02
thank you very much . 
i am gonna check it when i get back to room . 
thank you .

---

### Post by raja.genupula on 2011-09-02
Sorry i didnt it . it saying failed . gammu --identity saying " bad option"

---

