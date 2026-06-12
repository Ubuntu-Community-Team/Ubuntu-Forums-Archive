---
title: "Thunderbird upgrade kills provider for Google Calendar and Lightning"
date: 2010-07-07
forum: General Help
---

### Post by timgood on 2010-07-07
Latest update to Thunderbird 3.0.5 killed Lightning and Provider for Google Calendar. Lighting can be downgraded to version 1.0b1 which works ok, but nothing seems to get Google Calendar working with this version. Any ideas?

---

### Post by scouser73 on 2010-07-07
I assume that the version of Thunderbird you have installed is from the repositories, whereas if you install from the Mozilla website it would be version 3.1.  I have installed Thunderbird via that way and Lightening works fine for me, here's my instructions to install it that way if you wish. 

**[COLOR="Red"]**NOTE**[/COLOR] The following will in no way affect your Thunderbird profile**

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3.1**[/COLOR]]("http://www.mozillamessaging.com/en-GB/thunderbird/")


**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by timgood on 2010-07-07
I have built a 64 bit .deb for Thunderbird 3.1 which works well with Lightning and Provider for Google Calendar. If enough people want it I can make it available.

---

### Post by Strubbl on 2010-07-07
it would be cool for my laziness if you would share the deb timgood ;)

---

### Post by hlmyers on 2010-07-07
I for one, would like a copy of your 64b .deb file.

Cheers,

Harry

---

### Post by timgood on 2010-07-07
You can download my 64 bit .deb for Thunderbird [here]("http://eekageek.co.uk/index.php?page=downloads"). Remember, this works for me - it may not work for you.

Hope this helps.

---

### Post by Strubbl on 2010-07-07
doesn't work for me. i installed the deb, but in thunderbird i can't install lightning. i am getting the error:
""Lightning" could not be installed because it is not compatible with your Thunderbird build type (Linux_x86_64-gcc3). Please contact the author of this item about the problem."

---

### Post by Oolongtea on 2010-07-07
this helped a lot :)

---

### Post by colin.p on 2010-07-07
Thanks scouser73 for the info, worked perfectly.

Colin

---

### Post by timgood on 2010-07-08
> **Strubbl said:**
> doesn't work for me. i installed the deb, but in thunderbird i can't install lightning. i am getting the error:
""Lightning" could not be installed because it is not compatible with your Thunderbird build type (Linux_x86_64-gcc3). Please contact the author of this item about the problem."

You need the 1.0b2 64 bit Lightning which you can download [here]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/lightning.xpi"). (Right click and 'save as').


Hope this helps.

---

### Post by evencoil on 2010-07-11
Thanks timgood, your .deb worked for me.

Is there a google calendar provider that works for the new version?

Edit: Oh, nevermind, the official one seems to work fine:

[https://addons.mozilla.org/en-US/thunderbird/addon/4631/](https://addons.mozilla.org/en-US/thunderbird/addon/4631/)

---

### Post by Strubbl on 2010-07-11
> **timgood said:**
> You need the 1.0b2 64 bit Lightning which you can download [here]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/lightning.xpi"). (Right click and 'save as').


Hope this helps.
yes that helped! :)

(i have built my own deb for those who are interested: [http://linux4tw.de/~strubbl/thunderbird_3.1-1_amd64.deb]("http://linux4tw.de/%7Estrubbl/thunderbird_3.1-1_amd64.deb"))

thanks tim

---

### Post by SimonJones on 2010-08-31
> **timgood said:**
> You need the 1.0b2 64 bit Lightning which you can download [here]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/lightning.xpi"). (Right click and 'save as').


Hope this helps.

It did, thank you! Saved hours of Googling! :-)

---

### Post by Hilko on 2010-12-07
You can install the lightning extension for Thunderbird by openening synaptic package manager and install the package
```
xul-ext-lightning
```

---

