---
title: "Help with Lexmark X1185 Printer Setup/Driver ,  Google isnt helping..."
date: 2010-03-05
forum: General Help
---

### Post by Rasa1111 on 2010-03-05
Hey all, 

 Im at a friends house and he really needs to get his printer going before 4pm today. 

We have installed updates it said were required to get it working, yet it still wont print.. 

 Is there something simple Im missing? 

The driver/ whatever else needed, is eluding me, and the printer is really needed. 

anyone want to bite? lol  

 Thanks in advance, rasa

---

### Post by patchwork on 2010-03-05
Take a peek at this tutorial:
[URL="http://ubuntuforums.org/showthread.php?t=49714"]
http://ubuntuforums.org/showthread.php?t=49714[/URL]

---

### Post by Rasa1111 on 2010-03-05
hey patch, thanks..  

 I was just looking at that page to. 
 My only problem there, is.... 

 when given this link.. [http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151)

 I see at the bottom, the box for Linux/ and Ubuntu..
 but I dont see any drivers for them on the page..
 they all say they are for some kind of windows OS. 

I dont know where to find the download i need onn that page?

 thank you man,.

---

### Post by Rasa1111 on 2010-03-05
at the very botom of that link.. where it says:
[B] Select your operating system to view files for the Lexmark Z605
 
[/B]I see where "Linux/Unix" is, but where does one go from there?all the downloads above that box, in red, all say for MS systems. ? hmm... if I could find the actual download, I could manage the rest of the intruction in that post you linked me to. lol Thanks

edit: Is this what I need? 
it says for redhat linux...  ??
[Link]("http://support.lexmark.com/index?page=content&id=DR15809&actp=search&viewlocale=en_US&userlocale=EN_US&segment=DOWNLOAD&productCode=LEXMARK_Z604&searchid=1267818797957")

---

### Post by patchwork on 2010-03-05
I'd be really surprised if the red hat driver would not work for you here.  It is archived with tar.gz, so after you download it you will need to extract the file.   You can either use file roller (by clicking on it, or use the command line...

note: you may want to copy the file to a separate folder before extracting

```
cd <location of archive>
tar -xzvf <filename>
```EDIT:  yeah, just checked the tutorial again, that is the driver you need.  You will need to install alien, though.  Alien is a converter to/from red hat .rpm packages

---

### Post by Rasa1111 on 2010-03-05
awesome bro, thank you.  

Im heading back up there a little later to work on it some more, 
 I was a little confused as to the "alien" thing needed,  
but now i know its just something i need install. :lol:

 I think I could figure it out once converted.  lol
(if not, I hope you stick around, friend.. I will need someone to show my *possible* error messages to. ) :lol:

 Thanks allot for your time, Patch.  *deep bows*
Rasa <3

---

### Post by patchwork on 2010-03-05
No problem, alien is in the repos

```
 sudo apt-get install alien 
```

---

### Post by Rasa1111 on 2010-03-26
thanks Patch, 
 Im back at the home of said printer,
 and ive got alien installed now...

 now can someone tell me how to use 'alein' once I have it?

 ive been searcghing through [http://ubuntuforums.org/showthread.php?t=49714&page=1](http://ubuntuforums.org/showthread.php?t=49714&page=1)

for how to use / install this driver now that i have it,  but im having no luck.... yet. lol

 So, I have the driver~ from [here]("http://support.lexmark.com/index?page=answerlink&userlocale=EN_US&segment=SUPPORT&locale=en&url=http%3A%2F%2Fsupport.lexmark.com%2Findex%3Fpage%3Dcontent%26id%3DDR4360%26actp%3Dsearch%26viewlocale%3Den_US&productCode=&answerid=16777224&searchid=1269650150684")

and alien installed...
 what is my next step?

my printer at home is just recognized by ubuntu.. and it 'just works'..

 but this lexmark is a pita. :(

 many thanks, anyone who can help. <3

---

### Post by Rasa1111 on 2010-03-27
ahh nevermind. got it, .........................i think....... for now... lol

thanks.

---

### Post by colin.p on 2012-07-21
> **ebuh said:**
> The model number **Lexmark X1185**.

**Method 1:**
You may refer to the below links and use the troubleshooters. Check if it lists and helps resolve any issues: Open the Printer troubleshooter:
[http://support.lexmark.com](http://support.lexmark.com)

**Method 2:**
You may check if you have the latest drivers installed for the device. You may refer to the below link for getting the latest drivers and check 
[Lexmark X1185 Driver]("http://www.lexmarkdrivers.net/all-in-one-printers/lexmark-x1185-driver.html")

Hope this help.

It very well may help, but this thread is over 2 years old. I bet the fellow has long junked that printer and bought a new one. I know I did.:)

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

