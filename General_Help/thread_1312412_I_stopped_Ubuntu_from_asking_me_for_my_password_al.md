---
title: "I stopped Ubuntu from asking me for my password all the time... so what?"
date: 2009-11-03
forum: General Help
---

### Post by JugglinPhil on 2009-11-03
Recently a friend of mine was around and I was showing him Karmic, we installed a few apps and you know how it goes: You end up entering your password just about every minute. We both thought this was quite annoying and he even compared it to the Windows User Account Control...

After some thought I decided that I had to do something, because this is anything but freedom to me. 
After about 5 minutes of research I found out how and changed it using visudo, and now I finally can rest in peace. ^^ 

I have found a lot of opposition against doing this, but I couldn't really see their arguments applying to me: I am the only one using the computer, it is in a home environment and has nothing important on it that's not backed up on some external hdd. 

I know I have to be more careful now about using sudo commands and everything, but to me that is surely worth it. Additionally, if someone has physical access to my PC and knows what s/he's doing, I'd be in trouble anyway right?

Any opinions on this?

UPDATE: Thanks to P4man I was able to solve my problem without endangering my systems security too much (by editing sudoers) and my visudo is back to default.

---

### Post by Peter09 on 2009-11-03
Well the risk is that while browsing the internet, someone manages to run a remote script - after that its all over for your security.

How easy that is - well its difficult to say. So what peace of mind do you get while browsing the internet?

---

### Post by dbyjazz on 2009-11-03
Well Ubuntu has a lot of security enabled for a purpose ;-)

but I'd say you're safe because of what you said with nothing of real importance being on your drive and I highly doubt if a robber went and robbed your house he wouldn't be a linux geek ;)

but there is that internet security issue

---

### Post by scouser73 on 2009-11-03
I know you've said that there is only you who will be using the PC, but that's not something I'd do nor is it something that should be advertised for people not wanting to enter a password when using the Terminal and so on.

The way Ubuntu & Linux in general is set up is for security reasons and surely you must realise this when you've come to adopt Linux as an operating system.

Let me point you to an article on security posted in the forums: [[COLOR="Red"]**Ubuntu Security**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=510812"), the author if the article goes into great details about the implications on security and looks at it from two differing mindsets, one being the Windows mindset and the other being the Ubuntu mindset.

Please give that article some consideration, after all it could save you a massive headache and then some.

---

### Post by P4man on 2009-11-03
Limit your potential security risk by removing the password prompt for only those apps where it bothers you (apt-get, software-center, etc). I wouldnt remove it entirely as you seem to have done.

---

### Post by JugglinPhil on 2009-11-03
Okay that's a good point bout some hacker, but the only stuff I've got on here is music which is backed up, even my photos are on an external drive. 
Anyway, how would someone do this, run a remote script on my PC? I'm not intending to become a black hat, I'm just interested in that sort of stuff.

---

### Post by JugglinPhil on 2009-11-03
> **P4man said:**
> Limit your potential security risk by removing the password prompt for only those apps where it bothers you (apt-get, software-center, etc). I wouldnt remove it entirely as you seem to have done.
That would of course be way better, I take it that would make it save again right? Anybody willing to give advise/assistance on how to do this?

---

### Post by spoon_ on 2009-11-03
If you _do_ have the password prompts, is it any harder for a malicious website to run a remote script than if you don't? Just curious.

---

### Post by Muflon on 2009-11-03
You can think of it like seatbelts in cars.  They are annoying to put on and can be uncomfortable/restrictive to wear.  Most of the time you won’t need it and you could drive for years without having an accident but if you ever do, then you will be glad that you bothered to wear it.

Muflon

---

### Post by Peter09 on 2009-11-03
Every time you browse the Internet scripts are run - that little animated icon is a script for instance.

So if you don't do Internet banking, or have an Internet mail account, or log on to forums like these or any other activity that requires passwords etc then I guess your safe....... I think.

---

### Post by P4man on 2009-11-03
> **JugglinPhil said:**
> That would of course be way better, I take it that would make it save again right? Anybody willing to give advise/assistance on how to do this?```

man sudoers
```
Do use visudo to edit it, and use at your own risk. Im not recommending this but its certainly better than what you have now.

---

### Post by mcduck on 2009-11-03
> **JugglinPhil said:**
> Okay that's a good point bout some hacker, but the only stuff I've got on here is music which is backed up, even my photos are on an external drive. 
Anyway, how would someone do this, run a remote script on my PC? I'm not intending to become a black hat, I'm just interested in that sort of stuff.

Cracker's are not usually after your files, but after your computer's resources. Randomly searching through people's machines for something worth  some money is unlikely to work, but on the other hand any computer connected to Internet would be a nice extension to some botnet used for illegal purposes and sending spam mail etc.

As long as your computer is connected to the net, you should never count on being the only person using  (or trying to use) the machine. So you really should keep the passwords working like they are meant to. It's not limiting your freedom (you are still free to do whatever you want with the system), it's *protecting* your freedom.

If you feel that you need to type the password too often there are far better ways to work around that. Use "gksudo nautilus" and "sudo -i" to open root sessions in terminal/file manager and you won't have to type your password again and again, but you still don't have to break the entire securty conceptof te operating system. :)

