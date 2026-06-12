---
title: "Evolution's &quot;Remember Password&quot; is driving me nuts!!"
date: 2010-07-04
forum: General Help
---

### Post by whein on 2010-07-04
Sorry if this is easily fixed but I can't find an answer.  I have Evolution set up to monitor three GMAIL and five AOL email accounts.  On all of them I have the servers set up correctly and all the right settings to check email 65-75% of the time.  But for some reason, even though I have the "Remember this password" box checked for all of my AOL accounts, it will ask me over and over and over and over and over and over again for the passwords for all of my AOL accounts.  The GMAIL accounts seem to work flawlessly.

I know that I have the correct passwords because I am cutting and pasting from a text file with known working passwords.  And sometimes it will accept the passwords and everything is happy.  But other times (like tonight) I can put in the passwords six or seven times for each account and it still gets all pissy.  I can close and reopen evolution and re-enter the passwords and it still sits there in a seemingly endless loop of asking for the password.

Is there anyway to convince it to remember my passwords and NOT ask me for them again?  I don't care if it writes an entry to a log file saying that logging into the server failed.  I don't care if it flashes a little light or plays an annoying chime or something everytime it fails.  But I swear I am an inch away from putting my fist through my monitor if it keeps popping up the g.d. dialog asking for my passwords every six seconds!!!  This has been going on for months now and I can't believe I'm the only one this has happened to.

I would switch back to Thunderbird in a heartbeat if the mailbox formats were compatible...

Help?

-Will

---

### Post by lorenzosu on 2010-07-05
Hi,

I'm also suffering this annoying bug which looks like: [https://bugs.launchpad.net/evolution/+bug/255768](https://bugs.launchpad.net/evolution/+bug/255768)

I maybe found a workaround, although I'm using evolution with an Exchange account.
EDIT: This is using Evolution version 2.28.3 on Ubuntu Lucid.
It's pretty twisted but it eventually worked for me so I'll list all the passages:

- Close (Quit, not minimize etc.) Evolution
- Open Seahorse (i.e. the passwords manager usually located in "Accessories > Passwords and encryption keys")
- Locate the entry for the Evolutions password (in my case being an exchange account it said something like "exchange://..." I think this may vary a lot depending on the account. Anyway you can find out it is the password stored for Evolution because it shows in the details tab).
- Delete the password entry used by evolution
- Close Seahorse
- Open Evolution
- Input the password and *uncheck* the Remember password check-box
- After evolution loads quit it again
- Re-Open Evolution
- This time when you input the password *check* the Remember password check-box

After all this now Evolution seems to remember my exchange password.

Bests,
Lorenzo

---

### Post by NikoC on 2010-08-17
> **lorenzosu said:**
> Hi,

I'm also suffering this annoying bug which looks like: [https://bugs.launchpad.net/evolution/+bug/255768](https://bugs.launchpad.net/evolution/+bug/255768)

I maybe found a workaround, although I'm using evolution with an Exchange account.
EDIT: This is using Evolution version 2.28.3 on Ubuntu Lucid.
It's pretty twisted but it eventually worked for me so I'll list all the passages:

- Close (Quit, not minimize etc.) Evolution
- Open Seahorse (i.e. the passwords manager usually located in "Accessories > Passwords and encryption keys")
- Locate the entry for the Evolutions password (in my case being an exchange account it said something like "exchange://..." I think this may vary a lot depending on the account. Anyway you can find out it is the password stored for Evolution because it shows in the details tab).
- Delete the password entry used by evolution
- Close Seahorse
- Open Evolution
- Input the password and *uncheck* the Remember password check-box
- After evolution loads quit it again
- Re-Open Evolution
- This time when you input the password *check* the Remember password check-box

After all this now Evolution seems to remember my exchange password.

Bests,
Lorenzo

Good workaround! Worked for me on Ubuntu 10.04 and Evolution 2.28.3.

---

### Post by vimaljc on 2010-12-07
> **lorenzosu said:**
> Hi,

I'm also suffering this annoying bug which looks like: [https://bugs.launchpad.net/evolution/+bug/255768](https://bugs.launchpad.net/evolution/+bug/255768)

I maybe found a workaround, although I'm using evolution with an Exchange account.
EDIT: This is using Evolution version 2.28.3 on Ubuntu Lucid.
It's pretty twisted but it eventually worked for me so I'll list all the passages:

- Close (Quit, not minimize etc.) Evolution
- Open Seahorse (i.e. the passwords manager usually located in "Accessories > Passwords and encryption keys")
- Locate the entry for the Evolutions password (in my case being an exchange account it said something like "exchange://..." I think this may vary a lot depending on the account. Anyway you can find out it is the password stored for Evolution because it shows in the details tab).
- Delete the password entry used by evolution
- Close Seahorse
- Open Evolution
- Input the password and *uncheck* the Remember password check-box
- After evolution loads quit it again
- Re-Open Evolution
- This time when you input the password *check* the Remember password check-box

After all this now Evolution seems to remember my exchange password.

Bests,
Lorenzo



Good, works for me on 10.04 with Evol 2.28.3. I don't have any idea why.

---

