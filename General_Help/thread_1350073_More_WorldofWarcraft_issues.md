---
title: "More WorldofWarcraft issues"
date: 2009-12-08
forum: General Help
---

### Post by Bluefox79 on 2009-12-08
World of warcraft runs but when you try to log in it minimizes (doesen't crash) and a error pops up 
'Microsoft Visual C++ runtime library'
runtime error
program Z...
r6034
an application has made an attempt to load the c runtime library incorrectly.
please contact the application's support team for more information.

I'm using ubuntu with the latest updates/versions, please help,
seems blizzard screws this up every patch lately..

---

### Post by Bluefox79 on 2009-12-09
for real? no replies?

---

### Post by mikemikemike on 2009-12-09
Create a new another partion install Windows. Its not worth the aggravation.  Even Cedega in a PIA.

---

### Post by Bluefox79 on 2009-12-09
I was going to goof off, but, seriously, offer good advice guy, its not cool to tell poeple to go bacc to holy exploder.

Bump.

hehe, sploder..

also, ditch cedega, best 15$ a month saved ever.

Ever.

---

### Post by Linc_mc on 2009-12-09
I am having the same issue is there anyone that can help?

---

### Post by Bluefox79 on 2009-12-10
Bumpation: a word describing the action of bumping a thread.

---

### Post by Vaphell on 2009-12-10
google is your friend
[http://www.google.com/search?hl=pl&source=hp&q=world+of+warcraft+r6034&btnG=Szukaj+w+Google&lr=&aq=&oq=world+of+warcraft](http://www.google.com/search?hl=pl&source=hp&q=world+of+warcraft+r6034&btnG=Szukaj+w+Google&lr=&aq=&oq=world+of+warcraft)

several threads about r6034

---

### Post by Bluefox79 on 2009-12-11
***FIXED***

***FIXED***

Here is what I did:

Step one, DO NOT DELETE ANYTHING!!!'

Step two: Navigate to your World of Warcraft Directory (this will be different depending on your version of Windoze) Mine was found in:

C:\Users\Public\Games\World of Warcraft

Step Three: Edit the Microsoft.VC80.CRT.manifest file

Step Four: Find the line that looks like this:

<assemblyIdentity type="win32" name="Microsoft.VC80.CRT" version="8.0.50727.4053" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3b"></assemblyIdentity>

Replace the version number to 8.0.50727.762 (it should look like this)

<assemblyIdentity type="win32" name="Microsoft.VC80.CRT" version="8.0.50727.762" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3b"></assemblyIdentity>

Step Five: Save the file (it is a good idea to first make a backup file before overwriting)

All done. Your WoW should work perfectly. (You may also need to apply the aforementioned updates). But this worked for me.

<<Thank Fallhalen from winehq forums for this fix, thought I'd pass it on.>>

---

### Post by polpak on 2009-12-11
Nice fix!

I got mine working using winetricks and installing the visual c runtime 2008, but I like this solution much better.

---

### Post by Ylon on 2009-12-11
Looks like Vaphel advice get right that. I would suggest to refine it in:
[http://www.google.com/search?q=site%3A.forums.worldofwarcraft.com+wine+r6034](http://www.google.com/search?q=site%3A.forums.worldofwarcraft.com+wine+r6034)


It's more selective ;)

---