---

### Post by HiImTye on 2009-11-03
> **spoon_ said:**
> If you _do_ have the password prompts, is it any harder for a malicious website to run a remote script than if you don't? Just curious.
while it doesn't make it harder to run a malicious script it limits the powers that script can have (limiting the exposure your computer has to malicious scripts/code). the worst thing that can happen is you will need to make a new user (and possibly any 'owned' folders) rather than having to redo ubuntu

---

### Post by Peter09 on 2009-11-03
Spoon_

There are a lot of things that stop malicious scripts from executing anything that can damage the installation, however if it **can** gain root access (say because of no password) then most can be blown away quite quickly.

---

### Post by spoon_ on 2009-11-03
But everything valuable to me on my computer is accessible by my own user, without any password. I'm not sure what the malicious script gains by having control of root. I suppose it can mess up the system in more exotic and subtle ways, but even a non-root script can wipe out everything of value ...

---

### Post by JugglinPhil on 2009-11-03
> **P4man said:**
> ```

man sudoers
```Do use visudo to edit it, and use at your own risk. Im not recommending this but its certainly better than what you have now.
Sorry but this is too crazy for me, too much text in there I don't have a clue what it means/what to do.. ^^

---

### Post by JugglinPhil on 2009-11-03
> **spoon_ said:**
> But everything valuable to me on my computer is accessible by my own user, without any password. I'm not sure what the malicious script gains by having control of root. I suppose it can mess up the system in more exotic and subtle ways, but even a non-root script can wipe out everything of value ...
Yeah but they're not speaking bout wiping your data but messing up your whole OS (In which case I'd just reinstall in like 15 minutes, so I don't really get all the worries..)

---

### Post by Peter09 on 2009-11-03
> But everything valuable to me on my computer is accessible by my own user, without any password. I'm not sure what the malicious script gains by having control of root. I suppose it can mess up the system in more exotic and subtle ways, but even a non-root script can wipe out everything of value ...

As an example - with root access a malicious script **could** install a key-logger, every key that you press **could**  then be sent back to the hacker...... and you wouldn't know.

---

### Post by spoon_ on 2009-11-03
> **Peter09 said:**
> As an example - with root access a malicious script **could** install a key-logger, every key that you press **could**  then be sent back to the hacker...... and you wouldn't know.

Good example! I don't really have a clear idea in my head of which privileges require root and which don't. So it's impossible to write a keylogger that doesn't require root access?

---

### Post by P4man on 2009-11-03
> **Peter09 said:**
> As an example - with root access a malicious script **could** install a key-logger, every key that you press **could**  then be sent back to the hacker...... and you wouldn't know.

it seems keyloggers can run *without* root permission, so im not sure your example has merit. Still I dont really see the point of circumventing the sudo system, it only prompts you once per 15 minutes (by default).better safe than sorry

