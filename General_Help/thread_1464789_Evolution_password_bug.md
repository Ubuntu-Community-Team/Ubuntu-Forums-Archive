---
title: "Evolution password bug"
date: 2010-04-28
forum: General Help
---

### Post by J V on 2010-04-28
This has been a problem ever since I started using evolution, but not being fixed in Lucid is just a pita...

Every 2 to 7 days, evolution will forget my passwords (WLM)

When it does this, it pops open a window asking for my password, but when I enter it, it just pops the window open again, as if its incorrect.

The only way to get it working is to hit cancel, and manually click the "Refresh" button: Then the popup will work.

Does anyone else get this? Is there a fix?

---

### Post by munky99999 on 2010-04-28
Old bug it seems.

[https://bugzilla.gnome.org/show_bug.cgi?id=571504](https://bugzilla.gnome.org/show_bug.cgi?id=571504)

Still hasnt been fixed if I understand the situation.

I believe the current bug fix is to change your password. It'll reprompt and fix the situation until the login fails again.Then you'll be back in the same situation.

---

### Post by J V on 2010-04-28
"Committed to gnome-2-24" - Then why is it still here in gnome-2-30?

---

### Post by J V on 2010-04-30
bump?

---

### Post by dcstar on 2010-04-30
> **J V said:**
> This has been a problem ever since I started using evolution, but not being fixed in Lucid is just a pita...

Every 2 to 7 days, evolution will forget my passwords (WLM)

When it does this, it pops open a window asking for my password, but when I enter it, it just pops the window open again, as if its incorrect.
........

What "password"?, an e-mail account password, an Ubuntu system password? please be clear.

I use Evolution with multiple e-mail accounts, occasionally one particular account will prompt for the password (even though it is correct), this is not Evolution's fault, it is the fault of the POP server at that particular e-mail account and it usually fixes itself in a minute or two.

---

### Post by J V on 2010-04-30
The problem is that even when I input the correct password (Yes email password...) it just requests it again... Unless I hit cancel and refresh it won't accept my input.

---

### Post by J V on 2010-05-04
Anyone know why this is still here...?

---

### Post by dcstar on 2010-05-05
> **J V said:**
> The problem is that even when I input the correct password (Yes email password...) it just requests it again... Unless I hit cancel and refresh it won't accept my input.

Applications-Accessories-Passwords etc. and delete any relevant entries.

---

### Post by Wim Sturkenboom on 2010-05-05
Not of help, but I never had this happen since I installed Dapper. Upgraded to Hardy and it's still fine.

I use Evolution with 2 accounts; those accounts have the same pop and smtp servers but usernames and passwords are different.

I have another account that I access as a different computer user and it also has not happened on that account since I started using it.

---

### Post by J V on 2010-05-06
@dcstar: All that did was reproduce the error... Its still there...

---

### Post by J V on 2010-05-08
bumpity...

---

### Post by dcstar on 2010-05-08
> **J V said:**
> @dcstar: All that did was reproduce the error... Its still there...

Shut down Evolution and delete the ~/.gnome2_private/Evolution file.

---

### Post by J V on 2010-05-09
Theres nothing in ~/.gnome2_private... and theres no evolution folder in ~/.gnome2 either...

---

### Post by Shellboy on 2010-10-19
This bug really sucks! 
I am thinking to replace evolution soon, because the developers just ignore this bug.

And btw. @ dcstar: 
How can you claim its not evolutions fault? 
Other email clients dont behave in such a stupid way, so there has to be something wrong with the way evolution handles pop-accounts.

As long as there are little bugs like this, it will be hard to get people to use open source. 
Almost everybody i convinced to use Ubuntu is confused/annoyed about this bug.  

Cheers,Frank

---

### Post by dcstar on 2010-10-20
> **Shellboy said:**
> 
..........
And btw. @ dcstar: 
How can you claim its not evolutions fault? 
Other email clients dont behave in such a stupid way, so there has to be something wrong with the way evolution handles pop-accounts.
..........

Because - as I clearly wrote - the problem was in **the remote server** and when **the remote server** started working correctly the problem went away.

---

### Post by Hedley on 2010-11-27
> **dcstar said:**
> Because - as I clearly wrote - the problem was in **the remote server** and when **the remote server** started working correctly the problem went away.

I don't agree, if you're talking about the remote mailservers. I use several different mailservers (my own pop servers, as well as Gmail and Yahoo pop servers), and every once in a while Evolution just inexplicably "forgets" the passwords for **all** of them, and I have the re-enter each password. It seems rather unlikely to me that the exact same problem is occurring simultaneously on the Google, Yahoo, and my own hosted mailservers.

---

### Post by simonjpo on 2011-02-26
Hedley, I concur. People who allow subjectivism to prevent identification and solution of real problems contribute nothing and drag the whole open source cause down.

I have the same problem with Evolution.

It forgets the password when it fails to logon to any mail service.
Whoever wrote the programme seems to have assumed that only an incorrect password can cause a verification failure.

This is faulty business logic. Services fail intermittently for any number of reasons. The programmer probably thought they were being helpful in the case of a user changing a password at the server end, but to empty out the old password on the assumption that it was at fault is incredible.
Very, very naive.
Somebody at Novell should have a word with them.

---

### Post by xzero1 on 2011-11-11
As of this post the problem is still not fixed in lucid. I just changed to Thunderbird. :(

---

### Post by ChrisNZ on 2012-08-29
Same problem and just posted. Running Mint 12, Evo 3.2.2 still not fixed?

Someone please close this.

---

### Post by Toz on 2012-08-29
[ATTACH]223396[/ATTACH]
Oh no you don't. 
Closed.

---

