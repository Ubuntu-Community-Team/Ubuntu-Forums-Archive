---
title: "Some questions about safety."
date: 2012-03-11
forum: General Help
---

### Post by annnowik on 2012-03-11
Hi everyone.
I can't deny that I'm not good at Ubuntu yet and I don't know how most of advanced technical things work. Anyway, I chose Ubuntu (and generally Linux) because it seems to be more safe than other OS.
And I try to use it in a very safe way. But there is an one case which doesn't let me be calmed. I'm a student and every group of students of my school, like in my case, has a common mail box hosted on Gmail. From time to time I have to log in to it. The problem is the fact, that I don't know who and generally how many people have an access and use it. Moreover, I don't know what data the Gmail get from my browser/system and what data it's possible to get. So I'm thinking about a safe method - anonymously and leaving no traces.

Thats how I'm doing it:
-I installed Wine and then clean Firefox Portable through Wine.
-Everytime, I want to use our common Gmail, I open Firefox Portable which I use only for it and I log in using proxy.
-Then i log out and clean all history in FF portable.

As I said above, I'm not good at computers so please make me sure:

1. Is my method safe?
2. Is Gmail collecting any personal data from my computer?
3. If so, does it have an access to all my system or only Wine environment in my case?
4. Is Firefox portable or any site opened in it able to get any data from my system, like passwords/cookies from other browsers (on Ubuntu, not Wine), passwords of IM software or any other data?
5. Is there any better method than described above? 

Please explain me if it's safe and why so.
Thanks!
An

---

### Post by Paqman on 2012-03-11
I'm not quite sure what exactly you're trying to protect yourself from. Are you saying you have one email inbox that you share with several other students? Or that you all use accounts hosted on Gmail, but with your own logins?

> **annnowik said:**
> 
1. Is my method safe?


No safer than using your normal browser, really.

> 
2. Is Gmail collecting any personal data from my computer?
3. If so, does it have an access to all my system or only Wine environment in my case?
4. Is Firefox portable or any site opened in it able to get any data from my system, like passwords/cookies from other browsers (on Ubuntu, not Wine), passwords of IM software or any other data?


The only data Gmail has access to is the contents of the emails you send and receive through it, as well as a few small tidbits of useless info such as what browser and OS you use (and those latter ones can be easily spoofed). All websites you visit have access to your browser and OS details anyway, not just Gmail.
In general websites cannot access personal data or passwords on your machine, to do so would be a huge security breach.

> 
5. Is there any better method than described above? 


Depends what you mean by "better". As I said above, if you're worried about Gmail somehow accessing information besides that in your emails, then what you're doing is unnecessary.

---

### Post by annnowik on 2012-03-11
Thank you for your reply and sorry for my unclear explanation.

It's not my private Gmail account.

It's an Gmail account created by the leader of our group. We use it for sharing notes, schedules, asking each other about things connected with school etc.
And every member of group got an access needed to log in.


So let me ask in another way.

