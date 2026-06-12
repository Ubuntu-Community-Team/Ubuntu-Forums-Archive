---
title: "John the Ripper"
date: 2010-04-03
forum: General Help
---

### Post by savyboy24 on 2010-04-03
Anyone know how to install and use this program?

---

### Post by Johnny B on 2010-04-03
$ sudo apt-get install john

---

### Post by dacoolio on 2010-04-03
To use it to crack passwords, you need the hash and usually a password list. I find the Argon dictionaries to be great for password cracking, but unfortunatly their website disapeared :cry: anyways I found their list on [ thepiratebay]("http://thepiratebay.org/torrent/3833663/The_Argon_list_ver.2_Password_dictionary_2.3gig_Jo-Psyko_")

---

### Post by savyboy24 on 2010-04-03
Did that now how do I find it to run the program?

---

### Post by savyboy24 on 2010-04-03
the john program

---

### Post by dacoolio on 2010-04-03
Well it really depends on what you are using it for. Heres the basic syntax:

$ john [OPTIONS]  [PASSWORD-FILES]

Look at the man page for specifics:

$man john

---

### Post by savyboy24 on 2010-04-03
This is my class assignment. So  this is what I have to do. Still new so I actually am not sure how I would use this in real life situations. 


	 	 	 	 	  [SIZE=2]In this hands-on we crack some encrypted passwords with [/SIZE][COLOR=#0000ff]_[John The Ripper]("http://www.openwall.com/john/")_[/COLOR][SIZE=2] (JTR) to display their clear text versions.  (If you prefer, you can use [/SIZE][COLOR=#0000ff]_[Cain and Abel]("http://sectools.org/index.html#cain")_[/COLOR][SIZE=2] instead of JTR. The steps are similar.)[/SIZE][COLOR=#0000ff]_[[SIZE=2]Hands-On Mini-Project 14 - Crack Of Encrypted Passwords[/SIZE]]("http://ubuntuforums.org/#TOC")_[/COLOR]
 

 [SIZE=2]JTR should prove helpful to you when, for example, testing that the passwords used by your network users comply with company's password length, format, and change frequency policies, or checking how well your server is resistant to penetration testing by password cracking.[/SIZE]
 

 
[LIST=1]
[*][SIZE=2]Download 	the latest free "stable" release of John The Ripper[/SIZE]
[*][SIZE=2]Delete 	the file john.pot if there is one.  [/SIZE][SIZE=2]_Note: 	If you have trouble getting results from what follows, delete 	john.pot again_[/SIZE][SIZE=2]![/SIZE]
[*][SIZE=2]Create 	a text file and put it in a new folder ./secrets/[/SIZE]
[/LIST]
 

  	 	 	 		 			[SIZE=2]FileName[/SIZE]
 		 		 			[SIZE=2]desPasswords.txt[/SIZE]
 		 	 	 		 			[SIZE=2]Contents[/SIZE]
 		 		 			[FONT=Courier, Courier New, monospace][SIZE=2]LoginName1:CRyVSSACmdRhU[/SIZE][/FONT]
 			[FONT=Courier, Courier New, monospace][SIZE=2]LoginName2:CReMdMyLGCltw[/SIZE][/FONT]
 			[FONT=Courier, Courier New, monospace][SIZE=2]LoginName3:CR0sdhwzzoaNY[/SIZE][/FONT]
 		 	  

 
[LIST=1]
[*][SIZE=2]Open 	a command prompt window, cd to your install folder, and run 	[/SIZE][SIZE=2]**john-386.exe **[/SIZE][SIZE=2]with 	the file you just created.  For example, type[/SIZE][SIZE=2]**:**[/SIZE]
[/LIST]
 [SIZE=2]**	C:\Program Files\jtr\run>john-386 --format:DES ./secrets/desPasswords.txt**[/SIZE]
 
[LIST=1]
[*][SIZE=2]Run 	[/SIZE][SIZE=2]**C:\Program 	Files\jtr\run>john-386 --show ./secrets/desPasswords.txt  **[/SIZE][SIZE=2]What 	do you see?[/SIZE]
[/LIST]

---

### Post by dacoolio on 2010-04-03
Ok so first place you hashes in a text file. I used "password.txt". Then you need to run john on them, specifying that DES is used. 

```

$john --format:DES password.txt

```

John decrypts them, revealing the passwords in plaintext

```

hello            (LoginName1)
c00per           (LoginName2)
heikki           (LoginName3)


```

---

### Post by savyboy24 on 2010-04-03
a text file can I use open office odt

---

### Post by dacoolio on 2010-04-03
No I would use GEdit. It comes standard and is made for these kinds of things.

Applications >> Accessories >> gedit Text Editor

---

### Post by savyboy24 on 2010-04-03
after I make this file in the editor then I will make a folder in my Home folder call secrets. What does the path look like? john --format:DES home/secrets/passwords.txt  ??? The pathsways sometimes messs me up.

---

### Post by dacoolio on 2010-04-03
If you put the password.txt file in the Home directory, the path will look like such: /home/<user>/secrets/password.txt Replace <user> with your username.

The resulting JTR command will look like such:

```

$ john --format:DES /home/<user>/secrets/password.txt

```

---

### Post by savyboy24 on 2010-04-03
Thanks a bunch...

this should help me answer these questions yes?

  	 	 	 	 	 	  
[LIST=1]
[*][SIZE=2]Run 	[/SIZE][SIZE=2]**C:\Program 	Files\jtr\run>john-386 --show ./secrets/desPasswords.txt  **[/SIZE][SIZE=2]What 	do you see?[/SIZE]
[*][SIZE=2]Report 	the cleartext (decrypted) version of the user login passwords in 	desPassword.txt[/SIZE]
[*][SIZE=2]Briefly 	answer the following questions: (a) What does DES stand for? (b) 	What does 3DES stand for? (c) What is 3DES good for? (d)What are 	alternatives to 3DES? [/SIZE] 	
[*][SIZE=2]Briefly 	answer the following questions: (a) What does MD5 stand for? (b) 	What is a hash? (c) What is the format of the MD5 hash? (d) What is 	MD5 good for? (e) What are alternatives to MD5? (f) What are rainbow 	files?[/SIZE]
[/LIST]

---

### Post by dacoolio on 2010-04-03
Yes this should answer the first two questions. As for the the others, I will steer you towards my favorite [homework site.]("http://en.wikipedia.org/wiki/Data_Encryption_Standard")

---

### Post by savyboy24 on 2010-04-03
lol...thanks again. SOmetimes I get so wrapped up in all this I forget the obvious!!!

---

### Post by cariboo on 2010-04-03
From the code of conduct:

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

This thread is closed.

---

