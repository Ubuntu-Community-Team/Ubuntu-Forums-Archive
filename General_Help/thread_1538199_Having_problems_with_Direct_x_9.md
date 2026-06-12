---
title: "Having problems with Direct x 9"
date: 2010-07-24
forum: General Help
---

### Post by serdar132 on 2010-07-24
Hello,

I have recently switched to Ubuntu. I have Ubuntu 10.04

I have tried to install directx 9  with several ways.  At last i have tried this tutorials which explains step by step with clear explanations :
[http://www.wine-reviews.net/wine-reviews/games/how-to-install-directx-in-linux-using-wine.html](http://www.wine-reviews.net/wine-reviews/games/how-to-install-directx-in-linux-using-wine.html)

I have done everything very well until I extract the files od Directx to go on with the setup and install directx.  But it wont install and says check the error log sth like that.

Then I finally managed to figure out ( i guess ) to use wine tricks i wrote the commands it downloaded the file (104 mb)  Then it started to setup, it completed the setup to, but in terminal it was saying like erroe x104 as I remember and i couldny press sinish button to fully completed the direct x.

I font know what happened it seems now there is no way i can have decent direct x 9 on my ubuntu.

Pleae help me!

Thanks
Serdar

---

### Post by homerhomer on 2010-07-24
Yeah, that's a tough one, WINE already supports a lot of directx 9 natively. I would just install the latest version of wine and see if you program will run. 

this will help you get the latest version of wine
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

also look in the wind app data base to see if your desired program will run.

Good luck

---

### Post by serdar132 on 2010-07-24
Well my desired programme is Chessmaster Grandmaster edition. I saw that there were lots of people having problems running it. But in winehq says it should work almost perfectly.

Then I checked the bugzilla for winehq there were lots of bugs etc ... but then they saif if you have directx 9 installed as well as newest winehq it should work pretty good.

:(

---

### Post by Vaphell on 2010-07-24
wine supports most of dx9 out of the box you should try it first without full dx installation.

one bug i see in mailing lists is related to d3dx9_36, what happens if you install only that one?

---

### Post by serdar132 on 2010-07-24
How do I install only that one?

---

### Post by Zeike on 2010-07-24
The easiest way to install thinks like directx in wine is with winetricks.

see here: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

so if you run 'winetricks d3dx9' it should download & install directx 9 automatically.
or if you just want to install d3dx9_36 you can do 'winetricks d3dx9_36'

---

### Post by serdar132 on 2010-07-25
Well when I write  'winetricks d3dx9_36'  in terminal it says winetricks not found, but i thougt i had winetricks as i downloaded direct x from there (which didnt complete the setup nicely)

---

### Post by Zeike on 2010-07-25
> **serdar132 said:**
> Well when I write  'winetricks d3dx9_36'  in terminal it says winetricks not found, but i thougt i had winetricks as i downloaded direct x from there (which didnt complete the setup nicely)

You have to make sure you are running the command from the directory where you put the winetricks script.

Actually you'll probably have to do

"./winetricks d3dx9_36"

---

### Post by serdar132 on 2010-07-25
Thats weird. Now it says :

bash: ./winetricks: Permission denied

---

### Post by ThomasHC on 2010-07-25
Basically you need to do the following command to install wine tricks:

```
cd /usr/local/bin && sudo wget http://www.kegel.com/wine/winetricks && sudo chmod +x winetricks

```

Then just type:

```
winetricks
```

And a dialog should open and you can install direct x, along with many other Windows(TM) programs.

---

### Post by Zeike on 2010-07-25
> **serdar132 said:**
> Thats weird. Now it says :

bash: ./winetricks: Permission denied

You must make sure the script has the executable bit set with 'chmod +x ./winetricks'

---

### Post by serdar132 on 2010-07-25
Thank you man!

---

### Post by serdar132 on 2010-07-25
So when I try to install directx 9 it says internal system error occured. Please refer to DXError.log and Directx.log in your windows folder to determine problem

What should I do?

---

