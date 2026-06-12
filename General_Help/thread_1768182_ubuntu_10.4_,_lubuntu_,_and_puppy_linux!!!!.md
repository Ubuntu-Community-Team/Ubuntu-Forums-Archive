---
title: "ubuntu 10.4 , lubuntu , and puppy linux!!!!"
date: 2011-05-26
forum: General Help
---

### Post by evilheart on 2011-05-26
hi , i am new linux user , i downloaded ubuntu 11.04 on my my Pentium 4 , 512 MB RAM pc , off course unity was too heavy , so i switched to Gnome - xubuntu - and now using LXDE.

the performance is not very  bad , but sometimes it lags with ubuntu software center , any way i went  to linux looking for smooth performance and less bugs.and i am feeling that natty still somehow heavy , so i am thinking of switching to another linux distro , and i need some advice and user experiences , and now i looking for light , very user friendly distro. with good system control tools like gnome , i had 3 choices now :

1 - Lubuntu : it works on LXDE which i am using now , but LXDE that i have lack control tools , it doesn't even have a KB layout preferences tool.
but i don't if it will be different with Lubuntu as it is designed to work with LXDE and to be light in general.

2 - downgrade to 10.4 : that's from synaptic , right?? 
does that will increase the performance greatly? and what exactly will my system lose when i downgrade? for a normal user?

3- puppy linux : it is designed to be very portable and light as they say , but i don't know what will be the trade off , also installing it on the hard disk seems to be very annoying , so i want to make it last choice.

i hope you tell me your opinion.

---

### Post by ratcheer on 2011-05-26
First, I don't think Ubuntu 10.04 would save you all that much in resource requirements. Some, for sure, but not the difference in night and day.

I have recently tried both Puppy and Xubuntu and I liked both, very much. Of the two, I prefer Xubuntu, but Puppy is still very nice. Note that there was very recently a new release of Wary Puppy, which is intended specifically for older, underpowered systems. You can see it on the current front page of DistroWatch. However, the Puppy I tried was Lucid Puppy.

Tim

---

### Post by lightstream on 2011-05-26
How fast is the P4? What about the hard drive - how fast is that?

If your machine is at least 1 GHz, I would say go for xubuntu. If you have a 1 GHz CPU and your HDD is not ancient, your real bottleneck is the half-gig of RAM. xfce which is used by xubuntu is really efficient in its memory usage, so I would say it would be the best one for you.

Puppy is really lightweight and great for very old and slow machines, but I found the trade off pretty high, as it has a very clunky 1990s feel to it IMO.

---

### Post by evilheart on 2011-05-26
thanks guys for your reply , i already downloaded and tried XFCE4 before but it wasn't that fast than gnome , XLDE is faster but with less system control options as i mentioned . 

on xubuntu site , they mentioned i can simply switch from ubuntu by installing xfce , so the my original distro wasn't xubuntu , 
does that make a difference? 
if i installed Xubuntu from its CD from the beginning , will xfce work better??? is xubuntu configured from the beginning to make xfce work much better than the other desktop environments???

---

### Post by evilheart on 2011-05-26
> **ratcheer said:**
> First, I don't think Ubuntu 10.04 would save you all that much in resource requirements. Some, for sure, but not the difference in night and day.

I have recently tried both Puppy and Xubuntu and I liked both, very much. Of the two, I prefer Xubuntu, but Puppy is still very nice. Note that there was very recently a new release of Wary Puppy, which is intended specifically for older, underpowered systems. You can see it on the current front page of DistroWatch. However, the Puppy I tried was Lucid Puppy.

Tim

i downloaded Lucid puppy , but still didn't try it , did you face any problems with it? what makes Xubuntu better?

---

### Post by snowpine on 2011-05-26
> **evilheart said:**
> the performance is not very  bad , but sometimes it lags with ubuntu software center , any way i went  to linux looking for smooth performance and less bugs.

If your only performance issue is with the Ubuntu Software Center, you might consider learning how to update and install apps from the Terminal, for example:

```
man apt-get
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install firefox
```

and so forth.

To answer your specific question, L/X/K/Ubuntu are all the same "core" operating system with different "desktop environments." If you want to try Lubuntu simply:

```
sudo apt-get install lubuntu-desktop
```

Then, log out and choose Sessions, LXDE from the login screen. Same goes for "xubuntu-desktop".

Puppy is very fast and worth a test drive, in my opinion.

---

### Post by ratcheer on 2011-05-26
> **evilheart said:**
> i downloaded Lucid puppy , but still didn't try it , did you face any problems with it? what makes Xubuntu better?

I had no problems with Lucid Puppy, at all. I like it quite a bit. The reason I preferred Xubuntu is because it just seems to be a more complete Linux implementation - I am pretty sure it actually is.

