---
title: "Adobe Air and Tweetdeck Suddenly fails"
date: 2010-04-08
forum: General Help
---

### Post by jkonrad on 2010-04-08
So I was happily using tweetdeck on Adobe Air in my Ubuntu 9.10 x64 installation when it suddenly stopped. It now reports a series of errors.

First I get a pop up that says.

"You are trying to connect to an unverified server s3.amazonaws.com (on port 443). Do you trust this server, and want to go ahead with the connection? - view certificate - This Session - Never"

Selecting any option makes no difference and takes me to the second error.

"Ooops, TweetDeck can't find your data. TweetDeck is having trouble using some of your passwords that are stored securely on your machine. Clicking Submit will clear this data so that you continue to use TweetDeck. Please note that you will have to add your accounts to TweetDeeck again. - OK"

I then click OK many times. Eventually I get the third error;

"Sorry, Adobe AIR is having a problem running on this computer. It looks like your computer is one of a very small number of computers that don't play well with Adobe AIR. We're actively working with Adobe on this, and it would really help us if you would let us know that you're having trouble by opening a ticket at [http://support.tweetdeck.com/tickets/new](http://support.tweetdeck.com/tickets/new) - OK"

I then click OK many times and get a blank Tweetdeck. Nothing works. I can not setup an account or even load the settings pane. I can "close" it, but the icon in the top bar stays and I cannot remove it till I reboot.

Any thoughts? I've uninstalled tweetdeck. Then Adobe AIR. Then re-installed both and I get the same error.

---

### Post by romilmittal on 2010-04-10
AIR Applications on Linux are sometimes not able to access the Encrypted Local Storage (ELS) keystore. This results in application displaying behaviors like the one you are seeing.

