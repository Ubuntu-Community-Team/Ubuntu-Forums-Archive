---
title: "How to delete Evolution Mail"
date: 2010-09-09
forum: General Help
---

### Post by DanTheBib on 2010-09-09
Hey guys, 

Basically I messed up setting up Evolution with my Hotmail account, and I want to start again...however I can't do that. 

I have uninstalled it from the software centre, but when I reinstalled it, Evolution has remembered all my settings >_< 

Can anyone help it forget them xD

Thanks,

Dan

---

### Post by oldos2er on 2010-09-09
You need to use Synaptic Package Manager and choose 'Completely remove', or in terminal run **sudo aptitude purge evolution** to remove config settings in addition to the program itself.

---

### Post by DanTheBib on 2010-09-09
I did that through the terminal, and when reinstalled it has still got my settings :S

---

### Post by Merovius on 2010-09-09
Do you really need to uninstall it? Can't you just remove (or just uncheck)the Hotmail account from accounts and start over? I have several accounts unchecked and ignored with no ill effect. I messed up setting up email accounts via pop and imap and just unchecked them and left them.

---

### Post by DanTheBib on 2010-09-09
That would be fine, if you could just tell me how to do that I'd appreciate it :)

---

### Post by andrewthomas on 2010-09-09
you could also remove the .evolution folder in your home directory

---

### Post by Merovius on 2010-09-09
In evolution, Edit, Preferences.

Then under Mail Accounts just uncheck the box next to your Hotmail account. Or, highlight and click on "Delete" on the right.

Then start over.

---

### Post by DanTheBib on 2010-09-09
[This is all I have](http://i59.photobucket.com/albums/g316/Goku2212/Evolution.png)

I don't have a file option, I only have what you see. The "File" option you see at the top is on my taskbar and not to do with Evolution.

---

### Post by Merovius on 2010-09-09
Wow. I wouldn't even recognize that as Evolution. Your theme seems to have eliminated your tool bar at the top. Not sure how to get around that at the moment.

---

### Post by DanTheBib on 2010-09-09
Even prior to my theme it didn't have a toolbar across the top.

---

### Post by Merovius on 2010-09-09
Mine looks like this. If it works.. What version is yours ? 

[http://cid-8e09383c4ac6f893.office.live.com/self.aspx/Ubuntu/Screenshot-Drafts%20%5E50%20drafts%5E6%20-%20Evolution-1.png](http://cid-8e09383c4ac6f893.office.live.com/self.aspx/Ubuntu/Screenshot-Drafts%20%5E50%20drafts%5E6%20-%20Evolution-1.png)

---

### Post by DanTheBib on 2010-09-09
Found it! It was under preferences in Edit.

Turns out the top menu changes depending on program run. I've only just got this theme, so didn't know that.

Thanks for all the help, I've deleted my account like that and will redo it now :)

---

### Post by Merovius on 2010-09-09
Thats the same version as mine. I suspect that the edit in your top panel works with whatever application you have open, like on a Mac. (Thats why it says Evolution before the menu) With Evolution open click on edit and see if you have a preferences at the bottom of the list. If so thats where you need to be. Try that first.

---

### Post by Merovius on 2010-09-09
Bingo! Congrats.:)

---

### Post by mdwy62 on 2010-09-09
Here is a related Evolution mail deletion question. I have a pop account (yahoo) and I checked "Leave Mail on Server" and "Delete Mail After 10 days" under Receiving Options, thinking that this would
(a) leave my mail on the server and 
(b) delete the local copy of mail after 10 days.

Apparently this does the exact opposite, not deleting local mail, but deleting mail on the server after 10 days. Surprise! 4 years of emails gone!

My question is, is there a way to get Evolution to do what I intended? That is treat the web as my email repository and only have a small window into the past in my Evolution client?

Thanks.

-Mark D.

---

### Post by Merovius on 2010-09-09
Not sure about that. I handle my stuff locally. I don't have leave on server checked. I know in G-mail under the Forwarding and POP/Imap settings you can set it to archive mail after POP download. That would do it I would think. I forward all my mail to G-mail and then have Evolution pull it down from there. If you did this and set it to archive I would think all email would be archived. Mine is set to delete after download. I save what I want locally.

---

### Post by NearlyALaugh on 2010-09-10
[Edited]

---

### Post by dcstar on 2010-09-10
> **andrewthomas said:**
> you could also remove the .evolution folder in your home directory

You also may need to delete the account credentials in the !.gconf/apps/evolution folder, as well as the Keyring entries for the account login.

---

### Post by dcstar on 2010-09-10
> **mdwy62 said:**
> Here is a related Evolution mail deletion question..........


No, do not hijack threads with totally unrelated issues, start a new thread.

---

