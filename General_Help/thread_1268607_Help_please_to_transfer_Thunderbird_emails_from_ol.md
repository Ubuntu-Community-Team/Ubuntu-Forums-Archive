---
title: "Help please to transfer Thunderbird emails from old disk to new one."
date: 2009-09-17
forum: General Help
---

### Post by greenewbie on 2009-09-17
I want to move all my email messages, attachments, folders etc from my old hard disk to my new one: is that possible for a non-techie? I've looked at the **Thunderbird help notes**, they refer to a** profile folde**r (which I've managed to find on my file browser) but I suspect that has nothing to do with my actual messages etc. I'm confused about the whole thing. My old disk uses [COLOR=Red]Ubuntu 8.10 [/COLOR]but my new one has gone back to [COLOR=Red]8.04[/COLOR] (due to an issue with an accessory), does that complicate things in any way?
Many thanks for any help on this and I'd be particularly grateful for replies taking into account my complete lack of technical know-how! :confused:

---

### Post by wilee-nilee on 2009-09-17
Thunderbird is getting the email from a external email, just send them back to that and when you install thunderbird on your other HD get them back. I don't know if this is the most effective way not knowing how many you have top save.

---

### Post by greenewbie on 2009-09-17
I have hundreds of emails stored into Thunderbird accounts that I'd like to transfer to my new hard disk.  Is there a way to send them **“en bloc” **(even sending emails en bloc per individual folder)? From what I can see, you can only forward or save to my hard disk, **one** email at a time; if I did that it would probably take me a week!  So I'm still hoping that somebody knows a shortcut solution.......:confused:

---

### Post by StuartN on 2009-09-17
> **greenewbie said:**
> I have hundreds of emails stored into Thunderbird accounts that I'd like to transfer to my new hard disk.

Look in ~/.mozilla-thunderbird for the profile directory. If you did not set up the location yourself then it will be ~/.mozilla-thunderbird/<some_random_string>.default/Mail/Local Folders. Each file with no extension is a mail folder, e.g. "inbox". Ignore the .msf index files and any .dat or .html configuration files. Simply copy these files with no extension into your new profile directory structure, being careful not to overwrite anything important. Just note:

1) You require a folder called folder_name.sbd for any mail folder that has a subdirectory, AND a mail file with the same name (even if it has zero bytes) for Thunderbird to see subfolders.

2) When you copy a mail file without its .msf index, all deleted mail will reappear, unless you compact the folder first.

---

### Post by scouser73 on 2009-09-17
To move your Thunderbird profile which includes all the emails and attachments, you will need to back it up.

This can be done either on CD, or stored on other external media.

**1** - Back up **~/.mozilla-thunderbird** onto CD/DVD or other media.

**2** - Once you've got Ubuntu set up on your new hard drive, place the CD/DVD of your saved Thunderbird profile in the CD/DVD drive or other media into the pc.

**3** - Install Thunderbird via the Synaptic Package Manager, start it then close it immediately this will make a new folder and inside will be a new profile.  Delete the new profile and then copy & paste your existing profile into that folder.

**4** - With your saved profile in the new folder, go ahead and start Thunderbird, you will now see all your email addresses, emails and add-ons just as if it had always been there.

---

### Post by etnlIcarus on 2009-09-17
For a, "non-techie", I fear language like, "Back up ~/.mozilla-thunderbird", isn't going to be very useful.

[i]In your home folder, on the old hard drive, there will be a folder called ".mozilla-thunderbird". If you can't find it, you need to go to the menubar and find View>Show Hidden Files.

Copy that folder over to your new home folder on the new hard drive. The next time you start up thunderbird (make sure you don't do this while thunderbird is running), all your stuff should be as you left it.

For reference sake, the thunderbird folder should be found at /home/your username/.mozilla-thunderbird, when you open up the old hard drive.[/i]

---

### Post by greenewbie on 2009-09-20
:) MANY THANKS for your replies, you have been very helpful.  And well done [COLOR=Blue]**ETNLICARUS**[/COLOR] for pointing out that I have to click “Show Hidden Files” to find the above folder! :lolflag:

 I've now (apparently) copied the ***".mozilla-thunderbird"***folder to a memory stick.  Before I copy that to my new hard disk, I'd like to find out more about a discrepancy which is worrying me.  In the ***".mozilla-thunderbird" ***folder on my hard drive, there is an entry entitled [COLOR=#c90016]“lock”[/COLOR] :confused: (NO extension name after it unlike the others .ini; .rdf; .db etc), its size is 15 bytes and type is [COLOR=#c90016]“link (broken)”[/COLOR].  The “date modified” entry is “Sat 19 Sept” which I guess is the time when I copied the folder to the memory stick.  [COLOR=#c90016]My concern is that this entry doesn't appear in the memory stick copy [/COLOR](so for that reason it has 27 items in the subfolder, compared to 28 on the hard drive).  This entry's **icon** (ie appearing before the entry name) looks totally different from those of the other 27 items in the folder: instead of  a rectangle (with some kind of inscription in it), it doesn't have a rectangle at all, it has an icon of a padlock on an orange circular background, in turn superimposed on part of a blue-coloured diamond.

When I try to open this entry, a dialog box pops up saying “***the link 'lock' is broken. Move it to Trash******? This link can not be used because its target*** [series of numbers] ***doesn't exist***”.  
It briefly gives me the option to move it to Trash (which I haven't done because I don't know what it is) before a second dialog box pops up saying “***Opening Lock***” (with a picture of a light bulb on it),,,,,,,,,,,but then it blocks, it doesn't open anything.


 Do you think this is of any importance?  I'd just like to mention that I have reason to believe spammers have somehow managed to hack into my email system in the past. I'm worried that the “lock” discrepancy above is connected to compromising my system in some way.  I haven't been using anti-virus software or extra firewalls  beyond Ubuntu's built-in one (I gather that it's not imperative unlike when I used to use Windows), so can you guys give me any advice on that please?  I'd just like to reiterate that my technical know-how is practically non-existent (as you can see from the first sentence in this posting!)

---

### Post by etnlIcarus on 2009-09-20
It probably isn't too important. If removing it causes any undesirable behaviour, you can always just go into your Trash and restore the file.

As for spam, all someone needs to spam you, is to have your email address. Even if your mail service provide automatic spam filtering, you're still going to get the occasional bit of spam.

The best defence is just to be careful who you give your email address to. If you find you need to give your email address to some site you're not sure about, it's always a good idea to have a secondary email address, to minimise the risk to your primary address.

---

### Post by oldfred on 2009-09-20
The lock file is so thunderbird knows if the system has already been started. It sometimes does not get deleted on an abnormal shutdown and has to be deleted to allow startup.
More info on the thunderbird site:
[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

and lots of info on profiles sharing, moving etc.
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by StuartN on 2009-09-20
> **oldfred said:**
> The lock file is so thunderbird knows if the system has already been started.

As a general principle, it is always wise to exit any application while backing it up. If an application is running then its files are in an unknown state, and individual files (e.g. a mailbox file and its index file) could be backed up at different stages of a transaction.

---

### Post by greenewbie on 2009-09-26
Thanks VERY much everybody for your help, I copied the folder over and......it worked! I'm asonished that ALL of my stuff is there, emails, pics, addresses, the lot! :)

---

### Post by etnlIcarus on 2009-09-26
You'll find that works with most applications. They either place a hidden folder in your home directory, or place a hdden folder inside *another* hidden folder (.config, .kde, .gconf*), in your home directory.

Similarly with Windows: Inside c:\Documents and Settings\your username\, there's a hidden folder called *Application Data*, which contains most of the settings for the applications you use.

---