1. Suppose that you give me your login and password to your Gmail. I log in to it once. Can you get some info about me (except info about the fact I did log in with hour and my ip - it's nothing private about me). I mean my cookies, history of browser, passwords or something from my system?

2. I have my private Gmail account. I log in to my private one and then to the group account. Is this still safe? Is there no connection and sharing data between both loggings (Gmail sessions)?

I'm aware that it may look funny, but I'm really confused. I usually avoid using public computers and logging in to public accounts, but in this case I have no choice.

---

### Post by Dangertux on 2012-03-11
> **annnowik said:**
> Thank you for your reply and sorry for my unclear explanation.

It's not my private Gmail account.

It's an Gmail account created by the leader of our group. We use it for sharing notes, schedules, asking each other about things connected with school etc.
And every member of group got an access needed to log in.


So let me ask in another way.

1. Suppose that you give me your login and password to your Gmail. I log in to it once. Can you get some info about me (except info about the fact I did log in with hour and my ip - it's nothing private about me). I mean my cookies, history of browser, passwords or something from my system?

2. I have my private Gmail account. I log in to my private one and then to the group account. Is this still safe? Is there no connection and sharing data between both loggings (Gmail sessions)?

I'm aware that it may look funny, but I'm really confused. I usually avoid using public computers and logging in to public accounts, but in this case I have no choice.


The answer to #1 depends on if any of the mail you have in your shared gmail box contains personal information about you. If not, then realistically nothing too personal.

In any case, this wouldn't be changed by using a Windows version of Firefox in Wine anyway. 

Hope this helps.

---

### Post by Paqman on 2012-03-11
> **annnowik said:**
> 
1. Suppose that you give me your login and password to your Gmail. I log in to it once. Can you get some info about me (except info about the fact I did log in with hour and my ip - it's nothing private about me). I mean my cookies, history of browser, passwords or something from my system?


No.

> 
2. I have my private Gmail account. I log in to my private one and then to the group account. Is this still safe? Is there no connection and sharing data between both loggings (Gmail sessions)?


There is no connection between the two.

---

### Post by annnowik on 2012-03-11
Thanks again. I'm very glad to hear it.

Anyway, I've just reached a conclusion that it's even less save to use FF in Wine because it can execute viruses in opposition to browser working directly on Ubuntu.

Am I right?

It's a pity that Wine lets apps to get an access to external partition and generally all the Linux.

---

### Post by jonnyboysmithy on 2012-03-11
> **annnowik said:**
> Thanks again. I'm very glad to hear it.

Anyway, I've just reached a conclusion that it's even less save to use FF in Wine because it can execute viruses in opposition to browser working directly on Ubuntu.

Am I right?

Yes that is correct.

---

### Post by Paqman on 2012-03-11
Well, running a Windows browser and a Windows-like environment will put you at risk from exploits written for those, but the malware wouldn't be able to work the same as it would in a real Windows system. At worst it would just make a mess of the .wine folder in your home. It'd be unlikely to be able to spread itself of gain any access to the functional parts of a Linux system.

---

### Post by 3Miro on 2012-03-11
Think Unix and Multi-user.

Make a second user on your Linux machine and login as that user only when you need to run Firefox to check Gmail.

- Switch users, check Gmail, switch back to the main user

Alternatively, you can set the system so you can run firefox directly as the other user:
```
gksudo -u other_username firefox
```

If you feel sufficiently paranoid, you can fix your umask so that the other user will not have even a read access to your data. Although this is probably an overkill.

---

### Post by annnowik on 2012-03-12
Thanks you all for replies!

In fact - another user is an great idea.

1. But there is really no connection between users? Do different user profiles work like a totally independent systems? Is /home/User1 blocked when I'm logged as User2? Ok, it's possible to be disabled. But how about other common system files?

2. And what would be the best solution for using risky sites:

- new user profile
- virtual box with Ubuntu running on main Ubuntu
- new partition with new Ubuntu (I guess it's like an another hardware machine ;) )

?

---

### Post by Paqman on 2012-03-12
> **annnowik said:**
> Thanks you all for replies!

In fact - another user is an great idea.

1. But there is really no connection between users? Do different user profiles work like a totally independent systems? Is /home/User1 blocked when I'm logged as User2? Ok, it's possible to be disabled. But how about other common system files?


Each user has their own folder in /home. I believe by default Ubuntu allows read access to each other's home folders, but that's easily fixable if you don't like it. System files are shared, but they're also protected from modification by multiple layers of security, and using a second account does not reduce this in any way.

> 
2. And what would be the best solution for using risky sites:


Don't visit them. However Gmail is not what I would describe as "risky".

> 
- new user profile
- virtual box with Ubuntu running on main Ubuntu
- new partition with new Ubuntu (I guess it's like an another hardware machine ;) )


You have a guest account available to you. It's another account with very restricted privileges, and it's wiped clean every time you boot. The guest account does not have access to any other accounts, and cannot use sudo to access system settings.If you're forced to use a site that makes you nervous, switch to the guest account to use it then reboot after you're done. Just make sure you don't save anything you want to keep int the guest account's home folder, or it'll disappear when you reboot!

---

### Post by 3Miro on 2012-03-13
> **annnowik said:**
> Thanks you all for replies!

In fact - another user is an great idea.

1. But there is really no connection between users? Do different user profiles work like a totally independent systems? Is /home/User1 blocked when I'm logged as User2? Ok, it's possible to be disabled. But how about other common system files?

You should read up on Unix permissions. Generally speaking, you can see and use system files, but you can only modify what belongs to you (or more specifically you user). If you serf the web as user B, then you will be able to write over what is written in user B's home folder.

Thus is any damage done to user B will be contained to user B's home folder and will not affect anything else in the system. Theoretically it is possible to gain enough control over an account and then elevate privileges, but this is extremely difficult in a Unix setup.

However, by default, user B can read from the files of user A without modifying it. You can change this behavior with umask, but do some reading first.

> 
2. And what would be the best solution for using risky sites:

- new user profile
- virtual box with Ubuntu running on main Ubuntu
- new partition with new Ubuntu (I guess it's like an another hardware machine ;) )

?

A new partition within the same installation of Ubuntu is exactly like a new folder, so it will not help. Virtual Box and Dual-boot (as well as liveCD) are very secure options, but an overkill in my opinion. If all you want to do is access Gmail in a private manner, then the dual-user option will be more than enough.

For shady sites, it is best to not go there, but unless it is something ultra shady, I think Firefox + No-script is sufficient. I have FF with no-script that I use if I want to be a bit more private, then I use Chromium for all of the sites that I deem "secure". Basically, I dual-browsers, and what I do in one browser doesn't see what I do in the other.

---

### Post by winh8r on 2012-03-13
> **Paqman said:**
> Well, running a Windows browser and a Windows-like environment will put you at risk from exploits written for those, but the malware wouldn't be able to work the same as it would in a real Windows system. At worst it would just make a mess of the .wine folder in your home. It'd be unlikely to be able to spread itself of gain any access to the functional parts of a Linux system.

Dangertux wrote a very interesting article  on his security blog :

[http://tinyurl.com/6oe2d8f]("http://tinyurl.com/6oe2d8f")

---

### Post by annnowik on 2012-03-13
I'm gonna look at this, thanks...

Generally, I don't agree with the assumption that viruses in Wine are dangerous only to Wine environment and don't hurt the rest of Linux.

If some virus is made for changing something in system, it will only make a mess around .Wine folder (like virtual C:/Windows etc).

But if some virus is looking for a passwords or any other private data and then send it somewhere, it will also search in all Ubuntu system because of "Z:" disc in Wine (and generally ability to get an access over the Wine folder).
Same if a virus works as keylogger...

I hope you know what I mean. And I remark again, that I wrote this before reading the mentioned above link. Maybe I will change my mind after reading it.


And why I actually used to use Wine?

Because I wanted to use new, clean Firefox copy to login to a Gmail and I didn't know how to install Firefox again on Ubuntu. So the only solution that I could handle was multiple installation of FF Portable in Wine.

Anyway, is it possible to install something in Ubuntu twice or generally more than one time?

---

### Post by Paqman on 2012-03-13
> **annnowik said:**
> 
Because I wanted to use new, clean Firefox copy to login to a Gmail and I didn't know how to install Firefox again on Ubuntu. So the only solution that I could handle was multiple installation of FF Portable in Wine.

Anyway, is it possible to install something in Ubuntu twice or generally more than one time?

As mentioned above, you can use multiple Firefox profiles within one user account, or you can create multiple user accounts (including the disposable guest account) each with their own Firefox profile. So effectively, yes you can have multiple separate Firefox instances. Sure, they'll be sharing some system resources, but that's not a security problem as any exploit that could gain access to those resources once could do it any number of times.

---

### Post by winh8r on 2012-03-13
retracted

---

### Post by lovinglinux on 2012-03-13
> **Paqman said:**
> As mentioned above, you can use multiple Firefox profiles within one user account, or you can create multiple user accounts (including the disposable guest account) each with their own Firefox profile. So effectively, yes you can have multiple separate Firefox instances. Sure, they'll be sharing some system resources, but that's not a security problem as any exploit that could gain access to those resources once could do it any number of times.

Furthermore, you can use Firefox Private Browsing mode to avoid saving any data during the session. 

If you are not satisfied with using multiple profiles, you can download Firefox directly from Mozilla, extract it to your home directory and run it. Keep in mind it will use your profile by default, so you need to create a separate profile anyway.

I see no reason whatsoever to use Firefox for Windows under Wine.

---

