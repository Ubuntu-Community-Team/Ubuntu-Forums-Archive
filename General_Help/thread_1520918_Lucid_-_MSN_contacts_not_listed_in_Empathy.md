---
title: "Lucid - MSN contacts not listed in Empathy"
date: 2010-06-30
forum: General Help
---

### Post by Jimmy9pints on 2010-06-30
Hi, I have searched around for similar threads on here and Google but was surprised to find none. 

The title says it all really. I run Empathy, have used it for a while with both Google-chat and MSN protocols. I've been using it for a few months now and suddenly my MSN contacts have all disappeared. 

People are able to contact me via MSN, and when their message window pops up I am able to respond. It says they are offline however.

I have tried listing all offline contacts but they still do not appear in the list. 

I have tried uninstalling (including config files) and reinstalling but this wasn't successful either. When I reinstalled it still had details of my accounts so clearly the cofig files were not removed properly. 

Please advise!

Thanks in advance.

---

### Post by Jimmy9pints on 2010-07-02
Anybody any idea on this?

I haven't changed any of the settings and my MSN account is still enabled.

---

### Post by etteling on 2010-07-10
I am having the same problem on Kubuntu with Emesene, Pidgin and Kontact. The same problem also occurs if I log into a Gnome session. Did you find a solution?

---

### Post by Jimmy9pints on 2010-07-11
Yes, I found a (very poor) solution. 

After putting up with this for a while, I changed over to Pidgin from Empathy. However, I found that the situation was no better!

I then logged into MSN web messenger to find that there was exactly the same situation!!! None of my contacts were listed online. 

It turns out, all of my contacts have been deleted. 

The only solution then in that case was to sign up for a new account with MSN (after maybe 8 years of using that account). 

I still keep the old account open, and have changed the name to "My MSN Account is broken. Please add my new address ***@msn.com". Of course, most people probably think this is a spam message or trick, so only a few have done it.

The result is that I have lost 90% of my contacts.

---

### Post by avdongen on 2010-08-11
I have the same problem with some of my contacts. They don't see me online nor do i see them. I did some testing and this is my conclusion so far:

MSN Live Messenger
No problem, "problem contacts" see me and i see them

Emesene 1.6.1 + Emesene dev PPA
Problem occurs, they don't see me and i don't see them..

Pidgin 2.6.6
I can see them but they don't see me..

I checked and in Emesene the user are not even in my contact list. Thats why i did a debug in Emesene and guess what.. the XML the MSN servers gives me DO NOT contain the users i am experiencing problems with.

Not to jump to conclusions to quickly but it seems like MSN is not parsing the correct contact list because i am using a different client.. seeing the there Windows client is not experiencing problems..

Could someone please confirm my findings.

---

### Post by The_Eddster on 2010-10-04
None of my contacts show up as 'online'. At first it appears that I have no contacts, but then I click on view offline contacts and they're all there, all offline. Clearly this should not be the case as I have a lot of contacts who are online pretty much 24/7

Can anyone help me with this? 


Linux Mint 9 (Ubuntu 10.04)
Empathy 2.30.2

---

### Post by hattonn on 2010-11-01
I'm experiencing the same problem, though my msn contacts appear fine in pidgen

---

### Post by yakinikku on 2010-11-12
only one of mine is showing up.  oddly enough, my girlfriends computer is on right next to mine and she is not showing up in empathy.  running 10.10

---

### Post by roobinatube on 2011-01-22
Did anyone find a solution to this? Im struggling to get this to work...

Roo

---

### Post by hislordship on 2011-02-02
Ubuntu does not deliver updates for Pidgin automatically - you have to tell it to do so by adding the pidgin personal package archive to your software sources: 

terminal:
sudo add-apt-repository ppa:pidgin-developers/ppa (press enter, enter your password)

then sudo apt get-update (enter)

instead of the smiley enter : and p of course. sorry : and p without a space come out as smiley automatically here

---

### Post by H3110 on 2012-02-01
I'm sorry for the bump. But despite still having this problem myself, i've discovered the contacts are simply not correctly listed, this could be because i'm connected in 3 locations.

anyhow, with MSN... 

1. goto [http://www.live.com](http://www.live.com).
2. Sign-in.
3. start you conversations; then your Empathy client will pop-up the conversation.

---

### Post by green0eggs on 2012-02-04
For what it's worth I seem to be having this problem too. MSN contacts list is a bit buggered. I'm not smart enough to solve the problem though.

---