I did not attempt to install Puppy to my hard drive. I was quite surprised that I was able to install my proprietary nvidia driver, save and exit, restart, and it still had the video driver. Whatever they are doing is pretty impressive.

Tim

---

### Post by kerry_s on 2011-05-26
> 1 - Lubuntu : it works on LXDE which i am using now , but LXDE that i have lack control tools , it doesn't even have a KB layout preferences tool.
but i don't if it will be different with Lubuntu as it is designed to work with LXDE and to be light in general.

see pic, i'm running lubuntu 11.04

---

### Post by wildmanne39 on 2011-05-26
> **evilheart said:**
> hi , i am new linux user , i downloaded ubuntu 11.04 on my my Pentium 4 , 512 MB RAM pc , off course unity was too heavy , so i switched to Gnome - xubuntu - and now using LXDE.

the performance is not very  bad , but sometimes it lags with ubuntu software center , any way i went  to linux looking for smooth performance and less bugs.and i am feeling that natty still somehow heavy , so i am thinking of switching to another linux distro , and i need some advice and user experiences , and now i looking for light , very user friendly distro. with good system control tools like gnome , i had 3 choices now :

1 - Lubuntu : it works on LXDE which i am using now , but LXDE that i have lack control tools , it doesn't even have a KB layout preferences tool.
but i don't if it will be different with Lubuntu as it is designed to work with LXDE and to be light in general.

2 - downgrade to 10.4 : that's from synaptic , right?? 
does that will increase the performance greatly? and what exactly will my system lose when i downgrade? for a normal user?

3- puppy linux : it is designed to be very portable and light as they say , but i don't know what will be the trade off , also installing it on the hard disk seems to be very annoying , so i want to make it last choice.

i hope you tell me your opinion.

Hi, have you logged out and clicked on your user name and gone to the bottom of the screen and select ubuntu classic no effects that is lighter on resources.

---

### Post by lightstream on 2011-05-26
> **wildmanne39 said:**
> Hi, have you logged out and clicked on your user name and gone to the bottom of the screen and select ubuntu classic no effects that is lighter on resources.

Once you've installed XFCE in your vanilla Ubuntu, you'll need to activate it in a similar fashion to the above if you haven't already done so.

---

### Post by spcwingo on 2011-05-26
Debian testing with GNOME.  ;)

---

### Post by evilheart on 2011-05-27
> **snowpine said:**
> If your only performance issue is with the Ubuntu Software Center, you might consider learning how to update and install apps from the Terminal, for example:

```
man apt-get
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install firefox
```

and so forth.

To answer your specific question, L/X/K/Ubuntu are all the same "core" operating system with different "desktop environments." If you want to try Lubuntu simply:

```
sudo apt-get install lubuntu-desktop
```

Then, log out and choose Sessions, LXDE from the login screen. Same goes for "xubuntu-desktop".

Puppy is very fast and worth a test drive, in my opinion.


i installed apps from the terminal before , but i should know the exact application name used for the script , generally i don't like to use the terminal , also ubuntu software center is the only GUI tool to install .deb packages as i know.

i installed LXDE only , does that mean i am running lubuntu? 
i have read on their site that lubuntu uses different infrastructure than ubuntu , i don't know exactly what does that means !!! does that mean Lubuntu is designed to work mainly under XLDE like ubuntu is somehow designed to work under gnome? 

i think the main question for me now , will lubuntu work better than normal ubuntu with XLDE installed on it???? , 
i removed gnome after installing XFCE , which i feel it caused some problems , and now thinking seriously to install a clean lubuntu and try it.

---

### Post by evilheart on 2011-05-27
> **kerry_s said:**
> see pic, i'm running lubuntu 11.04

hmmmmmmmm!!!! it doesn't look like the XLDE i had , for some reason i feel that is more than a theme!!! , is that its native theme?
also in the XLDE i have , there is no GUI tool to change KB layout permanently , may be that is a new version.

---

### Post by kerry_s on 2011-05-27
> **evilheart said:**
> hmmmmmmmm!!!! it doesn't look like the XLDE i had , for some reason i feel that is more than a theme!!! , is that its native theme?
also in the XLDE i have , there is no GUI tool to change KB layout permanently , may be that is a new version.

no, it's not stock. i tweaked it to me. everything is still lxde.

adding lubuntu to standard gnome is useless, you have to go with straight lubuntu to get the savings & speed.

if you install on top of ubuntu, i assume it thinks you would use the gnome stuff in lxde, so you don't get the lxde apps that do the same thing.

i'm still playing with the look. i'm an old user of wm's so tweaking them is easy for me & i'll just write scripts to make whats there easier to use, instead of installing something else. example: lubuntu uses scrot to take screen shots, but there is no gui, so i made 1, then just changed the print short cut. lubuntu doesn't have zenity installed, so i used the standard xmessage.

---

