---
title: "firefox bookmarks gone after update"
date: 2009-08-12
forum: General Help
---

### Post by DrScum on 2009-08-12
running 8.04 just did the last update a minute ago, after updating all firefox bookmarks are gone and "back" button is not active. Bummer! Any help out there?

---

### Post by young-root on 2009-08-12
> **DrScum said:**
> running 8.04 just did the last update a minute ago, after updating all firefox bookmarks are gone. Bummer! Any help out there?

well firefox was updated so i guess it would erase any previous files just like a fresh install of ubuntu would...it should be backed up though...i'm not quite sure how to retreive it

---

### Post by emeraldgirl08 on 2009-08-12
For future ref do yourself a favor and add Xmarks to your add-ons in Firefox!

I know there's a way you can do a manual backup but that would entail doing it everytime you add a new bookmark.

Xmarks does this all for you and can install your bookmarks on any other computer if you want.

---

### Post by DrScum on 2009-08-12
Firefox is acting completely weird! You can access the backup through Organize Bookmarks and there is a backup from today available, but when I select it, nothing happens.
When starting it doesn't open my homepage as set in preferences.

---

### Post by michy99 on 2009-08-12
You may have messed up the ownership of your Firefox profile. Enter this in a terminal, replacing USERNAME with your username.```
sudo chown USERNAME:USERNAME -R ~/.mozilla/firefox*
```Then re-start Firefox.

---

### Post by emeraldgirl08 on 2009-08-12
Have you tried restarting your computer?

---

### Post by DrScum on 2009-08-12
thanks for the input, 

did change ownership and, as a former Windows user did of course restart as the very first option, still in trouble.
Just found out about another problem: when trying to shut down the sucker freezes. Hadn't that after the first shutdown after updating though.

---

### Post by DrScum on 2009-08-12
well, I just found out that the machine doesn't freeze, only the panel disappears. I can still start a program from a desktop launcher.
This looks very bad. Is there a way to go back to the situation before the last upgrade?

---

### Post by emeraldgirl08 on 2009-08-12
Michy and others- Do you think this would work???

Open up terminal. You may need to do this twice.

```
sudo apt-get update
```

Then restart.

---

### Post by DrScum on 2009-08-12
when doing this I get an error message saying:
W: GPG error ....some signatures couldn't be verified since the public key is not available and the machine still acts weird meaning it shows the same symptoms as stated above.

---

### Post by emeraldgirl08 on 2009-08-12
Give [THIS]("http://en.kioskea.net/faq/sujet-809-debian-apt-get-no-pubkey-gpg-error") a look and see if that helps!

---

### Post by lovinglinux on 2009-08-12
For the bookmark issue, see **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

This is a very common issue.

---

### Post by DrScum on 2009-08-12
emeraldgirl08 I did what it says in the link and was able to update without error message. After restarting......things seem to be ok, even the bookmarks are back!

Open Source rules!!

Thanks for your help!

---

### Post by emeraldgirl08 on 2009-08-12
:popcorn:

:KS

Yer in the right place for help!

I get answers here all the time too!

Congrats :)

---

