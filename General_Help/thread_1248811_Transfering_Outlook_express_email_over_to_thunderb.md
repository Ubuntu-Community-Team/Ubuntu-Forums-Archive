---
title: "Transfering Outlook express email over to thunderbird?"
date: 2009-08-24
forum: General Help
---

### Post by kawana on 2009-08-24
Hey, so my dad wants to switch to linux, but the only reason he hasn't yet, is he wants to know if he can switch his outlook express email, over to thunderbird? Say his email is [EMAIL="12345@shaw.ca"]12345@shaw.ca[/EMAIL], can he access that through thunderbird, once he's switched over to ubuntu?

---

### Post by HermanAB on 2009-08-24
Howdy,

Yes, Tbird can import Outlook Express data directly, but you may run into bugs with funny characters in the mail folders.  The only way to know how well it will convert is to try it and see.  Since Tbird is available for Windows, this is no problem at all.  Just install Tbird and try it.

The best way to transfer email is via an IMAP mail server.  The way to do that is to install Citadel ([www.citadel.org](www.citadel.org)) on a Linux machine, create a dummy account, subscribe from Windows Outlook and click drag drop your mail from the local store to the dummy account.  Then repeat it the other way from the dummy account on Citadel to Tbird on Linux.  By doing this, each mail client handles the mail natively and the result should be a perfect transfer.

---

### Post by apmcd47 on 2009-08-24
> **kawana said:**
> Hey, so my dad wants to switch to linux, but the only reason he hasn't yet, is he wants to know if he can switch his outlook express email, over to thunderbird? Say his email is [EMAIL="12345@shaw.ca"]12345@shaw.ca[/EMAIL], can he access that through thunderbird, once he's switched over to ubuntu?

He can change from outlook express to thunderbird easily. Just copy the settings over from one to the other. What is more difficult is how to import old mailboxes. OE uses a proprietary format.

Andrew

---

### Post by celthunder on 2009-08-24
If it's imap, all the mail is stored on the server anyway, he'll get all his emails and whatnot just as if he had always been using thunderbird, if it is pop3 then he will only recieve new emails from the mail server.  I'm sure there's a way to transfer the ones that he already has if it's in pop3 that someone came up with.

---

### Post by DeMus on 2009-08-24
> **kawana said:**
> Hey, so my dad wants to switch to linux, but the only reason he hasn't yet, is he wants to know if he can switch his outlook express email, over to thunderbird? Say his email is [EMAIL="12345@shaw.ca"]12345@shaw.ca[/EMAIL], can he access that through thunderbird, once he's switched over to ubuntu?

Have a look here:

[_Import form Outlook (Express) to Thunderbird_]("http://kb.mozillazine.org/Import_from_Outlook_Express")
Install T'bird in Windows and make the change, take the files with you to Linux and drop them in the T'bird folder.

---

### Post by ajgreeny on 2009-08-24
I think the easiest way is to install thunderbird on windows and  import all the mail etc etc, into that OS version; you are asked when you first start thunderbird, I think, if you want to import mail etc from OE, so choose yes.

Then you can simply copy across all the files in your windows thunderbird configuration, which in XP is in /Documents and Settings/User/Application Data/Thunderbird/Profiles/*9bxwbftc*.default, where the italic alphanumeric will be his own random set  These files need to go into the similarly named hidden folder in ~/.mozilla-thunderbird.  In fact you can simply copy across the *whole 9bxwbftc*.default folder if you prefer, but will then have to edit the profiles.ini file in ~/.mozilla-thunderbird folder and change the alphanumeric shown in that to match the profile you copied across.  If you just copy the contents of *9bxwbftc*.default, not the folder itself, you will not need to edit the profile.ini file.

Even though this may sound complicated, it really isn't, and when you, or he starts to carry it out, I think you will see that it's quite simple in the end.

EDIT:
Too slow again and I didn't see DeMus's post in time.

---

### Post by kawana on 2009-08-24
edit: Crap, i think im screwed. I copied just the program files/Mozilla Thunderbird folder and its contents, thinking that is what you ment. Now i see that i need that 'Documents and Settings/User/Application Data/Thunderbird/Profiles/*9bxwbftc*.default,'  thing.. i copied the wrong stuff.  Any thoughts on how i can fix this? Are there any files in the Mozilla Thunderbird folder that have the info needed?

---

### Post by fballem on 2009-08-24
> **kawana said:**
> edit: Crap, i think im screwed. I copied just the program files/Mozilla Thunderbird folder and its contents, thinking that is what you ment. Now i see that i need that 'Documents and Settings/User/Application Data/Thunderbird/Profiles/*9bxwbftc*.default,'  thing.. i copied the wrong stuff.  Any thoughts on how i can fix this? Are there any files in the Mozilla Thunderbird folder that have the info needed?

Depends what stage you are at. Do you have the original windows, or have you already replaced it with ubuntu? The other question is whether you have a backup of your Outlook files?

Let us know and we'll see if there are any options available for you.

---

### Post by mike555 on 2009-08-24
If he has a bunch of saved email in " .dbx " format he can change them (in Windows) to " .eml " using a little program called " undbx " from ...     [http://code.google.com/p/undbx/](http://code.google.com/p/undbx/)   . then they will open in Thunderbird ...

---

### Post by ajgreeny on 2009-08-25
If you only have the files from the windows **Program Files** folder (directory), then I'm afraid you don't have the emails etc etc, only the executables, which don't really help.  If you didn't have any backups or have not still got the windows install on disk, there is little that can be done.

---

### Post by ZungBang on 2009-08-27
> **mike555 said:**
> If he has a bunch of saved email in " .dbx " format he can change them (in Windows) to " .eml " using a little program called " undbx " from ...     [http://code.google.com/p/undbx/](http://code.google.com/p/undbx/)   . then they will open in Thunderbird ...

You don't need windows for this, just the dbx files - you should be able to compile and run undbx under Ubuntu, or run the windows executable using wine.

---

### Post by mike555 on 2009-08-27
The old OE emails are located in your "documents and settings" folder in Windows . if a person has that backed up then just look through it (they might be Hidden files)for something like "inbox.dbx" , copy that out and I found even a better free program to view them or convert them in Windows or on UBUNTU using wine ...... called .. "mailview" , from ;  [http://www.mitec.cz/mailview.html](http://www.mitec.cz/mailview.html)

---

