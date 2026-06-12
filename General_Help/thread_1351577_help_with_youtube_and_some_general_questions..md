---
title: "help with youtube and some general questions."
date: 2009-12-10
forum: General Help
---

### Post by black28 on 2009-12-10
hey guys, I have the adobe plugin but when I play videos on youtube the sound is perfect but the video is laggy, is there a way to fix this? or is my pc just slow? 

HP Vectra VL400 256MB+128MB ram, 60GB HDD, XUBUNTU 9.1 INSTALLED ON HDD,
PENTIUM 3.

also, is xubuntu safe to use for personal info? like online payments/banking and saving personal files like passwords and bank info on HDD? how can I make my pc more secure? all help is greatly appreciated. thank you.

---

### Post by black28 on 2009-12-10
does anyone have any input for me?

---

### Post by solidjoe on 2009-12-11
Flash video has no GPU acceleration - it's all on the processor. The latest version of flash is terrible on resources. I'd say its just a bottleneck of your processor. Until Adobe adds hardware/gpu acceleration, even the newer Atom processors are unable to keep up with a lot of flash sites. Sorry!

---

### Post by black28 on 2009-12-11
thanks, any word on personal file security?

---

### Post by akakingess on 2009-12-11
> **black28 said:**
> 
also, is xubuntu safe to use for personal info? like online payments/banking and saving personal files like passwords and bank info on HDD? how can I make my pc more secure? all help is greatly appreciated. thank you.
In regards to online safety, it really doesn't have as much to do with your operating system as it does with the browser and the site involved. In other words, you should be just as secure using Firefox with your bank online within Xubuntu as you would with Firefox and your bank within Windows. Keep in mind this is not necessarily a professional opinion, but rather a personal one although I do know a little about online security.

Follow up: Sorry, but I completely overlooked your question about overall computer security, which in my opinion Xubuntu would be more secure than your same system (provided it's all connected the same) running Windows. Viruses, adware, spyware, all of that you don't have to worry about nearly as much as with Windows (if at all), so you should feel just as safe with Xubuntu as you would with Windows if not more so.

---

### Post by black28 on 2009-12-11
oh, alright thanks. i was just curious like if linux programmers and other users could access my files and stuff that i save on my hard drive. yah i know sounds crazy but being knew to linux just want to know what is capable and stuff. that's not possible then?

---

### Post by akakingess on 2009-12-11
Not unless they know your username and password, just like on any other computer. They couldn't even install an application without your password. One of the beauties of Linux is it's security.

---

### Post by black28 on 2009-12-13
so even from their personal PCs or whatever they can't get into my PC and hack me?

---

### Post by black28 on 2009-12-13
anyone?

---

### Post by scouser73 on 2009-12-13
I see that you have the Firefox flash plug in but you could try installing flash from the Adobe website.

[COLOR="Red"]**Installing Flash Player via the Adobe website**[/COLOR]

**1** - Go to [[COLOR="Red"]**Adobe Flash**[/COLOR]]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

**2** - Select **.deb for Ubuntu 8.04+** from the drop down menu

**3** - Click **Agree & Install Now**

**4** - Select **Open With** **GDebi Package Installer** in firefox or save the file and install the **.deb** file that way

---

### Post by black28 on 2009-12-13
any on the PC Security Usage?

---

### Post by scouser73 on 2009-12-13
Well I use Ubuntu for online banking as opposed to Xubuntu, but it's basically the same any way.  The personal information you have is only safe if you trust the sites that you visit, if you visit a bankng site check that the website address has **https** - *Information from Wikipedia* > The main idea of HTTPS is to create a secure channel over an insecure network. This ensures reasonable protection from eavesdroppers and man-in-the-middle attacks, provided that adequate cipher suites are used and that the server certificate is verified and trusted.

The trust inherent in HTTPS is based on major certificate authorities which come pre-installed in browser software (this is equivalent to saying "I trust certificate authority (e.g. VeriSign/Microsoft/etc.) to tell me who I should trust"). Therefore an HTTPS connection to a website can be trusted if and only if all of the following are true:

   1. The user trusts the certificate authority to vouch only for legitimate websites without misleading names.
   2. The website provides a valid certificate (an invalid certificate shows a warning in most browsers), which means it was signed by a trusted authority.
   3. The certificate correctly identifies the website (e.g. visiting [https://somesite](https://somesite) and receiving a certificate for "Somesite Inc." and not "Shomesite Inc." [see #2]).
   4. Either the intervening hops on the internet are trustworthy, or the user trusts the protocol's encryption layer (TLS or SSL) is unbreakable by an eavesdropper.


I assume that you are using Firefox, which has a password manager, this is excellent for storing your passwords.

I have my passwords and other banking information stored on my hard drives and I have no problems whatsoever. 

Your personal information is only as secure as you allow.

---

### Post by black28 on 2009-12-13
just did the Adobe Update. still the same, any other suggestions? or is it just my hardware? anything on the Security?

---

### Post by black28 on 2009-12-13
exactly why im asking. i created a Document that i keep all my user names and passwords saved down too. i am a little hesitant to make it on Xubuntu until i find out if its safe or not. i do use Firefox, and also Alot of Opera. Opera seems Faster. so my personal HDD Files are only accessible if hacked through a website? i do online banking and stuff over Paypal and ebay as well.

---

### Post by scouser73 on 2009-12-13
> so my personal HDD Files are only accessible if hacked through a website?

The chances of that ever happening are extremely slim I would say, it pays to be cautious with your information.

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
Anything can be cracked it doesn't matter what you do security wise. Just depends on what the person trying to crack your system knows. Though the chances of someone being able to do it are slim the more you do to make your system secure. Default install of Ubuntu is pretty rock solid (more so than a Windows system that you spend hundreds on security software for IMO) and you can make it more so by employing encryption and a few other techniques. Look in the Security Discussions thread for more information.

---

### Post by black28 on 2009-12-13
would you ugys not recommend saving such file then?

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
I have one...

---

### Post by black28 on 2009-12-13
okay, thanks guys. nothing on the youtube vids?

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
When you play a youtube video open system monitor and see if it's using a lot of resources. If it is then your hardware isn't cut out. If that's the case you could switch over to LXDE and it might improve. If not then I would say do like scouser73 said in post 10.

---

### Post by black28 on 2009-12-13
in system monitor everything is sleeping using 0% CPU, Opera is 30 and Firefox is like 40%. i did the Adobe Install in post 10. no flash for Opera only Firefox. what is LXDE?

---

### Post by Leppie on 2009-12-13
In opera's address bar type about:config, then in the search bar type flash. Either check the "Ask flash download" option under "Extensions" or make sure the installed flash plugin's path is present in the "Plugin Path" under "User Prefs".

LXDE is another desktop environment, slightly lighter in use than xfce (I believe it uses about 30mb less ram than xfce). Try installing it in synaptic, you can always switch the environment when logging in using the session menu.

---

### Post by black28 on 2009-12-14
did that, it's already checked.

---

