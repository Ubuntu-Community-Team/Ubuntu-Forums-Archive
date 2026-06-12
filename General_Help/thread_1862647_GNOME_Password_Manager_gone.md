---
title: "GNOME Password Manager gone"
date: 2011-10-17
forum: General Help
---

### Post by elkingrey on 2011-10-17
I just upgraded to Ubuntu 11.10 and apparently with it my password manager, GPass, is gone. It wouldn't open, so I went to Synaptic Package Manager and it told me that not only is it not installed, but that I cannot install it because it is obsolete. 

Fair enough, but I couldn't imagine that it would delete the encrypted file that contains ALL of my passwords. To be honest, I never backed that file up because I am too much of a noob to know which file it was. Well, now that I'm in this predicament I had to figure out just which file contained all of my passwords. 

My best guess is that it is the passwords.gps file located in the ~/.gpass directory. There is also a passwords.gps.bak file. 

Now, assuming that these ARE the files that contain all of my passwords, my next problem is figuring out how to open or view them. I still have the password in my head that I plugged into the GPass program. I am assuming there has to be a way to access those files even without the GNOME Password Manager GUI software. 

If so, could somebody please clue me in on how to access them? Then I could transfer the data to Keepass, a seemingly more popular password manager. 

If the passwords.gps file is NOT the file I need, could somebody clue me in as to which file it is I am searching for? Any help would be much appreciated. Thank you!

---

### Post by malcomm77 on 2011-10-17
Install Revelation:

```
sudo apt-get install revelation
```

Once installed:

1. Import File
2. Select File (~/.gpass/passwords.gps)
3. Filetype: GPass 0.5.x (or newer)
4. Select Import

You should now be able to use Revelation password manager instead of GPass.

Hope that helps.

---

### Post by elkingrey on 2011-10-17
Wow! That was a huge help. I had just spent half the day laboriously transferring all of my usernames and passwords from GPass on a computer that still runs 11.04 to an Excel spreadsheet. Your method took all of two minutes! And revelation has a similar setup as GPass, but better. 

I appreciate the help!

---

### Post by jldr on 2011-11-08
> **malcomm77 said:**
> Install Revelation:

```
sudo apt-get install revelation
```Once installed:

1. Import File
2. Select File (~/.gpass/passwords.gps)
3. Filetype: GPass 0.5.x (or newer)
4. Select Import

You should now be able to use Revelation password manager instead of GPass.

Hope that helps.

YES ! thank's for the help ! :P

---

### Post by Grandma_DOG on 2012-05-20
> **malcomm77 said:**
> Install Revelation:

```
sudo apt-get install revelation
```Once installed:

1. Import File
2. Select File (~/.gpass/passwords.gps)
3. Filetype: GPass 0.5.x (or newer)
4. Select Import

You should now be able to use Revelation password manager instead of GPass.

Hope that helps.

I confirm this worked.
Also, if you choose 'GPass 0.40' it doesn't work, must choose 0.5.x

---

