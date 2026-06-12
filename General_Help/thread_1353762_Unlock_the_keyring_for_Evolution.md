---
title: "Unlock the keyring for Evolution"
date: 2009-12-13
forum: General Help
---

### Post by Tickborn on 2009-12-13
Hi there,
Is there a way to automatically unlock the keyring for evolution without typing the password every time i reboot the computer?
Thanx in advance!

---

### Post by Tickborn on 2009-12-17
sigh,
*BUMP*

---

### Post by avtolle on 2009-12-17
> **Tickborn said:**
> Hi there,
Is there a way to automatically unlock the keyring for evolution without typing the password every time i reboot the computer?
Thanx in advance!
I presume you wish to do an automatic log in, thus the question. There may well be a way, but I do not know what it is. I believe it may be done using the Password and Encryption Keys app, found under Applications>Accessories>Password and Encryption on 9.10, but I've not tried it.

---

### Post by Tickborn on 2009-12-19
Thanx. I'll tryto have alook there. I will post back in case i find a solution  for it.

---

### Post by rdh61 on 2010-01-02
Same problem here. Can't find a solution either. Very annoying.

---

### Post by Muscovy on 2010-01-02
I'd like to know too, for Ubuntu One (presumably the same). My family skips the login screen, so Ubuntu One manually requests a password.

---

### Post by Groundswell on 2010-01-02
i'de like to know this too, one way i'm guessing it could be solved is to un-encrypt the password. i wouldn't mind that on my pc since i'm the only one who uses it. maybe we should be asking how to store evolutions passwords unencrypted?

---

### Post by rdh61 on 2010-01-04
Here's how I resolved this:

Applications > Accessories > Passwords and Encryption Keys.
Delete "Passwords: default" in the "Passwords" tab.
Reboot.
Open Evolution and hit Send/Receive.
You will be asked to put in your password for the mail account, then another box will ask you to enter another password for the keyring where the mail account password will be stored. Leave it blank and click OK.
You will then be warned that the mail account password will be stored unencrypted.
If you accept this, you may be open to security risk, but you will no longer be bugged by that annoying keyring window.

---

### Post by Groundswell on 2010-01-04
thnkya rdh , gold star for u!:KS

---

### Post by mcduck on 2010-01-04
> **rdh61 said:**
> Here's how I resolved this:

Applications > Accessories > Passwords and Encryption Keys.
Delete "Passwords: default" in the "Passwords" tab.
Reboot.
Open Evolution and hit Send/Receive.
You will be asked to put in your password for the mail account, then another box will ask you to enter another password for the keyring where the mail account password will be stored. Leave it blank and click OK.
You will then be warned that the mail account password will be stored unencrypted.
If you accept this, you may be open to security risk, but you will no longer be bugged by that annoying keyring window.

There's no reason to delete any keyrings. You can simply right-click it and select "Change Password" to change/remove the password. :D

---

### Post by tiagoscd on 2010-01-04
Go to directory **~/.gnome2/keyrings** and delete to trash the file **login.keyring**.

After delete, restart the computer.

---

### Post by mcduck on 2010-01-04
> **tiagoscd said:**
> Go to directory **~/.gnome2/keyrings** and delete to trash the file **login.keyring**.

After delete, restart the computer.

Like already mentioned in this thread, there's no need to destroy your current keyring, the password can be changed without loosing all your stored keys by using the GUI tool found in the Applications menu..

---

### Post by groening on 2010-01-06
is there a way to export my passwords?? Seahorse does not offer to export (neither save nor copy) my passwords - that feature is only usable for PGP keys...

I know the keyring is stored at .gnome2/keyrings/login.keyring but:

I have a new PC, and I am going to encrypt the home folder, so I would run in trouble trying to overwrite the login.keyring with the one from my other PC...

I am kind of stuck here, any ideas how to solve this?

