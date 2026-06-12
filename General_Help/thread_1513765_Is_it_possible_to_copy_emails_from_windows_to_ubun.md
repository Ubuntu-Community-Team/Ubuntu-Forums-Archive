---
title: "Is it possible to copy emails from windows to ubuntu"
date: 2010-06-20
forum: General Help
---

### Post by dazndom on 2010-06-20
im a newbie with ubuntu . My missus has a vius/trojan infected laptop running XP. i need to get 4 yrs worth of business/ training emails off it. Is it possible to transfer these emails from xp to ubuntu without sending them via internet. Can some one give me suggestions or howto  please

cheers
Daz

---

### Post by QIII on 2010-06-20
What email client is she currently using?

---

### Post by aysiu on 2010-06-20
Are these Outlook POP3 emails or Thunderbird POP3 emails?

Or are these IMAP emails?

If they're POP3, they are actually stored on the computer. If they're IMAP, you don't need to save them, since they're on a remote server somewhere anyway.

If they're POP3 Thunderbird, you can just copy the appropriate Thunderbird folder to Ubuntu. If they're POP3 Outlook, it can be a bit trickier...

---

### Post by Rubi1200 on 2010-06-20
I can't speak for older versions of Outlook, but in Outlook 2003 if you save/saved the emails as a .pst it is possible to import them into Evolution on Ubuntu.

---

### Post by dazndom on 2010-06-20
outlook is the email client, also is it possible to transfer all multimedia files to ubuntu and then virus scan them in ubuntu, please excuse my stupid questions, missus is on my back, i said tough you will have to scrub it and lose lot, but that made my life miserable!!!!!

---

### Post by =CrAzYG33K= on 2010-06-20
If its Mozilla Thunderbird, there's an excellent *freeware* backup tool called MozBackup to backup the e-mails.

---

### Post by QIII on 2010-06-20
Like I say, dazndom...

I wear the pants in my family.  The ones my wife buys.

The answer to the question about the files is "most likely".  I'd say yes, but who knows.

As for Outlook, aysiu asked if you knew if they are POP3 or IMAP.  Do you know that?

---

### Post by Rubi1200 on 2010-06-20
> **dazndom said:**
> outlook is the email client, also is it possible to transfer all multimedia files to ubuntu and then virus scan them in ubuntu, please excuse my stupid questions, missus is on my back, i said tough you will have to scrub it and lose lot, but that made my life miserable!!!!!

Ok, first of all you need to save the emails in Outlook:

[http://it.emory.edu/showdoc.cfm?docid=3770](http://it.emory.edu/showdoc.cfm?docid=3770)

Once all the emails are saved get a USB stick or external HDD where you can save the .pst files.

Importing them into Evolution on Ubuntu is the next step:

Plug the USB/external HDD in and then Go to File > Import and follow the on-screen wizard which will guide you through the process.

This might also be relevant:

[http://www.sitedeveloper.ws/tutorials/outlook.htm](http://www.sitedeveloper.ws/tutorials/outlook.htm)

But, we do need to know if this is POP3 please.
[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")

---

### Post by QIII on 2010-06-20
> Note: The following instructions assume that you are using Microsoft  Outlook 2000 and above and it is configured to use IMAP Email access and  the client is using the default display settings.

Let's not get ahead of ourselves here.

Give the OP the chance to let us know if he is using POP3 or IMAP.

---

### Post by Rubi1200 on 2010-06-20
Aha, good point! I was not looking at that. But, the method to save the emails is the same.

This might help regarding the media files and scanning for viruses:

[http://www.howtodothings.com/computers-internet/how-to-check-for-viruses-on-ubuntu](http://www.howtodothings.com/computers-internet/how-to-check-for-viruses-on-ubuntu)

---

### Post by dazndom on 2010-06-20
sorry guys, email is pop3

shoppings done, now i must don the apron and cook dinner !!! hehehehehaaaaa ouch !!!
:lolflag:

---

### Post by QIII on 2010-06-20
Here's what I am *thinking *may work.  *Thinking, *mind you.

My wife runs Windows and uses Thunderbird.  I believe that when we set her up, she was given the opportunity to import from Outlook.  She hadn't used it, so there was no point.

I think the mechanism is there, but I'm not sure how it works out with the POP3/IMAP issue.

I need to do a little more looking, so don't launch into this right away.

So, just [I]thinking:

[/I]Since POP3 is kept locally, find out where Outlook stores the data.  I have no clue.  Back it all up.
Install Thunderbird on her machine.  If given the opportunity to import from Outlook, do so.  That will create a nice little package of everything you need in the profile.  We can figure out where Windows hides it and make a copy of it to removable media.

On the Ubuntu machine, use something like ClamAV to scan the media for Windows viruses.  They are not likely to be a problem for Linux, but you might want to clean them up before you mail them on to your Windows friends to infect their machines.

When your multimedia, personal and other important files are *cleaned up* and kept aside on some physical media, scan the bejesus out of the Windows machine.  Do your worst.

Put all the *clean *files back.

Figure out where Windows stores the Thunderbird profile.  Replace the contents of the original profile with the contents of the newly scanned files.

Unfortunately, I haven't the foggiest notion how to get Thunderbird stuff back into Outlook.

---

### Post by VastOne on 2010-06-20
> **dazndom said:**
> sorry guys, email is pop3

shoppings done, now i must don the apron and cook dinner !!! hehehehehaaaaa ouch !!!
:lolflag:

POP3 suggests the email is sitting on a server somewhere unless she has told that server (via a setting in Outlook) not to store messages on the server.

If they are still on the server you can get them that way.  If they are all on the laptop within Outlook you may have to go back into Windows and save that pst if it has not been done lately or set to save to pst by default.

Someone above pointed out a site for instructions on that.  As for your other question, yes you can boot via LiveCD and get any files and clean them even during that Live session.

---

### Post by QIII on 2010-06-20
> **VastOne said:**
> POP3 suggests the email is sitting on a server somewhere unless she has told that server (via a setting in Outlook) not to store messages on the server.

If we're lucky.  Some providers just don't do it at all with POP3 accounts.  With them, it's not an option.  (They generally do store it somewhere, off-line and compressed, to comply with civil and criminal warrants and things like that.)

If it were IMAP, this would be substantially more trivial all around.

---

### Post by HermanAB on 2010-06-20
OK, there are two methods to transfer email from Outlook to something else:
1. Copy the PST  file and import it into Thunderbird or Evolution.  This should work, but in practice, you may find that some mail goes missing.
2. Bounce the mail through an IMAP server.  Open a Gmail account.  Configure Outlook to use Gmail with IMAP. Click drag drop the mail with Outlook from the one account to the other.  Your mail will now reside on Gmail.  Then read the mail with Thunderbird, configured to use POP3. Your mail will now be on your local machine.

If you cannot open an account on Gmail, install Citadel, from citadel.org and do the same trick as explained above.  This works, because you use Outlook to transfer its mail from the Microsoft mess to the standard IMAP and Outlook can read its own junk quite well.  Once the mail is in a standard format again, any mail client can read it.

---

### Post by dazndom on 2010-06-20
thanks everyone, saved  the files in outlook and imported to evolution,
AFTER some gentle persuasion missus is now a UBUNTU convert, its the office software that has stopped her, she dont wannna learn how to work with OO coz at work they use
ms o 2007 but finally admits ms aint woth the stress

HOORAY   it is done):P

---

