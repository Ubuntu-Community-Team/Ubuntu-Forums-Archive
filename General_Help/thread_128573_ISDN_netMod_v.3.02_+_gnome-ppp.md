---
title: "ISDN netMod v.3.02 + gnome-ppp"
date: 2006-02-11
forum: General Help
---

### Post by snis on 2006-02-11
I am total begginer in Ubuntu. I managed to install linux etc. Now i had installed gnome ppp but i can't see my modem (*ISDN netMod USB v 3.02 "Intracom"*). Please help me with some instructions or links, or something, because I don't know how to install that ISDN.:confused: 
Thank You.

---

### Post by Claus7 on 2006-11-04
Indeed it is a real problem if a computer these days doesn't have an internet connection. Of cource you might have solved your problem, yet I would like to anwser anyway cause 1) if you find a solution why not post it? and 2) I have never found a complete solution to this problem. I must also say that this was one of the main reasons avoiding linux in general.

I must admit that now with the adsl connections this might be a little bit oldfashioned, yet a solution is always a solution.

I have made an isdn connection using [COLOR="Red"]netmod[/COLOR] (manufacturer Intracom) via the *[COLOR="DarkRed"]usb[/COLOR]* port. The distribution I 'm using is [COLOR="Red"]Ubuntu 6.06 LTS Dapper Drake[/COLOR]. 

In order to make an isdn connection from the beginning someone must take into account 2 things :
[LIST=1][*]The first is that the modem should be recognised by the computer. For the version I 'm using this in not a problem. The issue has to do with the version of the kernel. If the version is old, then someone must follow the instructions from the site of intracom, otherwise this instructions shouldn't be taken into account (usb_linux_22x_en.pdf).

[*]Second, one must be able to configure one's connection.

[/LIST]

There are three different ways of someone who wants to configure one's connection (if from my research I 'm correct). 
[LIST]
[*]The one is via [COLOR="#8b0000"]pppconfig[/COLOR], 
[*]the other via System -> System Management -> Internet 
[*]and the last via wvdial.[/LIST] 

The one that I will explain is the first one :

As the documentation of ubuntu says, [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto),

1. Open a terminal (Applications > System Tools > Terminal) and type :
  $ sudo pppconfig 
You must be a rooter in order to do this, as it will affect the whole system. After that
it will ask for your password.

2. You will be on the main menu. Choose 'Create Create a connection'. 

3. Leave the name as 'provider', hit 'Ok'. 

After step3, instead as these instructions, [COLOR="#8b0000"]I was asked to give the first and second adress of my IP provider[/COLOR]. Speaking of Tellas (this was my provider), I was able to learn these numbers by giving them a call. For this provider the numbers are as follows :

