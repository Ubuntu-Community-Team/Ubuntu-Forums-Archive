---
title: "Updating Firefox in Jaunty"
date: 2010-02-04
forum: General Help
---

### Post by Uadebisi on 2010-02-04
Hi,

Just got rid of 9.10 & installed 9.04 & noticed that it uses an older version of Firefox. I read up on this a bit on the FF site & not sure if it is a good idea to upgrade FF to a newer version outside of Ubuntu & don't know how to upgrade from within Jaunty, or if its even possible.

Can anyone offer any suggestions?

Thanks!

---

### Post by bwang on 2010-02-04
The official builds of Firefox will work, as long as you remember to change your launchers to point towards the new file.
Also, you will need to make symlinks to your plugins in ~/.mozilla/plugins since the official Firefox does not see plugins in /usr/lib/mozilla/plugins.

---

### Post by lovinglinux on 2010-02-04
See **[COLOR="Sienna"]Installing Other Versions[/COLOR]** section the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). If you are on 32bit, then I recommend using method #2.

---

### Post by Uadebisi on 2010-02-04
> **bwang said:**
> The official builds of Firefox will work, as long as you remember to change your launchers to point towards the new file.
Also, you will need to make symlinks to your plugins in ~/.mozilla/plugins since the official Firefox does not see plugins in /usr/lib/mozilla/plugins.

Thanks but would you mind explaining how to perform the tasks that you are suggesting? :D

---

### Post by scouser73 on 2010-02-04
[[COLOR="Red"]**Download Firefox 3.6**[/COLOR]]("http://www.mozilla.com/en-US/firefox/all.html")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

Enter these commands in Terminal

> **sudo -i**
Enter your password if asked
> **cd /opt**
> **chown -R username firefox**
[COLOR="Red"]**The username is what you use to log in to Ubuntu**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

---

### Post by Uadebisi on 2010-02-04
Thanks scouser73!

Well, looks complicated but I could try. Although I do not know what you mean by:
> Copy & paste the Firefox file that you have just extracted to **/opt**

How do I get to /opt? Remember, I have been using Windows since DOS

---

### Post by Uadebisi on 2010-02-04
> **lovinglinux said:**
> See **[COLOR=Sienna]Installing Other Versions[/COLOR]** section the [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567"). If you are on 32bit, then I recommend using method #2.

Thanks for the info but it all seems to be a bit over my head. Perhaps I should just stick with the older version of FF.

Also, as you may have read, I switched to Jaunty as I was tired of the constant & multiple bugs that I experienced with 9.10. However, as I was about to review your tutorial, Jaunty has already begun acting up as well. The screen is intermittently jumping, flashing & shifting, for lack of a better explanation. It doesn't matter what I am doing, whether using FF, Evolution or checking my preferences, this new issue occurs. 

This is a new one! I have never experienced this w/ Windows or Ubuntu. The final straw as to why I removed 9.10 was that the machine would freeze. See here:
[http://ubuntuforums.org/showthread.php?t=1379704](http://ubuntuforums.org/showthread.php?t=1379704)


So, no point of updating the browser when the OS seems unstable. :(

---

