---
title: "Renew Google Chrome"
date: 2011-03-11
forum: General Help
---

### Post by Cpierce on 2011-03-11
I was downloading a theme from Gnome eyecandy and noticed that the file was bigger than I expected, so I stopped and cancelled the download. However, since then my Chrome has been acting weird. I have sites asking for my keyring password, which I am not comfortable with. Those same sites on other browsers don't ask for keyring. I cleaned with Bleachbit, and scanned with Avast and Bitdefender, but the problem is still there.

 I want to "renew" Chrome. For Firefox, I just go to my home folder and delete .Mozilla . How do I do the same for Chrome ?  I am using Lucid and Chrome 10.0.648.127

---

### Post by lithopsian on 2011-03-11
How did you install chrome?  From a package?

---

### Post by Cpierce on 2011-03-11
yes, with a deb package

---

### Post by oldos2er on 2011-03-11
Chrome's settings are in ~/.config/google-chrome/Default

---

### Post by searchfgold6789 on 2011-03-11
I think this command will do the trick:```
sudo apt-get install chromium-browser && sudo apt-get --purge autoremove && sudo apt-get install chromium-browser
```

---

### Post by ajgreeny on 2011-03-11
> **searchfgold6789 said:**
> I think this command will do the trick:```
sudo apt-get install chromium-browser && sudo apt-get --purge autoremove && sudo apt-get install chromium-browser
```
I think you meant ```
sudo apt-get [COLOR=Red]remove[/COLOR] chromium-browser && sudo apt-get --purge  autoremove && sudo apt-get install chromium-browser
```but in fact I think just removing the configuration in ~/.config would do the trick without removing and reinstalling the whole package.

Even purging the application/package will not get rid of the configuration in /home, so you would still have the exact same problem, I think.

---

### Post by Irony on 2011-03-11
Just delete google chrome here;

```
~/.cache
```

and from here;

```
~/.config
```

That will reset google chrome to its default.

---

### Post by Cpierce on 2011-03-11
I deleted the files in .config and .cache. Then I ran the terminal command. It just installed Chromium instead of fixing Chrome. My understanding is that Chrome is stable and Chromium is development and gets updated all the time. That's why I use Chrome. 

Can I just replace Chromium with Chrome in the command line ?

---