The export function of seahorse is disabled for passwords (which in my opinion is the most stupid patch ever made, wtf...)
[https://bugzilla.gnome.org/show_bug.cgi?id=551477#c1](https://bugzilla.gnome.org/show_bug.cgi?id=551477#c1)

these guys surely never had >15wireless connections nor 70plus ftp-connection settings stored in their keyring...

what am I going to do? write them all down?
Seriously, isn't that rediculous to develop a keyring that cannot be fully exported?

---

### Post by jereece on 2010-02-13
MCDUCK - I did what you suggested "right-click it and select "Change Password" to change/remove the password" and I removed the password.  Ubuntu prompted me to be sure I wanted have no password for key rings?  I acknowledged that but now am wondering if this makes my computer more at risk from a security standpoint.  Can you or anyone comment on that aspect of doing this?

Thanks,
Jim

---

### Post by Marais on 2010-06-04
I posted this on an older thread and am posting here with hope there will be a solution:KS
On Linux Lucid this known bug where the password prompt shows up  everytime Evolution is launched is driving me NUTZ!

After the upgrade for Lucid Linux yesterday the problem has returned.

Before the upgrade a simple matter of disabling the gui in the startup  manager.
Now all is disabled but Evolution keeps prompting for passwords.
I'm set up as an automatically signed in user.

I deleted the files in /home/juser/.gnome2/keyrings

I also deleted the folder itself  /home/juser/.gnome2/keyrings

I also deleted the file in

/home/user/.gnome2_private

all to no avail!

I uninstalled and reinstalled ubuntu-desktop (to reinstall gnome-keyring.  I did the same for seahorse.

Any suggestions? Mr. Google has run out of ideas:sad::confused:

---

### Post by Boondoklife on 2010-06-04
> **jereece said:**
> MCDUCK - I did what you suggested "right-click it and select "Change Password" to change/remove the password" and I removed the password.  Ubuntu prompted me to be sure I wanted have no password for key rings?  I acknowledged that but now am wondering if this makes my computer more at risk from a security standpoint.  Can you or anyone comment on that aspect of doing this?

Thanks,
Jim

Well I do know one major downside, but this really has more to do with the auto-login feature. Since you are using that, else you would not need a blank default keyring, anyone can boot up your computer and have access to the passwords/secrets in the passwords application.

For me this is not a big deal as nothing of interest is installed on my laptop, I keep the goodies somewhere else. If you are in the habit of using the same password for lots of things and someone does happen to jot down your stored passwords, they could have free rain to your digital life. This is of course based on an assumption that you use the same passwords for other things, important things, but we all know better then to save those passwords on any computer don't we. :shock:

EDIT: As a side note if someone were to get access to computer through another account I believe it would be possible for them to get a copy of your /home/username/.gnome2/keyrings/login.keyring file which without a default password is stored in plain text. This means anyone could read it and get your login info for the stored user/pass combos.

---

### Post by Boondoklife on 2010-06-04
> **Marais said:**
> I posted this on an older thread and am posting here with hope there will be a solution:KS
On Linux Lucid this known bug where the password prompt shows up  everytime Evolution is launched is driving me NUTZ!

After the upgrade for Lucid Linux yesterday the problem has returned.

Before the upgrade a simple matter of disabling the gui in the startup  manager.
Now all is disabled but Evolution keeps prompting for passwords.
I'm set up as an automatically signed in user.

I deleted the files in /home/juser/.gnome2/keyrings

I also deleted the folder itself  /home/juser/.gnome2/keyrings

I also deleted the file in

/home/user/.gnome2_private

all to no avail!

I uninstalled and reinstalled ubuntu-desktop (to reinstall gnome-keyring.  I did the same for seahorse.

Any suggestions? Mr. Google has run out of ideas:sad::confused:

Is this asking for the default keyring password or your imap/pop password?

---

### Post by Marais on 2010-06-04
It's worse than you can imagine![-X
Evolution now asks all my passwords for my 4 email accounts =
gmail
yahoo
and two other POP servers:guitar:
Then the keyring which I disabled (or so I thought) in my startup applications and worked just fine and DANDY before the upgrade yesterday to my Linux Lucid 10.04 system.

Then the best for last, the keyring won't hold the damn passwords.
If I open seahorse from a terminal I get folders that according to the gui don't exist.
I can erase them manually by fishing for them in the .gnome2/keyrings folder, restart or whatever.

BUT
This thing "takes a lickin' but keeps on tickin".

I have so many filters I've established for Evolution plus my calendar and contact synch I don't want to start afresh after a year of setting these filters and whatever up with Thunderbird. I've resolved myself to wait for the next update and maybe someone will have fixed it. It is a know bug with Lucid and maybe since Karmic (one example here) =
[http://us.generation-nt.com/bug-528978-usr-bin-gnome-keyring-evolution-unable-connect-gnome-keyring-daemon-help-168547051.html](http://us.generation-nt.com/bug-528978-usr-bin-gnome-keyring-evolution-unable-connect-gnome-keyring-daemon-help-168547051.html)

---

### Post by Boondoklife on 2010-06-04
Sounds like you have hosed the keyring some how, why would you disable it? If you disable the keyring then where would you expect it to save the passwords, of course you are going to be prompted every time for every account. It would be like talking to a far gone alzheimer patient, or better yet 10 second Tom!

Does Evolution not backup all those settings with you do a backup? I never used the filters as I have the server do that for me and my calendar is online anyways.

---

### Post by Marais on 2010-06-04
But one of the GREAT mysteries in life is that since I installed Lucid I had this problem.
Then I found the solution to disable all keyrings at startup.
That worked fine and dandy for a few weeks.

Then after the update yesterday it all came back, and although according to my startup apps they are all disabled (and in fact) for all my other apps including the login screen they work fine, it's only Evolution.

I've found this bug listed at least 5 times and nobody has been able to address the issue (for the time being).

Most of the solutions are "Use Thunderbird".
I would if the migration was easy, but it seems that I'll lose all my filters and rules.
So I'll punch in four passwords each and everytime I fire up Evolution and once again to send mail...

ANNOYING:frown::oops::roll:

---

### Post by Marais on 2010-06-30
My problem in fact is I'm in France and therefore on the French Lucid Linux.:confused:
 The problem came from the fact that the French version made a default suitcase for the keyring with an accent=

/home/user/.gnome2/keyrings/par_[SIZE=5]défaut[/SIZE].keyring

This is a bug as we all know an accented letter is at least two if not more ASCII characters.):P

Solution weird as it seems was to create a fake account on Empathy instant messenger and now a month later the whole thing works with Evolution.

I learned this quickly but you Linux people need to remember DO NOT PUT ACCENTS INTO FILE NAMES
:lolflag:

---

