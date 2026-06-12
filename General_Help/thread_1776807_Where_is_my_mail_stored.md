---
title: "Where is my mail stored?"
date: 2011-06-06
forum: General Help
---

### Post by Maheriano on 2011-06-06
I'm using the default email that comes with Ubuntu.

What I had:
- 10.10 installed onto a terabyte hard drive with email organized into individual folders under the main folder

What I did:
- bought a new terabyte hard drive and installed 11.04 on it
- set up old terabyte drive as backup drive but kept everything on it

So how do I dig into the old drive to get the email off of it and into my 11.04 install? I didn't overwrite any files, I need to get the mail off before I can do that.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **Maheriano said:**
> I'm using the default email that comes with Ubuntu.

What I had:
- 10.10 installed onto a terabyte hard drive with email organized into individual folders under the main folder

What I did:
- bought a new terabyte hard drive and installed 11.04 on it
- set up old terabyte drive as backup drive but kept everything on it

So how do I dig into the old drive to get the email off of it and into my 11.04 install? I didn't overwrite any files, I need to get the mail off before I can do that.

Do you see the drive when you open file manager?

---

### Post by Maheriano on 2011-06-06
Oh ya, the drive works fine, I just don't know which files to copy over to get my mail back. Do you know where the files are?

---

### Post by linuxinstalledfromhdd on 2011-06-06
Did you backup evolution?  

[http://ubuntuforums.org/showthread.php?t=75859](http://ubuntuforums.org/showthread.php?t=75859)

---

### Post by Maheriano on 2011-06-07
I'm seriously considering that I didn't explain this properly. I'll try it again, my old hard drive is completely intact, if I swapped the drives around I could boot into it no problem. Everything is the same as the last day I used it, I just have it set up as a slave drive right now and I'm wondering where the mail is stored so I can get it copied to my new drive. I don't want to go through the hassle of swapping the drives, booting into it, exporting the mail and hoping it works.

Is there an easy way of copying a couple of files?

---

### Post by kjuergen on 2011-06-07
I don't use evolution which means I don't know the exact path. Somewhere in your home directory most likely is a folder .evolution. As it has the dot at the start you will only be able to see it when you set your file manager to show hidden files. In this folder you will find the mail most likely in mbox format (everything in one big file).

It will definitely be in a hidden file (mine is in .thunderbird and for Kmail it's in .kde/shared/apps/mail if I recall correctly)

Juergen

---

### Post by amauk on 2011-06-07
Evolution stores mail in
```
~/.local/share/evolution/mail
```

---

### Post by HermanAB on 2011-06-07
Howdy,

If you used Evolution with POP, then you can copy the mail folder as shown above.

If you use IMAP, then your mail remains on the mail server and doesn't need copying.

---

### Post by Quarkrad on 2011-06-07
I'm a newbie so obviously no expert.  I do not use Evolution (I use Thunderbird in both imap and pop forms for different email accounts) but most of these emails clients seem to work the same.  I have a similar set up in that I have created local folders and copy important emails from my 'email system' to the local folders on my PC.  So, like you, when I install a new version of Ubuntu or a new hard disc I have to copy everything over.  In Thunderbird (**./Thunderbird**) there is a user profile folder - it might be the case that you have a user profile folder in your **~/.local/share/evolution/mail** folder.  It could be the case that your (local PC folders with emails) local folders are in this user profile folder.  (I backup **/home** every time I power down so all my email is automatically backup up).

---

### Post by Maheriano on 2011-06-07
> **HermanAB said:**
> Howdy,

If you used Evolution with POP, then you can copy the mail folder as shown above.

If you use IMAP, then your mail remains on the mail server and doesn't need copying.

I have some POP, some IMAP and some saved folders. It's a mix.

---

### Post by Quarkrad on 2011-06-08
I'm a newbie so be careful what I'm about to say !!!!!   Although I do not use Evolution I set it up on my PC to send/receive to one of my email accounts.  I sent/received a number of mails to it so I had some data in it.  I then created a new folder under **On This Computer** (which I called Local) to which I copied a number of emails from my In-Box.  I then navigated to my **Ubuntu Home** folder (**Places/Home Folder**) and set it (**View/Show Hidden Files**) so I could see the hidden files in this directory.  There is a folder called ./Evolution.  I copied this folder to by Backup HD and un-installed Evolution from Ubuntu and deleted the ./Evolution folder from my **Home Folder**.  I then re-booed.  Obviously I then had no Evolution so I installed it from the Software Centre.  Launched Evolution and there was a vanilla package with no emails in it - but a new ./Evolution folder in **Ubuntu/Home**.  I close Evolution down and then copied the original ./Evolution folder from my Backup HD to **Ubuntu/Home** replacing the new one.  Re-launching Evolution I had my original emails, the set up to my email account and the Local folder I set up with copied emails in it.   So ....  in principle this is similar to Thunderbird.

---

### Post by ttguy on 2011-06-08
> **amauk said:**
> Evolution stores mail in
```
~/.local/share/evolution/mail
```

On my install it would appear to be in ~/.evolution/mail

---

### Post by DZ* on 2011-06-08
> **HermanAB said:**
> If you use IMAP, then your mail remains on the mail server and doesn't need copying.

IMAP folders can be selected for offline usage (right-click on a folder -> Properties). Then they are stored in ```
~/.local/share/evolution/mail/imap
```

---

### Post by DZ* on 2011-06-08
> **ttguy said:**
> On my install it would appear to be in ~/.evolution/mail

It was migrated to .local in Natty

---

### Post by Maheriano on 2011-06-15
Now that I copied my mail folder from the old drive to the new drive, now what do I do? They still don't show up in Evolution.

---

### Post by Maheriano on 2012-05-29
Bumping after a year. Still need an answer.

---

