---
title: "Evolution and SqLite"
date: 2012-05-07
forum: General Help
---

### Post by kuifje09 on 2012-05-07
Can someone explain why the new version of evolution stores its ( MY ) mail is a SqLite database.
I do not like that, and would like to have evolution without a databas again.
Any problem with SqLite causes the mail to become unreadable. If evloution dies and the mailfolders where as before, I can read them always.
This is a very wrong move if I may say.
Is thunderbird using plain mail-boxes? or any other mail client?

( Not to say anything about the microsoft Sh.t way of handling mail, than evolution is still holy )

Yes I am very sad and angry. ( I know I should post this also in the evolution forum if it is there ... )

---

### Post by The Cog on 2012-05-07
sqlite is widely respected, and widely used. I think it is likely to be more reliable than a raft of text files because of the effort sqlite puts into ensuring database integrity. I know that firefox uses sqlite, and would be surprised if thunderbird used anything else.

I suggest you install the sqlite-manager plugin for firefox and use that to look at the database files. It's the best sqlite gui I have found.

---

### Post by kuifje09 on 2012-05-08
Thanks for the response, I will have a look at the FF-Plugin.

I agree evolution is one of the best mailclients. I use it for years, after trying several. 
Only thing I do not like, it is now relying on SqLite.
But I think I will keep using it... 

If contacts etc where kept in the database I would have no problem, but without export to .mbox I cannot read the mails outside evolution. Thats my point.

---

### Post by kuifje09 on 2012-05-11
Okay I started downloading and installing the sqlite manager.
Thats great. But I am still more angry and I don't trust firefox nomore.
Previous I could clear all content, read most of the cache.
Now I say clear it all, and guess what, in the database I think everything or almost..
I still there. Even for example, the history in firefox says, there is nothing... ITS IN THE DATABASE !

So I think obfuscation is a good thing against intruders, but obfuscation, from my programs, against me? Thats very very very bad.

And at last, I cant find howto read my mail from sqlite. Thats why this started.

Does someone going to kill me if I now suspect some microsoft developers are taking over the linux scene ?

( They are stealing and buying all they can get theire hands on ... do they ?)

---

### Post by kuifje09 on 2012-05-13
> **The Cog said:**
> sqlite is widely respected, and widely used. I think it is likely to be more reliable than a raft of text files because of the effort sqlite puts into ensuring database integrity. I know that firefox uses sqlite, and would be surprised if thunderbird used anything else.

I suggest you install the sqlite-manager plugin for firefox and use that to look at the database files. It's the best sqlite gui I have found.

This SqLite plugin is of no help to me. How do you use it. My evolution is version 2.32.2

---

### Post by kuifje09 on 2012-05-13
Did some research with strace, and was supprised evolution has moved some data to .local/share/..... and so on.

Looking in the files, I think they are not SqLite files, but just some data, Berkely database files and some PAS ? files ( some summary files )

Looking in the trace file saved from strace scares me a lot. !

How Can I go back to some just a mail tool like evolution was some years back ?

---

