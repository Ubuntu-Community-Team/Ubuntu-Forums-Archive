---
title: "Flash upgrade in 10.04"
date: 2011-09-29
forum: General Help
---

### Post by indiana_crook on 2011-09-29
I'm having an issue with Flash... My firefox and Chrome both tell me that I must upgrade flash player in order to view things on certain sites, like Youtube.  I have reinstalled the flash-installer several times and all the plugins that are available, but I still get the message when I go on Youtube that says I need to upgrade flash.  I have even tried the Flash-Aid add-on.  My other computers run on the same version of Ubuntu (10.04 LTS) and they have no problems...  Any ideas?

---

### Post by An Sanct on 2011-09-30
The message might be a product of website misconfiguration. A local website here in my country told me to "go grab the newest flash version, version 8" until recently ... needless to say, I allready had version 10 installed at that point.

I always trust FlashAid, it is a blessing for firefox...

PS. A security flaw was detected in flash and malicious code is already used, so they urge you to upgrade.

---

### Post by garvinrick4 on 2011-09-30
> **indiana_crook said:**
> I'm having an issue with Flash... My firefox and Chrome both tell me that I must upgrade flash player in order to view things on certain sites, like Youtube.  I have reinstalled the flash-installer several times and all the plugins that are available, but I still get the message when I go on Youtube that says I need to upgrade flash.  I have even tried the Flash-Aid add-on.  My other computers run on the same version of Ubuntu (10.04 LTS) and they have no problems...  Any ideas?
If all else fails repository's and flash-aid remove all remnants of flash and install from adobe. Or wait have you tried a ppa of flash first? 
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
Choose adobe flash your version and gives you instructions. This should work but odd flash aid did not do it. 
Did you install flash aid then restart firefox and look in upper right hand corner with red circle with f in the middle 
and then click on and pick one of three choices then run the script, it does it for you. I do believe you forgot to finish 
the install and run script. It has newest versions of flash in 32 and 64 bit I know for a fact. But you do what you find best for you.

---

### Post by indiana_crook on 2011-10-04
> **garvinrick4 said:**
> If all else fails repository's and flash-aid remove all remnants of flash and install from adobe. Or wait have you tried a ppa of flash first? 
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
Choose adobe flash your version and gives you instructions. This should work but odd flash aid did not do it. 
Did you install flash aid then restart firefox and look in upper right hand corner with red circle with f in the middle 
and then click on and pick one of three choices then run the script, it does it for you. I do believe you forgot to finish 
the install and run script. It has newest versions of flash in 32 and 64 bit I know for a fact. But you do what you find best for you.

I've done both of these things, but to no avail. Yes, I did have the flash aid installed and functioning properly.  I watched the terminal do it's thing as it removed the unnecessary files and installed the new ones. After all is said and done it still does not work. I tried the PPA but it didn't work either. It doesn't make sense... When adobe is installed, it tells me that it is out of date.  It is the only computer I have that is doing this.  Is anyone else having this issue?

---

### Post by garvinrick4 on 2011-10-04
I am going to give you a link I posted in already that has the commands to remove
anything flash then you can install the way you choose from repository's, adobe.com with flash-aid or ppa. I would say you have some remnant of flash hanging around somewhere. 
[http://ubuntuforums.org/showthread.php?t=1850582](http://ubuntuforums.org/showthread.php?t=1850582)
Look at post 8 and run the commands.

---

### Post by indiana_crook on 2011-10-05
> **garvinrick4 said:**
> I am going to give you a link I posted in already that has the commands to remove
anything flash then you can install the way you choose from repository's, adobe.com with flash-aid or ppa. I would say you have some remnant of flash hanging around somewhere. 
[http://ubuntuforums.org/showthread.php?t=1850582](http://ubuntuforums.org/showthread.php?t=1850582)
Look at post 8 and run the commands.

That did not do the trick, however it did help.  After performing all the commands and getting no results, I went into the /usr/lib/mozilla/plugins/ to see if the file was actually being placed there.  I found that I didn't have permission to view the folder.  I changed the folder's permissions via the terminal and Flash started working again.  How the permissions got changed is beyond me. Flash just stopped working one day. But all is working now. Funny how it is usually the simple things... Thank you all for your help!

---

### Post by garvinrick4 on 2011-10-06
> That did not do the trick, however it did help.  After performing all  the commands and getting no results, I went into the  /usr/lib/mozilla/plugins/ to see if the file was actually being placed  there.  I found that I didn't have permission to view the folder.  I  changed the folder's permissions via the terminal and Flash started  working again.  How the permissions got changed is beyond me. Flash just  stopped working one day. But all is working now. Funny how it is  usually the simple things... Thank you all for your help!
Right click on any flash playing video and see what version of flash you are using? Nothing
important just a question of what is installed, no big deal.

---

### Post by indiana_crook on 2011-10-09
> **garvinrick4 said:**
> Right click on any flash playing video and see what version of flash you are using? Nothing
important just a question of what is installed, no big deal.

It is now running 11,0,1,152.

---

### Post by garvinrick4 on 2011-10-09
> It is now running 11,0,1,152.
The only place you could have got that is from Adobe.com at that time, extracted
and copied the libflashplayer.so to correct directory. 
It is all moot now it works and you are working, enjoy your Ubuntu indiana_crook.
Take care.

---