---

### Post by Peter09 on 2009-11-03
Well I've never tried to write a key logger either but at a guess to do so without root access would be difficult - as a start you need to stop the program that collects your key strokes at the moment - that would most probably require root access.

---

### Post by spoon_ on 2009-11-03
I'll also point out that without root access, you can copy the ~/.mozilla directory which probably contains all of your web passwords in an unencrypted form. Unless you have Firefox bug you for the master password at every launch.

---

### Post by P4man on 2009-11-03
> **Peter09 said:**
> Well I've never tried to write a key logger either but at a guess to do so without root access would be difficult - as a start you need to stop the program that collects your key strokes at the moment - that would most probably require root access.

I participated in a lengthy discussion about seahorse displaying passwords in clear text without user authentication. Thats where I learned you dont need root privilege to access passwords stored in the keyring (being logged in is enough) and it was also pointed out keyloggers dont need root permission. This was confirmed by a googling on a linux keylogger which indeed did not seem to require sudo to operate.

IOW your personal security/identity is not protected once you are logged in, sudo or no sudo. You *system* security however is protected.

---

### Post by norm7446 on 2009-11-03
Linux as a whole is only more secure than Windows because it requires a Root password for Administrative tasks from first install. The same happens in Windows but it does not ask you for your password every time you want to do something Administrative to the system, as it puts the first user on the system as an Administer and assumes that the user knows everything about the system wither it is malicious or not. Even if it is your Granny who only starts the Computer up to play Spider.

So if, unless your Root password is 40 characters long and very secure plus takes an absolute age to type in, it is only a small minor irritation, that will make you secure and not another E-Mail Zombie..

---

### Post by Peter09 on 2009-11-03
> So if, unless your Root password is 40 characters long and very secure plus takes an absolute age to type in, it is only a small minor irritation, that will make you secure and not another E-Mail Zombie..

mmmmm .. everything is crackable - however the criteria is whether its worth the time and effort to crack it.

---

### Post by mcduck on 2009-11-03
> **P4man said:**
> I participated in a lengthy discussion about seahorse displaying passwords in clear text without user authentication. Thats where I learned you dont need root privilege to access passwords stored in the keyring (being logged in is enough) and it was also pointed out keyloggers dont need root permission. This was confirmed by a googling on a linux keylogger which indeed did not seem to require sudo to operate.

IOW your personal security/identity is not protected once you are logged in, sudo or no sudo. You *system* security however is protected.

True, a keylogger (as well as other nasty stuff) can be installed on one user account only, and that won't need root permissions. The limitation is that hiding things well is harder without rot access, and what can be don is limited to that user's session only, so no other users, login passwords etc are available that way.