Please use the troubleshooting techniques mentioned in the following technote:
                 [http://kb2.adobe.com/cps/492/cpsid_49267.html](http://kb2.adobe.com/cps/492/cpsid_49267.html)

Let me know if it doesn't work for you,

Regarding the first dialog that you saw for certificate, whenever an AIR application (in this case Tweetdeck) tries to connect to a secure site, it asks for your approval if it is not already a trusted site on your system. You can accept it for the session if you want to continue.

Hope that helps,

Thanks,
-romil

---

### Post by jkonrad on 2010-04-10
Thank you for the reply. I tried this again after you recommended it, but I still get the same repose.

I had tried this earlier from a technician at TweetDeck. 

What ever the problem is, removing the ELS has no affect. Neither did creating a new gnome2 keyring.

Thank you for the thoughts though.

---

### Post by mkalen on 2010-04-12
I had the same problem on Kubuntu 9.10 64b (i.e. using KDE wallet and not GNOME keyring).

I could solve the problem by:
[LIST=1]
[*]Kill TweetDeck process
[*]Remove Adobe AIR ELS directory (rm -rf ~/.appdata/Adobe/AIR/ELS)
[*]Restart TweetDeck and re-enter all account data
[/LIST]

I still get the SSL certificate warning on each start but at least TweetDeck account data can now be retrieved.

@jkonrad: I should also mention that I granted Adobe AIR permanent access to the KDE wallet on first install. If there is a similar option for the GNOME keyring, you might try granting AIR access and follow the steps above.

---

### Post by jkonrad on 2010-04-12
Thanks for the tip with the ELS. It did not work for me. I'm looking forward to a format/install of 10.04 soon so that will likely fix the issue. Thanks for the help.

Jon

---

### Post by mkalen on 2010-04-13
> **jkonrad said:**
> Thanks for the tip with the ELS. It did not work for me.

It apparently only worked for me for a short time... today TweetDeck cannot access the account data anymore. Back to square one.

I doubt that Ubuntu 10.04 will remedy this since it seems to be a problem in Adobe AIR or (more likely?) TweetDeck itself.

Did you file a bug report with TweetDeck yet?

---

### Post by jkonrad on 2010-04-13
I did log a ticket with Tweetdeck. They first suggested the ELS thing too.

Since it was working earlier in 9.10 I just assumed some update or additional software I installed broke it. You're probably right, but starting fresh always feels like it's going to help!

If I come across anything to help, I'll post here.

---

### Post by eigenstil on 2010-04-13
hey there!

i'm experiencing exactly the same errors as you described. and i'm absolutely sure, that it is a bug in tweetdeck.

because i recently (about 10 minutes ago) installed adobe air, and 5 mins later i installed tweetdeck and i get the same errors and message about the certificate...

hopefully they will fix this issue. i really like tweetdeck...

---

### Post by dktnecro on 2010-04-22
hey guys
i had exactly the same problem as described. I solved it by installing the 32bit lib for gnome-keyring.
Look here for [further]("http://blog.gnu-designs.com/cleanly-installing-and-running-adobe-air-and-tweetdeck-on-64-bit-linux") instructions (at point 8.)
Now Tweetdeck works without any crashes - hope it does for you too...

Greets
dktnecro

---

### Post by mkalen on 2010-04-23
> **dktnecro said:**
> I solved it by installing the 32bit lib for gnome-keyring.

This seems to be the trick for 64bit KDE as well. Since Adobe AIR is a 32bit application it needs the 32bit version of the KDE wallet client libraries in order to get the AIR ELS working properly. (Similarly on GNOME, the 32bit libraries for GNOME keyring like the blogpost you linked to describes.)

You can check if 32bit kdewallet client libraries are installed by testing the dynamic link dependencies of e.g. Adobe AIR's libaddkey.so:
```
ldd "/opt/Adobe AIR/Versions/1.0/Resources/libaddkey.so" | grep kwallet
```

If you get something like "libkwalletclient.so.1 => not found" you will need to install the 32bit library. In Ubuntu 9.10 this library is in the kdelibs4c2a package, but this can be detected automatically by the getlibs package (see [http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")):
```
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
sudo getlibs libkwalletclient.so.1
sudo ldconfig

```
Re-run the ldd command above to check that the client library can now be resolved.

After this, erase Adobe AIR ELS and enter your account data anew:
```
rm -rf ~/.appdata/Adobe/AIR/ELS
TweetDeck
```

After this, AdobeAIR shows up in KDE wallet manager with an ELSKey stored password.

It all boils down to Adobe AIR beeing a 32bit app managed completely outside of the distribution's normal dependency resolving (APT on Ubuntu/Debian). If Adobe produced a DEB for AIR they could mark these library requirements in their package, making life easier for users of DEB-based distributions.

---

### Post by almadark on 2010-04-28
Thanks dktnecro

It work's for me!

---

### Post by virious on 2011-07-31
> **mkalen said:**
> This seems to be the trick for 64bit KDE as well. Since Adobe AIR is a 32bit application it needs the 32bit version of the KDE wallet client libraries in order to get the AIR ELS working properly. (Similarly on GNOME, the 32bit libraries for GNOME keyring like the blogpost you linked to describes.)

You can check if 32bit kdewallet client libraries are installed by testing the dynamic link dependencies of e.g. Adobe AIR's libaddkey.so:
```
ldd "/opt/Adobe AIR/Versions/1.0/Resources/libaddkey.so" | grep kwallet
```

If you get something like "libkwalletclient.so.1 => not found" you will need to install the 32bit library. In Ubuntu 9.10 this library is in the kdelibs4c2a package, but this can be detected automatically by the getlibs package (see [http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")):
```
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
sudo getlibs libkwalletclient.so.1
sudo ldconfig

```
Re-run the ldd command above to check that the client library can now be resolved.

After this, erase Adobe AIR ELS and enter your account data anew:
```
rm -rf ~/.appdata/Adobe/AIR/ELS
TweetDeck
```

After this, AdobeAIR shows up in KDE wallet manager with an ELSKey stored password.

It all boils down to Adobe AIR beeing a 32bit app managed completely outside of the distribution's normal dependency resolving (APT on Ubuntu/Debian). If Adobe produced a DEB for AIR they could mark these library requirements in their package, making life easier for users of DEB-based distributions.

Had the same issues with TweetDeck and Adobe AIR, your tip worked like a charm! Thanks mate! :).

---

