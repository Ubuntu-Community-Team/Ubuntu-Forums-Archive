---
title: "Need help with gpg key and launch pad"
date: 2010-04-07
forum: General Help
---

### Post by note32 on 2010-04-07
I'm trying to register my gpg key with launch pad but its not letting me I'm really sure what I'm doing:confused: wrong i followed the steps that lauchpad provided any help would be appreciated

---

### Post by colorlessprism on 2010-04-07
The easiest way to generate a new OpenPGP key in Ubuntu is to use  the *Passwords and Encryption Keys* tool.     
      

Open *Applications > Accessories  > Passwords and Encryption Keys*.     
      Select *File > New*, select *PGP  Key* and then follow the on-screen instructions.     
      

Now you'll see your new key listed in the *Passwords and  Encryption Keys* tool.           
      

      Before you add your key to Launchpad, you need to push it to the  Ubuntu keyserver.
      Open a terminal and type: "gpg --list-keys"
[B]
[/B]You'll see a list of OpenPGP keys in  your system, including the one you've just created, were after the "PUB" one it will be something like 1055A/12345678 you need the "12345678"

     Now type "gpg --send-keys --keyserver keyserver.ubuntu.com 12345678"
      obviously you will use your own number and not 12345678


      you should get a message similar to:
      gpg: sending key 12345678 to hkp server  keyserver.ubuntu.com
      It can take up to ten minutes before your key is available to  Launchpad

To import your OpenPGP key into Launchpad, you need the key's  fingerprint.
      
Open a terminal and type[FONT=Verdana] "[/FONT]gpg --fingerprint"
you need the "Key Fingerprint" number its long so copy and paste.

---