The main point is that using the root password, even if you are the only person supposed to use that machine, protects not only your own user account (to some level) and all the other possible user accounts on that machine, but like I already said in my previous post, it protects the *system itself*. Your files might be worthless to other people, your network connection, storage space and computing power on the other hand definitely are worth something.. (running and hiding a spam server for example is quite hard to do without root access in a way that the user doesn't notice anything (apart from things becoming slow), but with root access such things can be hidden so well that you'll have no change of finding out what's really happening.

These days only a machine without a network connection can be really considered as single-user machine. Every computer connected to any type of network should be treated as multi-user system.

edit: in other words, disabling the password authentication makes you considerably more vulnerable to rootkits and all the nasty stuff that can be done with a rootkitted machine.

---

### Post by P4man on 2009-11-03
> **mcduck said:**
> True, a keylogger (as well as other nasty stuff) can be installed on one user account only, and that won't need root permissions. The limitation is that hiding things well is harder without rot access, and what can be don is limited to that user's session only, so no other users, login passwords etc are available that way.

The OP is a a single user on his system iirc. Everything that matteres to him would be accessible from his user account.

And while files may or may not be worthless, having your identify stolen (email account passwords for instance) is probably as  bad as it gets. So if there is a way to exploit a vulnerability in firefox or whatever to run malicious code as *user*, having sudo to protect the system might be almost pointless (with 1 user account).

Frankly Id rather have my system rendered unbootable or my hdd erased by malware than having someone steal my identity. Which makes it somewhat odd that I have to enter my password 50x per day for various mundane tasks to protect my system, but what I care about most is not protected at all if I use the keyring or other apps to remember my pw.

---

### Post by mcduck on 2009-11-03
> **P4man said:**
> The OP is a a single user on his system iirc. Everything that matteres to him would be accessible from his user account.

And while files may or may not be worthless, having your identify stolen (email account passwords for instance) is probably as  bad as it gets. So if there is a way to exploit a vulnerability in firefox or whatever to run malicious code as *user*, having sudo to protect the system might be almost pointless (with 1 user account).

Frankly Id rather have my system rendered unbootable or my hdd erased by malware than having someone steal my identity. Which makes it somewhat odd that I have to enter my password 50x per day for various mundane tasks to protect my system, but what I care about most is not protected at all if I use the keyring or other apps to remember my pw.

My point was that the users files and information are not the *only thing* that needs to be protected. The system itself and it's resources are just useful things to get access to. Somebody erasing your hard drive isn't really a likely thing to happen, somebody rootkitting your machine and using it to distribute illegal material or send spam e-mails however is.

So even for a machine with a single local user maintaining the security between users and the system itself is stll important.

---

### Post by Soul-Sing on 2009-11-03
> After some thought I decided that I had to do something, because this is anything but freedom to me.
After about 5 minutes of research I found out how and changed it using visudo, and now I finally can rest in peace. ^^ 

Linux has nothing to do with [COLOR="Red"]this[/COLOR] "freedom". 
Linux is about:
- sudo permissions = restrictions
- trusted softwaresources
- opensource ideals ( real "freedom")
Remove on of these columns your are left with a non-linux system, and ends the support to this crippled systems imho.

( why discuss this in the general help subforum? )

---

### Post by JugglinPhil on 2009-11-03
@P4man, go check your mails, Pm didnt work..

---

### Post by JugglinPhil on 2009-11-03
> **leoquant said:**
> why discuss this in the general help subforum? 
My bad..

---

### Post by change_mode on 2009-11-03
Just keep in mind that if someone takes control of your computer and uses it for illegal actions, YOU are the one responsible for it.
Access to your computer could also be used to infect your friends' computers via phishing attacks, so it should be in your best interest to keep it safe.

> **JugglinPhil said:**
> I'm not intending to become a black hat, I'm just interested in that sort of stuff.

Don't worry, that's not going to happen, lol.

---

### Post by JugglinPhil on 2009-11-03
Okay everybody, thanks to P4man I was able to edit the sudoers so that I can use synaptic, apt-get and the software center without a password prompt, so I changed the visudo back to default. Hope you're happy now. ;)

---

### Post by P4man on 2009-11-03
> **JugglinPhil said:**
> Okay everybody, thanks to P4man I was able to edit the sudoers so that I can use synaptic, apt-get and the software center without a password prompt, so I changed the visudo back to default. Hope you're happy now. ;)

Its your computer and your data. If you're happy then so are  we, just keep in mind software in the repo's could be abused by a script. For instance now a script can install an ftp or ssh server without your permission. Im not saying this is a likely thing to happen and it would require another security leak which would anyhow expose your personal stuff, but your computer is now not safer than it was yesterday. But I guess its safer than it was a few hour ago...

---

### Post by JugglinPhil on 2009-11-03
> **P4man said:**
> Its your computer and your data. If you're happy then so are  we, just keep in mind software in the repo's could be abused by a script. For instance now a script can install an ftp or ssh server without your permission. Im not saying this is a likely thing to happen and it would require another security leak which would anyhow expose your personal stuff, but your computer is now not safer than it was yesterday. But I guess its safer than it was a few hour ago...
I'll take the risk, to me that's worth it. :)

---