1st IP address 62.169.194.17
2nd IP address 62.169.194.18
(I have to say that leaving these blank I could see the red light of my modem flashing, yet I couldn't browse the internet.)

4. Select 'Dynamic Use dynamic DNS', hit 'Ok'. (I didn 't have that option)

5. Select 'PAP Peer Authentication Protocol', hit 'Ok'. 

6. Enter your user name for the ISP, hit 'Ok'. ("tellas", without the "")  

7. Enter your password for the ISP, hit 'Ok'.  ("free", without the "")

8. Leave the speed at 115200 as recommended, hit 'Ok'. 

9. Choose Tone or Pulse dialing, hit 'Ok'. (I chose Tone)

10. Enter the phone number to your ISP (do not use any dashes), hit 'Ok'. (8015005000)

11. You can try to have your modem detected automatically, but it did not work for me, even on my easily detectable external modem. 
This step is very tricky. Choose here whatever you like, (I chose to detect it myself), and a new panel 
will appear asking you to type the port of the modem. [I][COLOR="DarkRed"]The default is ttyS1, which means that this is 
a serial port and NOT a usb port[/COLOR][/I]. So don't use this option. Instead wright [COLOR="Red"]ttyACM0[/COLOR] for the first usb port,
ttyACM1 for the second and so on (watch out that 0 is the first port), depending on which usb port you have
connected your modem.

12. If the modem wasn't detected, it will ask you for the port your modem is on. Enter the device name for your modem, hit 'Ok'. 

13. A summary screen will appear and give you the opportunity to make changes if needed. 

14. Choose 'Finished Write files and return to main menu.'. 

15. Choose 'Quit Exit this utility'. 

16. Exit the terminal window, type: 
  $ exit
  
A general remark here is that I didn't have any other connection configured. If you make a mistake
I think that it is better to erase the configuration you have made and SAVE the erasure you have made. 
For example, when I wanted to make a change in my configuration I was discovering also a 'provider.bak'
configuration. Maybe  because I 'm not so accustomed to linux yet, but for new users I think that way
someone can avoid problems.

Having done all that [COLOR="Red"]I must say that I was able to connect[/COLOR]. In order to do so I opened a terminal and typed:
$ pon 
In order to end the connection I typed :
$ poff

Here I have to add that sometimes I cannot connect with the first time, something that was depending on the provider and not on faulty configurations (for example busy lines). Most of the time I connect with the second try.

Yet, after exactly 2 minutes (120 seconds, I 'm writting also the seconds because I found it both while searching) the connection was terminated (or crushed if you prefer). In order to change that I had to do the following.
  
 [COLOR="Red"]If you lose the connection[/COLOR] a short time after connecting (30 sec - 3 min), you might need to edit options for pppd: 
gksudo gedit /etc/ppp/options

Find lcp-echo-interval30 and lcp-echo-failure4. Comment out these options by adding a [COLOR="DarkRed"]'#'[/COLOR] at the start of these lines, eg. # lcp-echo-interval30 and # lcp-echo-failure4. 

In other words with the above command you will open a new window where most of the lines will start with
this symbol : #. Yet, in front of lcp-echo-interval30 and lcp-echo-failure4 this symbol doesn't exist. Just add it.
As you can see you must be root to do that. 

I hope that this will help.
If someone has a better way let me know.
In the end I give some links which helped me to solve the problem. Some are in the hellenic language.

[http://www.ubuntuforums.org/showthread.php?t=130003&highlight=How+to+configure+ISDN](http://www.ubuntuforums.org/showthread.php?t=130003&highlight=How+to+configure+ISDN)
[http://www.debian.gr/?q=node/258#comment-592](http://www.debian.gr/?q=node/258#comment-592)
[http://www.ubuntuforums.org/showthread.php?t=127810&highlight=exactly+120+seconds](http://www.ubuntuforums.org/showthread.php?t=127810&highlight=exactly+120+seconds)
[http://www.ubuntuforums.org/showthread.php?t=129156&highlight=Modem+hangs+within+2+minutes](http://www.ubuntuforums.org/showthread.php?t=129156&highlight=Modem+hangs+within+2+minutes)
[http://www.techteam.gr/index.php?showtopic=22020](http://www.techteam.gr/index.php?showtopic=22020)

---

### Post by profediego on 2007-05-28
Hi, i am having problems configuring a isdn connection, i have an intracom netmod-usb modem,my gppp deteted it fine but when trying to conect i get this error:  

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR
--> Bad init string.

Does anybody here know how to solve this problem.  Thanks in advance

---

### Post by Claus7 on 2007-05-31
Hello,

long time no see to this subject. I haven't faced the problem you are facing. And as far as I have searched the forums :
[http://ubuntuforums.org/showthread.php?t=279058&highlight=gppp](http://ubuntuforums.org/showthread.php?t=279058&highlight=gppp)
you are using different type of configuration than mine. 
My suggestion is go for pppconfig. As far as your problem is concerned, reading the error messages, I suppose that in your configuration of gppp you might have chosen a serial port instead of usb port. I can't tell you more because I haven't used gppp.

Regards!

---

